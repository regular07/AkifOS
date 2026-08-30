---
connects: [seluloz-eter-viskozite-dozaj-esdegerligi, recete-olceklendirme-ve-fabrika-entegrasyonu]
sources: [import-2026-07-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# Viskozite–Dozaj Eşdeğerliği ↔ Reçete Ölçeklendirme

## Bağlantı

Selüloz eter ikamesi için hesaplanan hedef dozaj (ör. weber.kol Standart'ta ~9,2 kg / 2600 kg), laboratuvar denemesi yapılabilmesi için ölçekleme dosyasındaki (o_lc_ekleme.xlsx) oran mantığıyla küçük partiye — çoğu zaman 1 kg ürün bazına — indirgenir. Aynı reçetenin 5,98 / 7,5 / 9,2 kg'lık üç varyantı da 1000 g'a normalize edilerek DOE noktaları elde edilir.

## Ana Fikir

Ölçeklendirme makalesindeki "az miktarda kullanılan katkılarda tartım hassasiyeti" uyarısı burada kritik hale gelir: 1 kg bazında selüloz eter yalnızca 2–4 g'dır, dolayısıyla 0,01 g hassasiyetli terazi ve sabit su/karıştırma parametresi (TY.AK.170) olmadan deneyin tek değişkeni (selüloz eter miktarı) izole edilemez ve sonuç tartım hatasıyla domine olur.
