---
connects: [uretmeden-sat-web-tasarim-satis-hunisi, web-demo-gorsel-secimi-ve-metin-kontrasti]
sources: [2026-08-29.md]
created: 2026-08-30
updated: 2026-08-30
---

## Bağlantı

Satış hunisinin "üretim" adımı soyut bir aşama değil, somut bir demo sitenin (örnek: La
Dolce Spoon kahve sitesi, Basic Paket) baştan sona hazırlanmasıdır. Bu üretim sürecinde
tekrar eden iki hata sınıfı ortaya çıktı: başarısız CDN görseli yerine gerçek fotoğraf
seçimi ve arka plana göre değişmeyen sabit metin renginin yarattığı kontrast kaybı.

## Ana Fikir

Huninin hızı ("demo düşük maliyetli ve çabuk olmalı") ile kalitesi ("müşteri görmeden
önce temel hatalar yakalanmalı") arasındaki gerilim, her demo üretiminde aynı QA
adımlarının tekrarlanmasını gerektiriyor: görsel kaynağı gerçek fotoğraf mı yoksa
CDN'e bağımlı mı, ve her bölümün metin/arka plan kontrastı ayrı ayrı test edildi mi.
Bu kontrol listesi, huninin üretim adımına sabit bir alt-adım olarak eklenebilir.
