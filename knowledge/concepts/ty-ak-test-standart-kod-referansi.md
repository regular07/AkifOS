---
title: TY.AK Test Standart Kod Referansı
aliases: [TY.AK kodları, MA.AK kodları, fabrika iç test yöntemi dokümanı, TYAK referans dokümanı]
tags: [yapi-kimyasallari, kalite-kontrol, standart, dokumantasyon]
sources: [import-2026-07-part-001.md, import-2026-07-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# TY.AK Test Standart Kod Referansı

Fabrikanın iç test yöntemi dokümanları TY.AK.XXX kod sistemiyle numaralandırılır (örn. TY.AK.018 Elek Analizi, TY.AK.001/009 Open Time, TY.AK.010/161 Kayma Tayini); ancak bu kodların resmi bir master listesi yoktur ve farklı Excel dosyalarına (qp02_database, PARTOZ, HAMMADDE_2026) dağınık şekilde geçer. Fabrika-içi test yöntemleriyle TS EN 1015 serisi ve TS EN 12004 (seramik yapıştırıcı) ailesi arasındaki eşleşme çıkarılıp, karşılığı olmayan test yöntemleri için kendi MA.AK.XXX kod serisi taslak olarak oluşturulmuştur.

## Önemli Noktalar

- TY.AK kodları tek bir kaynakta değil, birden fazla Excel dosyasına dağınık geçer: **qp02_database.xlsx** en kapsamlı kaynaktır (14 kod), PARTOZ'da bazı kodlar (ör. TY.AK.017) sadece orada geçer, HAMMADDE_2026'da ise (TY.AK.036, TY.AK.087) qp02_database'de hiç bulunmayan kodlar vardır — tam liste için birden fazla dosyaya bakmak gerekir.
- Örnek kod-test eşleşmeleri: TY.AK.018 Elek Analizi, TY.AK.001/009 Open Time (açık zaman), TY.AK.010/161 Kayma Tayini, TY.AK.035 Harç Yoğunluğu, TY.AK.036 Nem Tayini, TY.AK.124 Therm/Min grubu sıvalarda Flow Table yayılma tayini, TY.AK.225 Çekme Yapışma Kuvveti/Su Tutma Testi.
- TY.AK.124'te tanımlı karıştırma parametreleri: 500 gr ürün, Bosch marka mikser, 1. devir — Min grubu (weber.min deko) için 15 sn, Therm grubu için 25 sn karıştırılır; su oranı ise ürünün kendi QP02 kalite kontrol planındaki karışım oranından alınır.
- TS EN 12004 (seramik yapıştırıcı) ailesindeki bazı resmi test yöntemlerinin (EN 1348 çekme yapışma mukavemeti, EN 12002 enine deformasyon/esneklik) ve TS EN 1015 serisindeki bazı bölümlerin (EN 1015-9 genel harçlar, EN 1015-19 su buharı geçirgenliği) fabrika içinde karşılığı olmadığı tespit edilmiş, bunlar için MA.AK.001-004 taslak kodları oluşturulmuştur — bunlar resmi Weber dokümanları değildir, standardın genel kapsamına dayanan taslaklardır ve resmi kabul öncesi doğrulama gerektirir.
- Kodun tam/birebir metni gerekiyorsa (özet değil), görsellerdeki orijinal başlık ve adım yapısı (TEST METODU, NUMUNE HAZIRLAMA, TESTİN YAPILIŞI, SONUÇLARIN DEĞERLENDİRİLMESİ) korunarak aktarılmalıdır; özetleme fabrika pratiğinde bilgi kaybına yol açar.
- **Kayma tayini dikey bekleme süreleri:** TY.AK.161 (ağır seramik, 300 gr) dikey konumda 5 dk; TY.AK.010 (normal seramik, ref. TS EN 12004-2 / EN 1308) dikey 5 dk; TY.AK.162 (C1/C1T, 200 gr, yalnızca kol standart / XL STD / seraçim max) Metod 1'de süre yok (ağırlık kaldırılıp doğrudan ölçüm), Metod 2'de dikey 3 dk.
- **Açık zaman (open time) referansı EN 1346'dır:** TY.AK.001 (Wetting/Open Time, seramik ile, Weber yöntemi) ve TY.AK.009 (Açık Zaman Tayini, ref. TS EN 12004 / TS EN 13468); Therm grubu sıvalar için ayrıca kendi metodları vardır (TY.AK.019, TY.AK.020, TY.AK.122).
- **TY.AK.160 (Selüloz Eterlerde Viskozite Tayini):** viskozite sınıfına göre değişken test konsantrasyonu kullanır — <20 mPa·s → %4,75 (25 g); 20–80 → %2,85 (15 g); 100–60.000 → %1,9 (10 g); >60.000 → %1 (5 g). Bu bir ham selüloz karakterizasyon/KK testidir, reçete dozaj rehberi değildir. (Kullanıcının andığı "TY.AK.190" diye bir kod yoktur; kastedilen TY.AK.160'tır.) Karışım su oranı için ayrıca TY.AK.170 referans alınır.

## Detaylar

Seramik yapıştırıcılarda kayma/açık zaman testlerinde kullanılan seramik miktarı ürün ailesine göre değişir: çoğu weber.kol ürününde 300 gr ağır seramik kullanılırken, **seraçim max, kol standart ve kol std** ürünlerinde istisna olarak 200 gr seramik kullanılır — bu ayrım TY.AK.161 metninde açıkça belirtilir ve QP02 kalite kontrol planlarında ürün bazında doğrulanır.

TS EN 1015 serisi ile TS EN 12004 (seramik yapıştırıcı) ailesi arasındaki fark önemlidir: 1015 serisi kâgir/sıva harcı test yöntemlerini (taze/sertleşmiş harç), 12004 ailesi ise seramik yapıştırıcıya özgü testleri (EN 1308 kayma, EN 1346 açık süre, EN 1348 çekme yapışma, EN 12002 esneklik) kapsar; 2017'de bu ayrı standartların çoğu EN 12004-2'de tek dokümanda birleştirilmiş olsa da fabrika dokümanlarında hâlâ eski numaralarıyla anılırlar.

Güncelleme (import-2026-07-part-002): Kayma tayini dikey bekleme süreleri (TY.AK.161 ve TY.AK.010 için 5 dk, TY.AK.162 Metod 2 için 3 dk), açık zaman kodlarının EN 1346 karşılığı ve TY.AK.160 selüloz eter viskozite tayininin viskozite sınıfına göre değişen test konsantrasyonu (%1 – %4,75) eklendi. TY.AK.160, bir selüloz eterin başka bir viskozite sınıfıyla ikame edilmesinde reçete dozajının kaba tahmini için de kullanılmıştır (ayrıntı ilgili kavramda).

## İlgili Kavramlar

- [[yapi-kimyasallari-urun-standartlari]] — TY.AK kodları, bu makalede özetlenen EN 1015 ve EN 12004 serisi resmi test standartlarının fabrika içi (iç doküman) karşılığıdır.
- [[psd-gradasyon-hesaplama]] — TY.AK.018 (Elek Analizi), PSD/gradasyon hesaplamasının ham veri kaynağı olan test yöntemidir.
- [[seluloz-eter-viskozite-dozaj-esdegerligi]] — TY.AK.160'ın viskozite sınıfı–konsantrasyon tablosu, selüloz eter ikamesinde dozaj eşdeğerliği hesabının çıkış noktasıdır; TY.AK.009/161/225 ise ikamenin doğrulama testleridir.
- [[deneme-uretimi-alternatif-hammadde-recete-degisikligi]] — Alternatif hammadde deneme partileri bu TY.AK test kodlarıyla (açık zaman, kayma, su tutma) değerlendirilir.

## Kaynaklar

- import-2026-07-part-001.md
