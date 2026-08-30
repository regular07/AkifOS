---
title: Reçete Ölçeklendirme ve Fabrika Entegrasyonu (Scale-Up)
aliases: [ölçekleme Excel dosyası, o_lc_ekleme, batch büyütme, reçete kütüphanesi, scale-up]
tags: [yapi-kimyasallari, formulasyon, uretim, excel]
sources: [import-2026-07-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# Reçete Ölçeklendirme ve Fabrika Entegrasyonu (Scale-Up)

Kuru harç fabrikalarında laboratuvar/üretim reçeteleri (orijinal şarj 2000/2600 kg gibi) istenen herhangi bir hedef miktara (1 kg, 100 kg vb.) oranlanarak ölçeklendirilebilir: her hammaddenin miktarı orijinal şarja bölünüp "kg başına oran" bulunur, bu oran hedef miktarla çarpılarak yeni reçete elde edilir. Reçeteyi laboratuvar ölçeğinden fabrika üretimine taşırken (scale-up) miktar oranlamanın ötesinde homojenlik, dozaj toleransı ve hammadde ekleme sırası gibi ek mühendislik faktörleri devreye girer.

## Önemli Noktalar

- Ölçeklendirme formülü basittir: `kg_başına_oran = hammadde_miktarı / orijinal_şarj_kg`, `yeni_miktar = kg_başına_oran × hedef_kg`; Excel'de tek bir sarı hücreye hedef kg girilince tüm hammadde satırları otomatik güncellenir.
- Fabrikanın reçete kütüphanesi (o_lc_ekleme.xlsx örneğinde 36 ürün) her ürünü ayrı sekmede tutar; ortak bir "hammaddeler" referans sekmesi hammadde kodu/tanım/ana grubu (Agrega, Bağlayıcı, Kimyasal) eşleştirir — bu yapı hem ölçeklendirme hem PSD/gradasyon hem SAP QP02 kalite kontrol dosyalarıyla çapraz referans için ortak temel oluşturur.
- Laboratuvardan fabrika ölçeğine geçişte (scale-up) dikkat edilmesi gerekenler: mikser tipinin (planeter, ribbon blender, kulplu mikser) ve karıştırma süresi/hızının homojenliğe etkisi, az miktarda kullanılan katkılarda (RDP, selüloz eter, lifler) tartım hassasiyeti (büyük ölçekte %0.1'lik sapma bile performansı değiştirebilir), ve silo/big-bag ekleme sırasının laboratuvar sırasıyla birebir aynı olması (özellikle selüloz eterin ıslanma davranışı nedeniyle).
- Fabrikaya tam geçmeden önce küçük bir pilot üretim (100-200 kg) ile laboratuvar sonuçlarının doğrulanması önerilen bir ara adımdır.
- Reçete oranları, doğrudan elek analizi verisi tutulmayan ürün gruplarında (ör. seramik yapıştırıcısı) PSD/gradasyon tahmininin de temelini oluşturur: her hammaddenin kendi elek dağılımı reçetedeki ağırlık oranıyla çarpılıp toplanarak ürünün teorik gradasyon eğrisi hesaplanır.

## Detaylar

Reçete kütüphanesindeki ürün aileleri (weber.kol seramik yapıştırıcıları, weber.dress sıvalar, weber.therm yalıtım ürünleri, weber.joint derz dolguları, weber.min ürünleri), hammadde gruplarına göre (Agrega: kalker/dolomit/taş tozu; Bağlayıcı: çimento/kireç/uçucu kül; Kimyasal: selüloz eter, nişasta eteri, polimer, priz hızlandırıcı vb.) sınıflandırılır. Bu sınıflandırma, hem ölçeklendirme dosyasında hem SAP QP02 hammadde kalite kontrol formatında aynı malzeme kodlarıyla birebir eşleşir, böylece iki dosya arasında (örn. reçetede olup kalite kontrol tablosunda eksik olan ürünleri bulmak için) kod bazlı karşılaştırma yapılabilir.

## İlgili Kavramlar

- [[psd-gradasyon-hesaplama]] — Reçete ağırlıklı teorik PSD hesaplaması, bu makalede anlatılan reçete kütüphanesindeki hammadde ağırlık oranlarını doğrudan girdi olarak kullanır.
- [[hammadde-sap-kalite-kontrol-formati]] — Reçete kütüphanesindeki hammadde kodları, SAP QP02 formatındaki hammadde kalite kontrol sayfalarıyla malzeme kodu üzerinden eşleştirilerek eksik/tutarsız kayıtlar tespit edilir.

## Kaynaklar

- import-2026-07-part-001.md
