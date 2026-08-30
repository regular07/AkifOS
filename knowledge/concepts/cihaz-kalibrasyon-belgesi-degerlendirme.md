---
title: Cihaz Kalibrasyon Belgesi Değerlendirme (ISO 7500-1)
aliases: [kalibrasyon sertifikası okuma, Zwick kalibrasyon, ISO 7500-1 sınıf 0.5, genişletilmiş ölçüm belirsizliği, relatif gösterge hatası, tekrarlanabilirlik histerezis, çekme basma cihazı doğrulama]
tags: [kalite-kontrol, metroloji, kalibrasyon, olcum-belirsizligi, test-cihazi]
sources: [import-2026-08-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# Cihaz Kalibrasyon Belgesi Değerlendirme (ISO 7500-1)

Bir test cihazının (ör. Zwick çekme/basma makinesi) kalibrasyon sertifikasından ölçüm belirsizliğini okuma ve "cihaz doğru mu ölçüyor" kararını verme yöntemi. Sertifikada üç şey aranır: sınıf beyanı (ISO 7500-1'e göre ör. sınıf 0,5), yük basamakları tablosundaki hata sütunları (gösterge hatası, tekrarlanabilirlik, histerezis) ve genişletilmiş ölçüm belirsizliği. Karar, ölçülen hataların sınıf limitinin altında kalıp kalmadığına bakılarak verilir.

## Önemli Noktalar

- **Genişletilmiş ölçüm belirsizliği U:** sertifikanın son sütun(lar)ında, k=2 kapsam katsayısıyla (%95 güven) verilir; cihazın okuduğu her değerin gerçek değere sapma payıdır. Örnek (Zwick): basmada ±%0,16; çekmede ±%0,10 (tek yön) / ±%0,14 (artan-azalan birleşik).
- **Sınıf beyanı:** ISO 7500-1'e göre sınıf 0,5 → izin verilen gösterge hatası ±%0,5. Uygunluk beyanı bölümünde çekme ve basma için ayrı verilir (hata profilleri farklı olduğundan iki yön ayrı değerlendirilir).
- **"Doğru ölçüyor mu" kararı üç sütuna bakılarak verilir:** relatif gösterge hatası q (referans yük hücresine göre % sapma), tekrarlanabilirlik b, histerezis v — her biri sınıf limitinin (%0,5) altında olmalı. Örnekte en yüksek q basmada %0,203, çekmede %0,054; b ve v ~%0,1 → sınıf 0,5 sağlanıyor, cihaz doğru ölçüyor.
- **Sertifika bir tarihteki durumu yansıtır** (ör. 17.12.2025); periyodik kalibrasyon aralığı boyunca geçerli kabul edilir.
- **Ölçüm belirsizliği, test sonucunun raporlanan değerine bir bant ekler;** spesifikasyon sınırına çok yakın sonuçlarda uygunluk kararı verirken bu bant dikkate alınmalıdır (ISO/IEC 17025 mantığı).

## Detaylar

Sertifikada aranacak yapı: kapak / uygunluk beyanı (sınıf), yük basamakları tablosu (her basamakta q, b, v değerleri) ve genişletilmiş belirsizlik sütunu. Bir cihazın "sınıfına uygun" sayılması için gösterge hatası, tekrarlanabilirlik ve histerezis kriterlerinin hepsinin birden sınıf eşiğini karşılaması gerekir; sadece belirsizliğin düşük olması yetmez. Bu okuma becerisi, "sadece spesifikasyona uygun mu" değil "ölçüm sistemimin kendisi güvenilir mi" sorusunu sorabilmenin parçasıdır ve renk ölçümü / kalibrasyon iş vakasıyla aynı çerçeveye oturur.

## İlgili Kavramlar

- [[ty-ak-test-standart-kod-referansi]] — Zwick makinesi TY.AK.225 (çekme yapışma) ve EN 1348 gibi testlerde kullanılır; cihazın kalibrasyon belirsizliği bu test sonuçlarının güvenilirliğinin üst sınırını belirler.
- [[yapi-kimyasallari-urun-standartlari]] — EN 12004 / EN 1015 sınıf eşiklerine (ör. çekme yapışma ≥1,0 N/mm²) yakın sonuçlarda, ölçüm belirsizliği bandı uygunluk kararını doğrudan etkiler.
- [[spektrofotometrik-renk-olcumu-xrite]] — her iki konu da "ölçüm sisteminin kendisi güvenilir mi" sorusudur (biri kuvvet, diğeri renk); ISO/IEC 17025'in ölçüm belirsizliği ve kalibrasyon maddeleri ortak dayanaktır.

## Kaynaklar

- import-2026-08-part-001.md
