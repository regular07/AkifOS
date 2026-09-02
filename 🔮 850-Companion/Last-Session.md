# Son Oturum — 2026-09-02: Yazılım Döngüsü Planı, İş Devri, Web Tasarım Araştırması

Bir önceki oturum (2026-09-01 mega özet) `Journal.md` benzeri detayıyla Threads.md'de.
Bu oturum yerel Mac'te (Claude Code CLI) yapıldı — bulut oturumundan (session_01NNUkj...)
devralındı.

## Bağlam: iki oturum karışıklığı çözüldü
Akif önce claude.ai/code **bulut** oturumunda çalışıyordu (uzak konteyner, sadece git
klonu, OneDrive/tarayıcı/cron göremiyor). Bu oturum **yerel** Claude Code — araçlar
gerçek Mac diskinde çalışıyor. Bulut oturumundaki git push 403 sorunu Akif GitHub App
bağlantısını düzeltince çözüldü.

## Yapılanlar

### 1. model-secimi skill güncellemesi main'e alındı
Bulut oturumunun `claude/ne-durumdayiz-kllg05` branch'indeki `ae2e100` commit'i
(`fable-orchestration`'dan 2 kural: sessiz model mirası engeli + "devretme bedava değil")
`main`'e merge + push edildi. Artık canlı kural.

### 2. Yazılım Döngüsü mimari planı — Fable yaptı
`🏰 300-Projects/Yazılım Döngüsü/Plan.md`. Akif'in isteği: "yapay zekadan oluşan yazılım
döngüsü" ile bir internet sitesi kurup yönetmek. Roller: **patron = Akif** (2 onay kapısı),
**mimar = Fable** (ana konuşma döngüsü, asla subagent değil), **kod = Sonnet** (şablon) /
**Opus** (zor), **test lane** (Sonnet) + **bağımsız test-gate lane** (`/code-review` + Opus,
en yüksek efor), **görsel** (Faz 0: Artifact/design + placeholder).
- **Faz 0** (şimdi, Codex/Higgsfield yok): `yazilim-dongusu` skill'i + Döngü-Log +
  Deeploico iskeleti. Pilot: **Deeploico portfolyo sitesi**.
- **Faz 1**: Higgsfield alınınca görsel lane.
- **Faz 2**: Codex alınınca `codex-fleet` + `gptpro-handoff`.
- **Faz 0 HENÜZ BAŞLAMADI** — Akif bunaldığı için bilinçli park. Plan dosyada bekliyor.
- Referans: avenoxskills klonu `/tmp/avenoxskills` (Codex CLI + OpenAI aboneliği YOK,
  Higgsfield YOK — ikisi de "para gelince/yakında" slotları).

### 3. İş durumu güncellendi (Akif bunalmış)
Akif: "kafam çok dağınık, normal işlerimi yapamıyorum, çok iş var, görünce yoruluyorum".
- **2 Eylül işlerinin hiçbiri yapılmadı** → 3 Eylül'e devredildi (gardırop değişim talebi
  + Granola kaydı, kettle, Pattex 502, talaş tozu + ahşap tutkalı).
- **105.000₺ banka promosyonu yattı** → `🔐 400-Vault/Bütçe Takibi.md` Gelir/Alınan'a işlendi.
- **Aktif odak: Yapı Kimyasalları numune takibi** (rutin). Aylık rapor (Temmuz+Ağustos
  birikmiş) geç kalındı ama numune takibinden sonraya park.
- **Veri aktarma / geçmiş-import işine ara verildi** — Akif'i yoruyor. Mobilden takip edecek.
- Dashboard'a "Çalışma modu" notu eklendi: yeni açık iş yaratma, tek konuya indir.

### 4. Web tasarım araştırması — Fable başlattı (arka planda)
`🏰 300-Projects/Deeploico/Tasarım Araştırması.md`. Akif "10.000 dolarlık internet sitesi"
kalitesinde fikirler istedi — internet araştırması + GitHub repo incelemesi + 3 somut
tasarım yönü + stack önerisi. Bu, Yazılım Döngüsü Faz 0'ın pilotu.

## Bekleyen / Sıradaki
- **Akif `/model fable` yazacak** — web sitesi tasarımına Fable ile devam (model-secimi kuralı).
- Fable tasarım araştırması bitince Akif bir yön seçecek → Faz 0'ın ilk somut hamlesi.
- Bilgisayar uyku modu: Akif `sudo pmset -c sleep 0 disksleep 0 displaysleep 0 powernap 0`
  komutunu kendi çalıştıracak (sudo, Claude yapamaz) — henüz yapılmadı.
- 2 Eylül'den devreden ev işleri + kira (4 Eylül) + elektrik takibi (8 Eylül) duruyor.

## Ton
Akif bunalmış — DEHB, çok açık iş, hepsini görünce yoruluyor. Ona listeyi daraltarak,
tek iş vererek, takip yükünü üstlenerek yardım et. Yeni açık iş yaratma. Yazılım döngüsü
ve tasarım işleri heyecan verici ama Akif kafası toparlanınca dönecek — zorlama.
