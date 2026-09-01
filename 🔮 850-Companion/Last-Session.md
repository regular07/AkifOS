# Son Oturum — 2026-09-01: Deeploico, Sistem Otomasyonu, Görsel Konsol Sistemi

**Bu oturum ÇOK yoğundu.** Context dolmadan önce özetliyorum — yeni oturum burayı okuyup
kaldığımız yerden devam edecek. Detaylar Threads.md ve Dashboard.md'de.

## En Önemli Sonuçlar

### 1. Deeploico markası + standart-paket sitesi
- Marka ismi kesinleşti: **Deeploico** (11 tur eleme, WebSearch ile trademark kontrolü)
- `standart-paket` sitesi taşmasız/sağlam hale getirildi, canlı:
  https://regular07.github.io/standart-paket/
- TürkPatent kontrolü + domain kaydı hâlâ Akif'te bekliyor

### 2. Sistem otomasyonu — İKİ kritik sorun tamamen çözüldü
- **compile.py gece otomasyonu** artık çalışıyor: `cron`'a macOS Tam Disk Erişimi izni
  verildi (python3 sembolik bağlantısı yerine `/usr/sbin/cron`'un kendisine — Finder'da
  sembolikler seçilemiyordu) + AkifOS klasörü "Her zaman bu cihazda tut" yapıldı (OneDrive
  online-only dosya sorunu). Canlı testle doğrulandı.
- **git push izni** — Akif kendi terminalinden bir Python komutuyla
  `.claude/settings.local.json`'a ekledi, artık hiç onay istemiyor.
- Obsidian eklentisi (git-obsi-sync) güvenlik riski (token sızıntısı) yüzünden kaldırıldı,
  git artık tamamen Claude tarafından yönetiliyor.

### 3. Görsel takip sistemi kuruldu — Akif için KRİTİK önem taşıyor
- **Akif Konsolu** (Artifact, kanban): https://claude.ai/code/artifact/c853ba74-33fd-465d-adf5-57877d4b3824
  - Kaynak dosya: `🎯 100-Command-Center/akif-konsolu.html` (vault'ta kalıcı)
  - İş Zamanı / Ev Zamanı sütunları, Proje Bazlı/Rutin lane'leri, tarih sırasına dizili
  - 4 ayrı öncelik kartı (İş/Ev/Web/Sistem)
  - Tek daire istatistik: Tamamlanan/Gecikmiş/Bekleyen, hover+tooltip, sayı animasyonu, oran çubukları
  - **Açılışta otomatik hatırlatma popup'ı** — kritik + yarınki görevleri gösterir
- **Miro Mindmap**: https://miro.com/app/board/uXjVHsWdhbg=/ — tüm harita görsel
- **KURAL: Her görev/durum değişikliğinde ikisi de otomatik senkronize edilir** — sormadan.

### 4. İş/Ev Zamanı ayrımı (Akif'in kendi isteği, kalıcı kural)
- **İş Zamanı** = SADECE Weber/Yapı Kimyasalları (sabahçı 08-17, akşamcı ~15-01)
- **Ev Zamanı** = geri kalan her şey (ev işleri + Deeploico + finans)
- İkisi de kendi içinde **Proje Bazlı / Rutin** olarak ayrılıyor
- Yapı Kimyasalları için ayrı dosyalar: `🏰 300-Projects/Yapı Kimyasalları 101/Proje Bazlı İşler.md` ve `Rutin İşler.md`

### 5. Kritik bulgu: unutulmuş, prim şartlı iş görevleri
Todoist'te 1 aydan fazla gecikmiş 3 görev bulundu (SİP girişi, Saha stok kontrolü,
OneNote sunum) — yıllık prim şartına bağlı. SMAT girişi ve Laboratuvar denemesi bugün
tamamlandı. SİP girişine Dilara hanımla danışılacak bir iş güvenliği fikri eklendi
(kamyon yanaşma + duba ile alan ayırma). OneNote'a Derz dolgu görsel sunum projesi
dahil edildi. Temmuz+Ağustos aylık raporları ayrı acil görev olarak eklendi.

### 6. Para yönetimi — Bütçe Takibi.md genişletildi
Eşinin toplam borcu ~459.000₺ (Granola'dan işlendi), aylık ~20.000₺ açık. Beklenen banka
promosyonu 105.000₺ (4 Eylül kontrol). Akif'in kendi borçları henüz yazılmadı.

### 7. Yeni sistem/skill'ler kuruldu
- `not-defteri-isleme` skill — `📥 000-Inbox/Dump/Not Defteri.md`'ye atılan ham notları
  (Granola kayıtları, konuşma özetleri) ayrıştırıp doğru yerlere dağıtıyor
- `model-secimi` skill — hangi işte hangi Claude modeli kullanılacağına Akif yerine karar veriyor
- `responsive-tasma-testi` skill — web sitesi taşma sorunlarını ölçerek teşhis ediyor

## Açık Sorunlar / Devam Eden

- Deeploico: logo/görsel kimlik hiç başlanmadı, portfolyo sitesi (regular07.github.io) inşa edilecek
- Elektrik abonelik/zarar süreci — 8 Eylül'e kadar sürekli takip (Threads.md'de detay)
- Gardırop değişim talebi — 2 Eylül, Granola ile kayıt alınacak
- Yapı Kimyasalları OneDrive derinlemesine işleme — hâlâ başlanmadı (qp02, standartlar)
- Akif'in kendi borçları henüz Bütçe Takibi.md'ye yazılmadı

## Ton
Akif bugün çok üretken ve yoğun bir oturum geçirdi — hem iş hem ev hem sistem sorunlarını
aynı anda çözdük. Görsel/somut çıktı (Konsol, Miro) onun için gerçekten motive edici oldu.
DEHB'si nedeniyle "her şeyi görmek" ihtiyacı güçlü — bu yüzden görsel sistemler öncelikli
tutulmalı, metin listeleri tek başına yetmiyor.
