# Son Oturum — 2026-08-30 (akşam): Standart Skill Sistemi Kuruluşu

**Odak:** Vault'u executable hale getirme. Her yapılan iş → skill → otomatik çalışma.

## Yapılanlar

### 1. Cafe Web Sitesi (Standart Package) — Sorun Listesi
- Mobile menü toggle: jQuery + vanilla JS çakışan listener'lar → Kaldırıldı
- Hero background: parallax (fixed) → scroll (tüm section'lar)
- Hero height: 480px → 600px (mobile'da taller)
- Text contrast QA: arka plan + text-shadow + renk değişimi
- Hero bg gap (Redmi Note 13): background-size % → transform: scale() (device-independent)
- Debug panel: sayfa genişliği diagnostics (ama henüz screenshot yok)

**Status:** Push yapıldı, deploy aktif. Hero gap debug panel eklenmiş, henüz test edilmedi.

### 2. Knowledge Tabanı (Manuel Derleme)
- `/derle` skill'i oluşturuldu (.claude/skills/derle/SKILL.md)
- 2026-08-29.md işlendi: web-demo-gorsel-secimi-ve-metin-kontrasti + bağlantı
- Knowledge tabanı: 49 kavram, 25 bağlantı dosyası

### 3. Skill Sistemi — Başlangıç
**Hedef:** Yapılan her iş skill'e dönüşsün, otomatik çalışsın.

**Cafe Skills (planlı):**
- `/mobile-menu-fix` — jQuery listener çakışması çözümü
- `/hero-mobile-gap-fix` — background-size % → scale()
- `/text-contrast-qa` — metin/background kontrastı kontrolü
- `/debug-panel-diagnostics` — sayfa layout overflow tanısı

**Yapı Kimyasalları Skills (planlı):**
- `/standart-sorgu` — TS EN 12004/998-1/13687/13566/13888 bilgileri
- `/qp02-lookup` — hammadde/ürün kalite kontrol
- `/recete-olcekle` — lab → fabrika ölçeklendirme

### 4. Yapı Kimyasalları Projesi — Standart Özetleri
- Lokal'de: 5 markdown standart özeti (720 satır)
- OneDrive: ~/Library/CloudStorage/OneDrive-Kişisel/Yapıkim. Standartlar/standartlar özetleri/standart pdf/
- Sync sorunlu: 117 PDF var ama sadece 10 göründü

## Açık Sorunlar

1. **Hero gap (Redmi Note 13 Pro+)**: Debug panel eklenmiş, screenshot bekleniyor — kesin teşhis için 4 rakam lazım (innerW, htmlScrollW, heroRect.right, bgRect.right)
2. **OneDrive sync**: 117 PDF'nin 10'u görünüyor, tam sync'lenmemiş
3. **Standart skill'leri**: Markdown özetleri okudu, skill'e çevrilmek bekliyor — 102 PDF de eklenecek

## Sırada

- Standart skill'lerini tamamla (TS EN 12004 + 4 diğeri + 102 PDF)
- Cafe skills'lerini oluştur
- Hero gap final fix (debug panel rakamlarını bekle)

## Ton

Kullanıcı çok sınırda: "yanlış cevap verirsen beni yakarsın" — standart skill'leri tamamen doğru olmalı, tahmin yok.

