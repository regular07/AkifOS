---
title: Kalker Agrega Kaynaklı Kayma (Slip) Sorunu Vaka Analizi
aliases: [C2 yapıştırıcı kayma sorunu, seramik kayma problemi, flex dinamik yapıştırıcı kayma, tava payı spec revizyonu]
tags: [yapi-kimyasallari, kalite-kontrol, kok-neden-analizi, kayma]
sources: [import-2026-06-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# Kalker Agrega Kaynaklı Kayma (Slip) Sorunu Vaka Analizi

Bir C2 sınıf seramik yapıştırıcısında (flex dinamik ürünü) yaşanan kayma (slip) sorunu, reçetedeki %52,5 oranındaki ince kalkerin (0-160 µm → sonradan 0-200 µm) PSD verileriyle geriye dönük analiz edilerek kök nedene bağlanmıştır. Sorun, ince kalkerin tava payının (90 µm altı fraksiyon) düşmesiyle su tutma kapasitesinin azalması ve harcın reolojik stabilitesini kaybetmesi olarak açıklanmıştır. Bu, PSD/gradasyon hesaplamasının somut bir kalite sorunu çözümünde nasıl kullanıldığına dair gerçek bir örnektir.

## Önemli Noktalar

- Reçetede ince kalkerin oranı kritik: %5 gibi düşük bir oranda PSD varyasyonunun karışıma etkisi ihmal edilebilirken, %52,5 gibi yüksek bir oranda aynı varyasyon (tava payında birkaç puanlık değişim) karışımın toplam ince fraksiyonunu belirgin şekilde değiştirir.
- Kayma sorunu, malzeme 0-160 µm olarak ölçülürken yaşanmış; 0-200 µm'ye geçişle (ve elek setine 160 µm eklenmesiyle) ürün stabilize olmuştur — bu, çok ince malzemenin (aşırı yüksek tava payı) reoloji dengesini bozabileceğini, sadece "az ince" değil "çok ince" olmanın da risk taşıdığını gösterir.
- 0-200 µm dönemindeki 73 ölçümün istatistiksel analizinde tava payı ortalaması %82,7, minimum %78,8 (0-160 dönemi) → %82,3 (0-200 dönemi) olarak yükselmiş ve standart sapma ±2,48'den ±0,87'ye düşerek stabilite artmıştır.
- Kök neden analizi metodolojisi: (1) reçete oranlarını doğru okumak (bu vakada ilk analizde iki hammadde miktarı ters okunmuş ve düzeltilmiştir), (2) mevcut spec'in hangi döneme/malzemeye ait olduğunu doğrulamak (eski spec 0-160 µm için yazılmış, 0-200 µm'ye geçilince güncellenmemiş), (3) sorunlu ve sorunsuz dönemlerin PSD verilerini karşılaştırmak.
- Önerilen yeni spec, sorunsuz döneme ait gerçek ölçüm istatistiğine (ortalama ± değişkenlik payı) dayandırılmış ve mevcut/eski spec'in gerçek üretim verisiyle örtüşmediği (ör. eski üst sınır %15 iken ölçümler %10-21 arasında çıkması) tespit edilmiştir.

## Detaylar

Analiz sürecinde birkaç yanlış anlama düzeltilmiştir: önce reçetedeki iki kalker türünün (0-710 µm ve 0-160 µm) miktarları karışık okunmuş, ardından hangi dönemin (0-160 mi 0-200 mü) kayma sorunu yaşadığı ters anlaşılmıştır. Doğru resim şu şekildedir: 0-160 µm dönemi → kayma sorunu; 0-200 µm'ye geçiş → ürün düzeldi. Bu nedenle risk analizi, mevcut (sorunsuz) 0-200 µm verisinin altına düşen tava paylarının (özellikle %80'in altı) riskli bölge olarak işaretlenmesi şeklinde yapılmıştır.

Önerilen yeni spec (0-200 µm kalker, sorunsuz dönem istatistiğine göre): 355 µm 0-0, 160 µm 0-2, 90 µm 13-19, tava payı 82-85 (alt sınır güvenlik payıyla). Bu değerler EKK yöntemiyle hesaplanan n katsayısı (≈0,127-0,141, çok ince dolgu malzemesi karakterinde) ile de tutarlıdır.

Pratik ders: agrega/hammadde tedarikçisi veya öğütme inceliği değiştiğinde (0-160→0-200 µm gibi), mevcut spec'in otomatik olarak yeni malzemeye uygun kalmadığı, spec'in her değişiklikte yeniden istatistiksel olarak doğrulanması gerektiği bu vakada somut biçimde gösterilmiştir.

## İlgili Kavramlar

- [[psd-gradasyon-hesaplama]] — Kayma sorununun kök nedeni, Fuller formülü ve EKK n katsayısı yöntemiyle hesaplanan PSD/gradasyon eğrisinin tava payı sapmasına dayanır.
- [[yapi-kimyasallari-urun-standartlari]] — TS EN 12004'teki T (kayma dirençli) sınıfı ve EN 1308 kayma test standardı, bu vakadaki kayma probleminin resmi sınıflandırma/test çerçevesini oluşturur.

## Kaynaklar

- import-2026-06-part-001.md
