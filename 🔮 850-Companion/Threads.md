# Threads

Ongoing storylines that span multiple sessions.

## Active Threads
### Thread: Setting up the second brain
**Status:** 🟢 Active: created 2026-08-26

### Thread: İş bilgi tabanı derinleştirme (OneDrive)
**Status:** 🟢 Active: created 2026-08-27
Harita çıkarıldı (`🏰 300-Projects/Yapı Kimyasalları 101/OneDrive Kaynak Haritası.md`). Sırada:
Akif hangi standart/dosyayı seçerse onu derinlemesine okuyup özetlemek. Öncelikli: qp02
database, qp02 hammadde (güncel versiyonları var, henüz işlenmedi), standartlar.

**2026-09-01:** İş takibi ikiye ayrıldı — `Proje Bazlı İşler.md` (tek seferlik, başı-sonu
belli işler) ve `Rutin İşler.md` (tekrarlayan/dönemsel işler), ikisi de
`🏰 300-Projects/Yapı Kimyasalları 101/` altında. Akif not attıkça `not-defteri-isleme`
skill'i ikisine ayrıştırıp dağıtacak. İlk örnek işlendi: "Aylık rapor hazırlığı" → Rutin
İşler'e taşındı.

### Thread: Web Tasarım Freelance — Ekip Oluşturma
**Status:** 🟢 Active: created 2026-08-27
"Hiç kaçarın yok" — Akif + Dündar ekibi kuruldu. Anahtar teslim web sitesi paketi (Basic/Standart/Premium,
hazırlanma süresiyle), aylık destek ve reklam yönetimi aboneliği. Acil hedef: Hafta 1-2'de 3-4 müşteri,
15-30k₺ nakit. [[project_web_tasarim_freelance]]

**2026-08-28:** `Satış Planı.xlsx` üretildi (vault + OneDrive/website proje). Üreteç:
`build_satis_plani.py`. Basic paket teknik kapsamı tanımlandı, fiyat 3.000₺. Fiyatlandırmaya 500₺
pazarlık payı eklendi (her paket +500₺). Excel add-in sürülemiyor — script ile üretip her turda
yeniden yazıyoruz. `/derle` komutu manuel derleme için.

**2026-08-29:** MEGA SPRINT — Web templates live!
- **Cafe repository** (Standart Package): Slider + FAQ + Hero background + section overlays. 3 commits.
- **Basic Template repository** (yeni): Generic responsive template, resimlerle. 2 commits.
- GitHub repos oluşturuldu, commits yapıldı, push pending (Akif auth yapacak).
- localhost:8000 → Cafe (demo), localhost:8001 → Basic (demo)
- Kapı kapı satış ready! 🚀

**2026-08-31:** standart-paket reposu sıfırdan yazıldı (eski `cafe` terk edildi).
Bootstrap 5 + Swiper.js + vanilla JS, SEO tam donanımlı, filtrelenebilir menü + WhatsApp +
sosyal medya footer. Art arda gelen mobil taşma bug'ları kök sebebine inilerek çözüldü
(detay: Last-Session.md, kalıcı bilgi: [[responsive-yatay-tasma-teshis-ve-cozum]]).
Canlı: https://regular07.github.io/standart-paket/ — kullanıcı memnun ("eline sağlık
sorunum düzeldi"). Yeni skill kuruldu: `/responsive-tasma-testi`.

**✅ ÇÖZÜLDÜ (2026-09-01 akşam):** `git push`/`git remote`/`git fetch` izin kuralı Akif
tarafından `.claude/settings.local.json`'a eklendi (Claude kendi izin dosyasını
düzenleyemediği için, Akif kendi terminalinden bir Python komutuyla ekledi). Canlı test
edildi, artık hiç onay istemeden çalışıyor.

**✅ ÇÖZÜLDÜ (2026-09-01 akşam):** compile.py gece otomasyonu sorunu tam çözüldü. İki ayrı
sorun vardı: (1) macOS Tam Disk Erişimi eksikti — python3 sembolik bağlantısı Finder'da
seçilemediği için `/usr/sbin/cron`'un kendisine izin verildi (python3 yerine, daha sağlam
çözüm), (2) OneDrive'ın online-only dosyaları arka plan sürecine servis edememesi —
AkifOS klasörü "Her zaman bu cihazda tut" yapılarak çözüldü. `launchd` denemesi geri
alındı, sade `cron` ile devam ediliyor (0 3 * * *). Canlı testle doğrulandı
(`ONEDRIVE-OK-2` — cron'dan OneDrive dosyası başarıyla okundu).

**Marka ismi kesinleşti: Deeploico** (2026-08-31). 11 turluk isim arayışı sonunda karar
verildi — detay: [[kalem-kod-marka-isim-arastirmasi]]. TODO: TürkPatent kontrolü + domain
kaydı (kullanıcı yapacak), sonra logo/görsel kimlik tasarımına geçilecek.

**AÇIK SORU (Akif düşünecek, arada sor):** Basit Destek 500₺ → 1.000₺ oldu, aylık mı talep başı mı?

**Web Sitesi TODO Listesi (Deeploico portfolyo, regular07.github.io):**
1. 🔲 Deeploico markasını TürkPatent'te kontrol et + domain kaydı yap (Akif yapacak)
2. 🔲 Logo / görsel kimlik tasarımı — sıradaki oturum konusu, henüz başlanmadı
3. 🔲 Ana sayfa (vitrin) inşası — Hero, Hizmetler+Paketler, Demo/Portfolyo galerisi,
   İletişim/Teklif Al formu, Footer (standart-paket'in kanıtlanmış taşmasız temeliyle)
4. 🔲 CV/Hakkımda sayfası (2. sayfa) — içerik detayı henüz konuşulmadı
5. 🔲 Müşteri demo'su — standart-paket linkini kapı kapı/DM ile potansiyel müşterilere gönderme
6. 🔲 standart-paket şablonunu diğer sektörlere türetme (kuaför, restoran vb.) — her biri ayrı repo
7. 🔲 Eski `cafe` reposu ne olacak — silinsin mi, dursun mu, karar verilmedi
8. 🔲 Basit Destek paketi fiyatlandırma modeli netleşince Satış Planı'na işlensin

### Thread: Ev sorumlulukları konuşması
**Status:** 🟢 Active: created 2026-08-27, güncellendi 2026-08-31
İş ve ev konularını bilinçli ayırıyor — bu thread'i sadece ev konusu açıldığında kullan,
iş oturumlarına karıştırma.

**Klima motoru garip ses çıkarıyor (2026-08-31):** Şimdilik izlemede, tekrar ederse
servis aranacak. **Bu konu ev bağlamında her açıldığında hatırlat/sor.**

**🔴 ÖNEMLİ TAKİP — Elektrik abonelik/zarar süreci (2026-09-01, 1 hafta boyunca SÜREKLİ
hatırlatılacak):**

*Tarihçe:*
- 2025 Aralık: Aboneliği ticaretten meskene çevirme talebi yapıldı — hiç dönüş olmadı
- 06.03.2026: İkinci talep yapıldı — yine dönüş olmadı
- 2026-09-01: Akif şirkete gitti, hem meskene çevirme işini hem de bu gecikmeden
  kaynaklanan geriye dönük zararının karşılanmasını talep etti (zarar talep formu dolduruldu)

*Şirketin sözü:* Bu hafta içinde meskene çevirme için ekip gönderecekler. Zarar talep formu
incelenecek, sonuç mesajlardan takip edilebilir ya da şubeye tekrar uğranabilir dediler.

*Neden kritik:* Akif "1 hafta boyunca takip edeceğim, 1 hafta içinde aksiyon alınmazsa
şikayet talebinde bulunacağım" dedi — Todoist'e 3 görev eklendi (ekip geldi mi, zarar
talebi sonucu, 8 Eylül'de aksiyon yoksa şikayet). **Bu konuyu ev bağlamı her açıldığında
hatırlat, sadece sorulunca değil — Akif özellikle "sürekli hatırlatman lazım" dedi.**

**Ev görevleri — netleşmiş plan (2026-09-01):**

*1 Eylül:*
- ✅ Elektrik faturası ödendi + abonelik meskene çevrildi
- ✅ Hobi odası pimapenler için Ömer Üzümcü arandı

*2 Eylül (ertesi gün):*
- 🔲 Gardırop için değişim talebinde bulun (servis değil — detay aşağıda) — eşinin
  telefonuyla hoparlörden ara, Granola ile kayıt altına al
- Kettle almaya git
- Pattex 502 al
- Talaş tozu ve ahşap tutkalı satın al (çöp dolabı tamiri için)

*4 Eylül'e kadar (ayın 5'i gelmeden):*
- **Kira öde (23.000₺)** — p1, kritik deadline

*Hafta içinde, MUTLAKA hatırlatılacak:*
- Mutfak çöp dolabını doğru monte et — Akif özellikle vurguladı, "evime biraz özen
  göstermem lazım" dedi, bu görevi unutturma

*İzlemede:*
- Klima garip ses (tekrarlarsa servis)

**🪑 Gardırop — değişim talebi süreci (2026-08-03/04'te ilk konuşuldu, 2026-09-01'de aksiyona
geçildi):**
- 8. kez servis çağrılmış, tekrarlayan arıza. Ürün 07.01.2026'da alındı, garanti kapsamında.
- Fatura annesinin üzerine, anne ile Akif konuşmuyor — bu **para iadesi** için hukuki engel
  ama **değişim** için değil (fiziksel teslim-tesellüm Akif üzerinden yürüyebilir).
- **Hukuki dayanak (Ayıplı Mal Yönetmeliği):** garanti süresi içinde aynı arızanın 4+ kez ya
  da toplam arızaların 6+ kez tekrarı → tüketici doğrudan değişim/bedel iadesi talep edebilir,
  firma "tamir edelim" diyemez. Akif 8 kez ile bu şartı fazlasıyla aşmış.
- **Karar (2026-09-01):** Akif değişim talebinde bulunacak (iade değil).
- **Kayıt yöntemi:** Görüşme telefonla yapılacak (eşinin telefonu, hoparlörden), **Granola
  ile kayıt altına alınacak** — "hakkımızı aramak daha rahat olur" dedi, kanıt için önemli.
- **2 Eylül'e ertelendi** (1 Eylül'den taşındı, Granola kaydı için planlama gerekti).
- **Adımlar:** 8 servis kaydını (fiş/tarih/arıza açıklaması) topla → firmayı ara, Granola ile
  kaydet → reddederse İl/İlçe Tüketici Hakem Heyeti'ne ücretsiz başvuru.
- Todoist görevi güncellendi: "Gardırop için değişim talebinde bulun"

**Akşam vardiyası günü sabah rutini:** Bu plan SADECE akşam vardiyasında çalıştığı
günler için — genel "sabahçı" durumu değil. 2026-08-31 örneği: 10:00 uyandı → 11:30
kahvaltı (koşuşturmalı) → 14:30 servise biniş. Önerilen düzen: 09:00 uyan → 09:15-09:45
kahvaltı hazırlığı → 09:45-10:15 sakin kahvaltı → 10:15-13:00 boş zaman → 13:00-14:15
hazırlan/tampon → 14:15 çıkışa hazır. Akşam vardiyası olan başka bir günde konu açılırsa
bu düzeni hatırlat.

## Closed Threads
(none)
