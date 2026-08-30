---
connects: [recete-olceklendirme-ve-fabrika-entegrasyonu, psd-gradasyon-hesaplama]
sources: [import-2026-07-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# Reçete Ölçeklendirme ↔ PSD ve Gradasyon Hesaplaması

## Bağlantı

Ölçeklendirme dosyasındaki (o_lc_ekleme.xlsx) reçete ağırlık oranları, rutin elek analizi verisi hiç tutulmayan ürün gruplarında (seramik yapıştırıcısı gibi) gradasyon eğrisini tahmin etmenin temel girdisidir: her hammaddenin kendi ölçülmüş elek dağılımı, reçetedeki ağırlık yüzdesiyle çarpılıp toplanarak ürünün "reçete ağırlıklı teorik PSD" eğrisi hesaplanır.

## Ana Fikir

Reçete ölçeklendirme aracı başlangıçta sadece üretim miktarını (2600 kg → 1 kg gibi) oranlamak için tasarlanmıştı, ama aynı oran verisi PSD hesaplamasına aktarılınca doğrudan ölçüm yapılmayan ürünler için de gradasyon tahmini mümkün hale geldi. Bu, tek bir reçete veri kaynağının (hammadde ağırlık oranları) hem üretim planlama hem kalite/formülasyon analizinde tekrar kullanılabildiğini gösteren somut bir örnektir.
