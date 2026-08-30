---
title: SAP QP02 Hammadde/Ürün Kalite Kontrol Formatı
aliases: [QP02 format, SAP kalite kontrol tablosu, kontrol karakteristiği tablosu, kırma eleme dosyası, partoz dosyası]
tags: [yapi-kimyasallari, kalite-kontrol, sap, excel]
sources: [import-2026-06-part-001.md]
created: 2026-08-26
updated: 2026-08-28
---

# SAP QP02 Hammadde/Ürün Kalite Kontrol Formatı

Fabrikada SAP QP02 işlemi kapsamında her ürün veya hammadde için ayrı Excel sayfası tutulur; her sayfa malzeme kodu, ürün/hammadde adı, işlem (ör. "0010 ürün/hammadde kalite kontrolü") ve plan grubu meta bilgileriyle başlar, ardından standart bir sütun yapısına sahip kontrol tablosu gelir. Bu format hem ürünler hem hammaddeler için birebir aynı şablonda kullanılır ve günlük/partili ölçüm verilerinin (ör. elek analizi, elek üstü kalan gram) sistematik olarak kaydedilmesini sağlar.

## Önemli Noktalar

- Standart sütun yapısı: **Krkt. | Kontrol Karakteristiği | Ölçü Br | Alt sınır | Üst sınır | Bilgi alanı 1-3**; her satır bir test parametresini (ör. elek analizi 355 µm, görsel kontrol, analiz sertifikası) temsil eder.
- Hammadde sayfalarında tipik kontrol karakteristikleri: görsel kontroller, parti/lot no, üretim/son kullanma tarihi, analiz sertifikası, elek analizi (birden fazla elek boyutu + tava), nem tayini, renk/renk şiddeti (L/A/B/DE), toz yoğunluk tayini.
- Aynı fabrikada bu formatın farklı veri kaynaklarıyla beslenen türevleri vardır: "kırma eleme dosyası" (kalker gibi kırılan/elenen hammaddelerin ölçüm kayıtları), "partoz dosyası" (sıva ürünlerinin elek analizi ölçümleri), "QP02 database" (olması gereken spec alt-üst sınır referans tablosu).
- STD satırı (spec) dosyanın başında ayrı tutulur ve zamanla malzeme değişse (ör. 0-160 µm → 0-200 µm kalker) bile otomatik güncellenmez — bu nedenle periyodik olarak gerçek ölçüm verisiyle karşılaştırılıp geçerliliği doğrulanmalıdır (bkz. [[kalker-kayma-sorunu-vaka-analizi]]).
- Format, yeni hammadde eklerken kolayca çoğaltılabilir: mevcut ürün formatı referans alınıp malzeme kodu/adı/spec değerleri SAP ekran görüntüleri veya analiz sertifikalarından okunarak doldurulur.

## Detaylar

Bu format, ürün kalite kontrolünden hammadde kalite kontrolüne bire bir taşınabilir bir şablondur — sütun yapısı değişmez, sadece malzeme kodu ve kontrol karakteristikleri değişir. Örneğin "QP02 Hammaddeler" adlı bir dosyada 10 hammadde (Hostapur OSB, Niğtaş NGE 1020, Tylose MH 20006, Uçucu Kül, dolomit, Portland çimento, beyaz çimento vb.) için ayrı sayfalar oluşturulmuş, her biri SAP ekran görüntüleri ve PDF analiz sertifikalarından derlenen alt/üst sınır değerleriyle doldurulmuştur.

Fabrikanın PSD/gradasyon çalışmalarında bu format doğrudan girdi kaynağı olarak kullanılır: kırma eleme ve partoz dosyalarındaki elek üstü kalan gram/yüzde verileri, kümülatif geçen % hesaplamasına ve Fuller eğrisi karşılaştırmasına temel oluşturur (bkz. [[psd-gradasyon-hesaplama]]).

## İlgili Kavramlar

- [[psd-gradasyon-hesaplama]] — Bu formattaki elek analizi satırları (elek üstü kalan gram/yüzde), PSD ve gradasyon hesaplamasının ham veri girdisidir.
- [[kalker-kayma-sorunu-vaka-analizi]] — Kayma sorununun kök nedeni, bu formatta tutulan kırma eleme dosyasındaki tarihsel elek analizi verileri incelenerek tespit edilmiştir.
- [[sap-qm-kalite-kontrolde-kalan-stok-sorun-giderme]] — QP02'de kayıtlı muayene partisi bulunamadığında, sorunun SAP tarafındaki (QA32, MB51, MB5B) işlemsel kök nedenini bulma sürecidir.

## Kaynaklar

- import-2026-06-part-001.md
- import-2026-07-part-001.md
