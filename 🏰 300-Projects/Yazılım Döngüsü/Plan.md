---
title: Yazılım Döngüsü — AI Filosu Mimari Planı
created: 2026-09-02
modified: 2026-09-02
type: project
status: active
tags: [yazilim-dongusu, ai-filosu, mimari]
---

# Yazılım Döngüsü — AI Filosu Mimari Planı

Mimar: Fable. Patron: Akif. Bu plan Akif'in "bir internet sitesi kur ve onu bir
yazılım döngüsü ile yönet" isteğinin tam mimarisidir.

Omurga kuralı (`fable-orchestration`): **Kıt ve pahalı üst model (Fable) sadece
mimari + yargı yapar, asla subagent olarak çoğaltılmaz. Ucuz katmanlar mekanik
işi yapar. Devretmek bedava değildir.**

---

## 1. Roller ve Eşleşme Tablosu

Akif'in istediği her rol → Claude Code'da bunu ne karşılıyor:

| Rol (Akif'in dediği) | Somut mekanizma | Model | Araç | Seri/Paralel |
|---|---|---|---|---|
| **Patron** | Akif. İki onay kapısı: (1) spec onayı, (2) canlıya çıkmadan önizleme onayı. Karar verir, kod yazmaz. | — | Konuşma | 2 kapı |
| **Mimar** | Ana konuşma döngüsü (`/model fable`). Spec yazımı, hangi lane hangi modelde kararı, entegrasyon, çakışma çözümü, nihai yargı. **Asla subagent değil.** | Fable | Ana döngü | Seri |
| **Kod yazan — kolay / şablon iş** | Agent tool subagent. Kendi kendine yeten brief + "senin dosyaların" (OWNS) + "dokunma" (DO-NOT-TOUCH) listesi. Var olan bir kalıbı kopyalayan, mevcut pipeline'a binen işler. | **Sonnet** | Agent tool / Workflow phase | Paralel (2–4 lane) |
| **Kod yazan — zor / hassas iş** | Agent tool subagent, dar ve eksiksiz spec. Yeni state machine, contract'a duyarlı tasarım, correctness-kritik yol. | **Opus** | Agent tool | Paralel |
| **Bağlam toplama** (kod tabanını anlama, araştırma taraması) | Agent tool subagent. Brief gevşek olabilir, çıktı "anlayış"tır, diff değil. | **Opus** | Agent tool | Paralel/Seri |
| **Test yapan** | Ayrı lane. Spec'in kabul kriterlerine karşı test yazar **ve çalıştırır**, pass/fail raporlar. "Kod testi geçiyor" der. | **Sonnet** (saf çalıştırma: Haiku) | Agent tool / Workflow phase | Kod lane'lerinden sonra seri |
| **Test kontrol eden** (gate-reviewer) | **AYRI birim.** Test yapan lane ile asla aynı değil. Şunu sorar: testler gerçekten spec'i kapsıyor mu yoksa sığ/oyunlanmış mı? İmplementasyon spec'e uyuyor mu, gizli bug var mı? Kabul kontrolünü **bağımsız kendisi** tekrar çalıştırır. | `/code-review` skill (ana döngü) + **Opus** reviewer subagent | `/code-review` + Agent tool | Test lane'inden sonra seri, **en yüksek efor** |
| **Görsel — Faz 0** | Artifact + `design` / `dataviz` skill + placeholder görseller | Sonnet | Artifact / skill | Kod lane'leriyle paralel |
| **Görsel — Faz 1** | Higgsfield lane, spec'ten yazılmış görsel brief | — | Higgsfield | Paralel |
| **Kod yazan — Faz 2** | `codex exec` lane, worktree izolasyonu | gpt-5.x (high/xhigh) | codex-fleet | Paralel |
| **Derin denetim — Faz 2 (ops.)** | GPT Pro handoff döngüsü, milestone başına bir kez | GPT Pro | gptpro-handoff | Milestone başına |

### "Test yapan" vs "test kontrol eden" — neden iki ayrı birim

`fable-orchestration`'ın kuralı: **"Bir lane'in 'başardım' demesi kanıt değil,
iddiadır."** Aynı zeka hem kodu/testi yazıp hem "doğru" derse, kör noktasını
kendisi denetleyemez. Bu yüzden:

- **Test yapan lane** dar bir soruyu cevaplar: "Yazdığım testler şu an geçiyor mu?"
- **Test kontrol eden (gate) lane** geniş soruyu cevaplar: "Bu testler doğru şeyi
  mi test ediyor? İmplementasyon spec'e gerçekten uyuyor mu? Testi kandırmadan
  ben kabul kontrolünü çalıştırınca ne oluyor?"
- Gate lane **read-only**'dir (Faz 2'de `--sandbox read-only`), fiziksel olarak
  kod düzeltemez. Düzeltme gerekiyorsa ana döngüye rapor eder, Mimar yeni bir
  yazma lane'i açar.
- Gate lane her zaman **en yüksek modelde/eforda** çalışır (Faz 0: Opus +
  `/code-review`; Faz 2: Codex `xhigh`), denetlediği işin büyüklüğünden bağımsız.

---

## 2. Döngünün Akışı — Fikirden Canlıya

Bir "internet sitesi özelliği" fikrinden yayına kadar pipeline:

```
[1] FİKİR (Akif)
      Akif bir özellik fikrini söyler / Inbox'a atar.
      → İnsan girdisi.
        |
        v
[2] SPEC (Mimar / Fable, ana döngü)  ── SERİ, sadece ana döngü ──
      Fable detaylı spec yazar: özellik ne, hangi dosyalar, kabul kriterleri,
      görsel ihtiyaç, lane bölümü (kaç lane, her biri hangi model,
      OWNS / DO-NOT-TOUCH listeleri, kabul kontrolü, rapor formatı).
      → Token buraya harcanır. Lane'i kendin yapmak yerine brief'i iyi yaz.
        |
        v
[3] ONAY #1 (Patron / Akif)  ── KAPI ──
      Fable spec özetini sunar. Akif onaylar ya da düzeltir.
        |
        v
[4] KOD LANE'LERİ  ── PARALEL (2–4 lane) ──         ┐
      Fable Agent tool / Workflow ile lane'leri açar. │  Görsel lane
      Her lane: açık model (sonnet kolay / opus zor), │  buna PARALEL
      eşzamanlı yazma varsa worktree izolasyonu,      │  koşar (Faz 0:
      kendi kendine yeten brief.                       │  Artifact + placeholder)
      Her lane işi bitince BİR commit atar.            ┘
        |
        v
[5] TEST LANE  ── SERİ (kod lane'leri oturduktan sonra) ──
      Tek lane spec kabul kriterlerine karşı test yazar + çalıştırır.
      model: sonnet. pass/fail raporlar.
        |
        v
[6] TEST-GATE LANE  ── SERİ, en yüksek efor ──
      /code-review (ana döngü) + Opus reviewer subagent.
      Testler spec'i gerçekten kapsıyor mu? Kod spec'e uyuyor mu?
      Kabul kontrolünü BAĞIMSIZ tekrar çalıştır. "Yeşil"e güvenme.
      → FAIL ise: rapor ana döngüye, [4]'e geri dön (yeni yazma lane'i).
        |
        v
[7] ENTEGRASYON (Mimar / Fable, ana döngü)  ── SERİ, sadece ana döngü ──
      Her lane'in commit'ini tamamlanma sırasına göre main'e cherry-pick et.
      Çakışmaları çöz. TEK tam kapıyı çalıştır (build + tüm testler).
      Lane'ler asla repo-kök kapısını veya git'i kendileri çalıştırmaz.
        |
        v
[8] GÖRSEL PASS (paralelden gelen çıktı burada birleşir)
      Faz 0: placeholder'lar yerinde, build yeşil.
      Faz 1+: Higgsfield görselleri aynı dosya adlarıyla placeholder'ları ezer.
      responsive-tasma-testi skill ile mobil kontrol.
        |
        v
[9] ONAY #2 (Patron / Akif)  ── KAPI ──
      Akif siteyi lokal / preview branch'te önizler. Onaylar.
        |
        v
[10] DEPLOY (Mimar / Fable)
      git push → regular07.github.io → GitHub Pages yayınlar.
      Canlı URL'yi doğrula (aç, gör).
        |
        v
[11] İZ BIRAK
      Döngü-Log.md güncelle (hangi özellik, hangi lane'ler, ne kırıldı, URL).
      Konsol + Miro senkron (mevcut kural).
```

**Paralel olan:** kod lane'leri (2–4), görsel pass, bağlam toplama lane'leri.
**Seri olan:** spec → onay #1 → lane'ler → test → gate → entegrasyon → onay #2 → deploy.
**İnsan (Akif) kapıları:** [3] spec onayı, [9] canlı-öncesi önizleme onayı. Bu iki kapı kaldırılmaz.

### Agent tool mu, Workflow tool mu?

- **Faz 0:** skill'in yönettiği düz **Agent tool** çağrılarıyla başla. Basit,
  Akif adım adım takip edebilir.
- **Faz 1–2:** pipeline stabilleşince bir **Workflow script**'ine taşı (phase'ler:
  parallel kod → test → gate → entegrasyon). `workflow-authoring` skill'i referans.

---

## 3. Faz Planı (impact × effort + DO-NOT)

### FAZ 0 — Şimdi kurulabilir (Codex yok, Higgsfield yok)

**Impact: Yüksek** — tüm döngüyü kanıtlar, gerçek bir varlık (Deeploico sitesi) üretir.
**Effort: Orta** — bir skill dosyası + klasör iskeleti + bir referans koşu.

**Oluşturulacak dosyalar:**

| Dosya | İçerik |
|---|---|
| `.claude/skills/yazilim-dongusu/SKILL.md` | Orkestrasyon skill'i. Bölüm 2'deki pipeline + model routing tablosu + DO-NOT listesi kodlanmış. `fable-orchestration` yasasını içerir: her lane'de açık model, Fable asla fan-out edilmez, gate lane test lane'inden ayrı. Tetik: "siteye şunu ekle", "yeni özellik", "döngüyü çalıştır". |
| `🏰 300-Projects/Yazılım Döngüsü/Plan.md` | Bu dosya. |
| `🏰 300-Projects/Yazılım Döngüsü/Döngü-Log.md` | Her koşunun kaydı: özellik, lane'ler, ne kırıldı, deploy URL, süre. |
| `🏰 300-Projects/Deeploico/` | Pilot site proje iskeleti: `Spec/` (özellik başına spec), `Özellik-Kuyruğu.md` (backlog), repo pointer (ayrı repo mu `regular07.github.io/deeploico` alt-yol mu — ilk adımda karar). |

**Pilot site önerisi: Deeploico portfolyo sitesi** (`regular07.github.io`).

Gerekçe:
- **Gerçek ihtiyaç.** Last-Session: "portfolyo sitesi inşa edilecek", hiç başlanmadı.
- **Düşük risk.** Akif'in kendi markası, bekleyen ödemeli müşteri yok, hata ucuz.
- **Deploy yolu kanıtlı.** `standart-paket` aynı yolla canlı — GitHub Pages + git push çalışıyor.
- **Görsel ağırlıklı.** Görsel lane boşluğunu görünür kılar, Higgsfield alımını (Faz 1) somut gerekçeye bağlar.
- **Tekrarlı bileşenler.** Proje kartları, galeriler → şablon Sonnet lane'leri için ideal.

**DO-NOT (Faz 0):**
- Fable'ı **asla** subagent olarak açma.
- Agent / Workflow çağrısında `model` parametresini **asla boş bırakma** — açıkça sonnet/opus/haiku.
- Aynı lane'e hem test yazdırıp hem gate yaptırma. Ayrı.
- 4 yazma lane'ini **tek paylaşımlı checkout'ta** çalıştırma — lane başına worktree veya net OWNS listesi.
- Worktree'leri **OneDrive klasörü içinde** açma (senkron çakışması, online-only dosya). `~/Documents/AkifOS` veya `/tmp` altında aç.
- Pilot olarak **ödemeli bir müşteri sitesi** seçme.
- "Hızlı gitmek için" Akif'in iki onay kapısını atlama.
- Görsel kaliteye Faz 0'da zaman harcama — placeholder yeterli, kalite Faz 1'in işi.

---

### FAZ 1 — Higgsfield alınınca

**Impact: Yüksek** (portfolyo sitesinde görsel = ürünün kendisi).
**Effort: Düşük** (slot Faz 0'da zaten tasarlandı).

- Görsel lane pipeline'ın **[8]. adımına** girer, **kod lane'leriyle paralel** koşar
  (görseller spec'te tanımlı, koddan bağımsız).
- Fable spec'in görsel bölümünden bir **görsel brief** yazar: stil, boyutlar, asset listesi.
- Higgsfield üretir: hero görselleri, proje thumbnail'leri, doku/arka plan, ikon setleri.
- Çıktı repo'nun `assets/` klasörüne düşer. **Placeholder swap:** Faz 0
  placeholder'ları birebir aynı dosya adlarıyla değişir, build hiç kırılmaz.
- Gate hâlâ geçerli: test-gate lane görsellerin yüklendiğini, kırık referans
  olmadığını, `responsive-tasma-testi` ile mobil taşma olmadığını kontrol eder.
- Yeni: `.claude/skills/yazilim-dongusu/` içine `gorsel-lane.md` referansı veya skill'e bölüm.

**DO-NOT (Faz 1):**
- Görsel üretimin kod pipeline'ını **bloklamasına izin verme** — paralel, placeholder build'i yeşil tutar.
- Spec'ten yazılmış brief olmadan **ad hoc görsel üretme**.

---

### FAZ 2 — Codex alınınca (para gelince)

**Impact: Yüksek** (throughput + Fable limit rahatlaması — Codex neredeyse aynı yetenekte, sub'da bol).
**Effort: Orta** (kurulum + ilk fleet koşusu + ayar).

Codex CLI + OpenAI aboneliği kurulur. `codex-fleet` devreye girer.

**`fable-orchestration` göç yasası: execution → Codex, context → Opus, judgment → ana döngü.**

| Lane tipi | Faz 0/1'de | Faz 2'de |
|---|---|---|
| Kod yazma (en büyük / en zor execution, migration, refactor, contract'a karşı test yazma) | Sonnet / Opus subagent | **`codex exec` lane**, worktree izolasyonu, `-m gpt-5.x`, `high`/`xhigh`, yazma lane'i `--full-auto` |
| Bağlam toplama (kod tabanı haritası, araştırma, keşif) | Opus subagent | **Opus subagent — DEĞİŞMEZ.** Codex belirsizliği iyi taşımaz. |
| Spec yazımı, entegrasyon, çakışma çözümü, yargı | Fable ana döngü | **Fable ana döngü — DEĞİŞMEZ.** |
| Test-gate / review-gate | Opus + `/code-review` | **Codex en yüksek preset (`xhigh`), `--sandbox read-only`** |
| Görsel | Higgsfield | Higgsfield **+** Codex `gpt-image-2` (ikinci seçenek) |

**Fleet disiplini (codex-fleet):**
- Spawn'ları 2–5 sn arayla **stagger** et (thundering herd → zombi lane).
- Her spawn'ı `caffeinate -i` ile sar (macOS uyku mid-flight lane'i sessizce öldürür).
- **Worktree-per-lane + lane başına bir commit + orchestrator cherry-pick** — canlı çakışma yok, lineer geçmiş.
- Log dosyası büyümeyen lane ölüdür — aynı brief'le respawn.
- Her lane'in **kabul kontrolünü entegrasyondan önce kendin çalıştır** — "başardım" iddiadır.
- Lane'ler **asla repo-kök kapısını veya git'i çalıştırmaz** — sadece orchestrator (Fable).

**gptpro-handoff döngüsü (Faz 2, opsiyonel — GPT Pro / ChatGPT aboneliği ayrı alım):**

Periyodik derin denetim için. Döngü: SCOPE → Fable prompt yazar → zip bundle'lar
(`gptpro` export skill) → Akif ChatGPT web UI'a yapıştırır → rapor gelir →
**her bulgu canlı koda karşı doğrulanır (kapı budur, Fable yapar)** → tutan
implemente edilir, tutmayan neden tutmadığıyla kaydedilir.

Kullanım: Deeploico ödemeli müşteri almadan önce güvenlik denetimi, performans
analizi, mimari review. **Kadans: milestone başına bir kez, özellik başına değil.**

**DO-NOT (Faz 2):**
- Bağlam toplama lane'lerini Codex'e taşıma — belirsizlikte Opus daha iyi.
- Spec yazımını veya entegrasyonu ana döngüden çıkarma.
- 20-lane fleet'i her yerde `xhigh` / fast tier'da koşturma — lane'leri katmanla (mekanik → medium, zor → xhigh).
- Codex lane "succeeded" dediğinde güvenme — kabul kontrolünü kendin çalıştır.
- GPT Pro bulgusunu canlı ağaca karşı doğrulamadan implemente etme.
- Codex fleet lane'lerine repo-kök kapısı / git çalıştırtma.

---

## 4. Somut İlk Adımlar (bu hafta)

1. **Akif:** `/model fable` yaz. Bu planı birlikte gözden geçir, onayla. (~5 dk)
2. **Claude (Fable):** `.claude/skills/yazilim-dongusu/SKILL.md` oluştur — pipeline
   + model routing tablosu + DO-NOT listesi kodlanmış. `beyin-doktor` ile skill'in
   görünür olduğunu doğrula.
3. **Claude (Fable):** `🏰 300-Projects/Deeploico/` iskeleti — `Spec/`,
   `Özellik-Kuyruğu.md`, repo kararı (ayrı repo mu alt-yol mu). Boş GitHub Pages
   reposu aç, "hello world" deploy et, **canlı URL doğrula.** (Deploy yolu yeşil
   olmadan lane açma — codex-fleet kuralı: "gate GREEN olmadan lane spawn etme".)
4. **Claude (Fable):** İlk özellik için spec yaz — en küçük dikey dilim:
   *"landing page hero + 3 proje kartı, placeholder görsellerle"*. Lane bölümü:
   2 Sonnet lane (hero, kartlar) + 1 Sonnet test lane + 1 gate (`/code-review` +
   Opus reviewer). Akif'e spec özetini sun → **onay #1**.
5. **Claude (Fable):** Döngüyü bir kez uçtan uca çalıştır (lane'ler → test → gate
   → entegrasyon → onay #2 → deploy). `Döngü-Log.md`'ye ne oldu / ne kırıldı yaz.
   Bu **referans koşu** — sonraki her özellik bunu tekrarlar.

---

## 5. Riskler ve Sınırlar

1. **Fable'ı subagent olarak fan-out etme** — en pahalı model. Agent/Workflow
   çağrısında `model` boş bırakılırsa sessizce miras alınır ve en pahalı model
   çoğalır. Kural: her lane'de açık `model: sonnet/opus/haiku`. Fable sadece ana döngüde.
2. **Devretmek bedava değil** (`fable-orchestration`). Her subagent kendi
   context + koordinasyon maliyetini taşır. Küçük iş + limitler sağlıklıysa Fable
   elle yapsın. 4 lane açmak ≈ 4× token; 1 kırık lane ≈ yarım saat debug. Sadece
   gerçekten paralelleştirilebilir, izole, büyük iş devret.
3. **Limit / kota.** Fable limiti dolarsa döngü durur. Faz 0'da bir özellikte
   lane sayısını 3–4 ile sınırla. Faz 2'de Codex bu yükü alır ama Codex sub'ının
   da bir tavanı var (`omp usage` benzeri) — fleet öncesi kontrol et.
4. **"Yeşil" kanıt değil.** Test lane "geçti" derse bu iddia. Gate lane bağımsız
   doğrulamazsa hatalı kod canlıya gider. Gate lane asla test lane ile aynı olmayacak,
   her zaman read-only + en yüksek efor.
5. **Eşzamanlı yazma lane çakışması.** Paylaşımlı checkout'ta lane'ler birbirinin
   kaydını ezer. Worktree-per-lane veya net OWNS / DO-NOT-TOUCH listesi zorunlu.
6. **Akif'in bilgi seviyesi.** Döngü fazla otomatikleşirse Akif ne olduğunu takip
   edemez. Her koşu `Döngü-Log.md` + Konsol/Miro senkron. İki onay kapısı Akif'in
   kontrol noktası — kaldırma.
7. **OneDrive + worktree.** Worktree OneDrive senkron klasörü içinde açılırsa
   senkron çakışması / online-only dosya sorunu. Worktree'leri OneDrive dışına aç.
8. **macOS uyku.** Uzun fleet koşusunda lid-close lane'i sessizce öldürür
   (~5KB çıktı, sıfır edit). `caffeinate -i` (Faz 2 için kritik).
9. **Codex/Higgsfield gelmeden aşırı tasarım.** Faz 0 döngüsü bu ikisi olmadan
   **tam çalışmalı.** Placeholder + Artifact yeterli. Görsel kalitesi Faz 1'in işi.
