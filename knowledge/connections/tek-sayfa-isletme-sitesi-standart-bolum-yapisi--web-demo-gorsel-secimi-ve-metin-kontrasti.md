---
connects: [tek-sayfa-isletme-sitesi-standart-bolum-yapisi, web-demo-gorsel-secimi-ve-metin-kontrasti]
---

## Bağlantı

Standart bölüm iskeleti (hero → menu → gallery → about → reviews → slider → FAQ → contact)
her demoda kontrol edilecek bölümlerin listesini sabitler. Görsel/metin kontrastı QA'sı da
tam olarak bu bölümler üzerinde, her biri farklı arka plan tonu kullandığı için ayrı ayrı
yürütülür — kafe sitesinde hero ve reviews aynı kontrast tuzağına düştü.

## Ana Fikir

Sabit bölüm iskeleti QA'yı öngörülebilir kılar: hangi bölümlerin kontrast kontrolünden
geçeceği baştan bellidir, böylece hata müşteri görmeden yakalanır.
