---
title: Web Demo Üretiminde Görsel Seçimi ve Metin Kontrastı QA'sı
aliases: [text-shadow kontrast, arka plan görseli üzerine metin, kahve sitesi demo, web QA kontrast kontrolü, gerçek fotoğraf vs soyut desen, La Dolce Spoon]
tags: [web-tasarim, ui-ux, qa, freelance, gorsel-tasarim]
sources: [2026-08-29.md]
created: 2026-08-30
updated: 2026-08-31
---

> Güncelleme (2026-08-31, 2026-08-29.md yeniden derlendi): QA döngüsünün pratik
> özellikleri netleşti — kontrast düzeltmeleri tek seferde değil, bölüm bölüm ve
> çok sayıda küçük commit ile (kafe oturumunda 9 commit) yapılır; hero bölümü QA
> onayı alırken reviews bölümü ayrı bir tur bekler. Site iki repoda geliştirilir
> (şablon + müşteri projesi), ikisi de ayrı push edilir.

# Web Demo Üretiminde Görsel Seçimi ve Metin Kontrastı QA'sı

"Basic Paket" demo sitesi üretirken (örnek: La Dolce Spoon kahve sitesi) tekrarlayan iki
üretim/QA sorunu ve çözümü: arka plan görseli seçimi ve metin okunabilirliği kontrolü.

## Önemli Noktalar

- **Gerçek fotoğraf > soyut desen:** Unsplash CDN başarısız olunca önce SVG dot pattern
  denenmiş, ama Pexels'ten gerçek kahve fotoğrafı eklenince çözüm hem teknik hem görsel
  olarak daha iyi sonuç vermiş — müşteri tarafında gerçek fotoğraf soyut desenden daha
  güçlü etki yaratıyor.
- **Kontrast tuzağı:** krem/açık arka plan üzerinde beyaz yazı yeterli kontrast sağlamıyor,
  gözden kaçırılması kolay bir hata. Koyu arka plan + koyu yazı da aynı sorunu yaratır.
- **Çözüm tekniği:** text-shadow ve arka plana göre değişen yazı rengi (koyu zeminde beyaz,
  açık zeminde koyu) + görselin üzerine yarı saydam overlay eklemek, metnin zemin
  görselinden bağımsız her koşulda okunur kalmasını sağlıyor.
- **QA taraması gerekli her bölüm için:** hero, reviews/yorumlar gibi farklı arka plan
  tonu kullanan her bölüm ayrı ayrı kontrast kontrolünden geçirilmeli — bir bölümde
  düzeltilen kontrast diğerinde otomatik düzelmiyor.

## Detaylar

Bu QA kontrolü, ["üretmeden sat" web tasarım satış hunisinin](uretmeden-sat-web-tasarim-satis-hunisi)
üretim aşamasında ortaya çıkan somut bir üretim/kalite adımıdır: demo hızlı ve düşük
maliyetli olmalı ama görsel/metin kontrastı gibi temel okunabilirlik hataları müşteri
görmeden önce yakalanmalı. Pratik kural: her arka plan değişiminde (hero, section
background, kart görseli) üzerine binen metnin hem açık hem koyu bölgede test edilmesi;
tek bir global metin rengi/gölgesi tüm bölümler için yeterli olmuyor.

## İlgili Kavramlar

- [[uretmeden-sat-web-tasarim-satis-hunisi]] — Bu kontrast/görsel QA'sı, hunideki
  "üretim" adımında Basic Paket demo sitesi hazırlanırken uygulanan somut bir kalite
  kontrolü.
- [[github-pages-ile-statik-site-yayinlama]] — Demo, bu tür statik yayın servisinde
  canlıya alınıp QA sonrası müşteriye link olarak gösteriliyor.
- [[tek-sayfa-isletme-sitesi-standart-bolum-yapisi]] — Bu QA taramasının kapsamı bu
  bölüm iskeletidir; hero, reviews gibi her bölüm ayrı kontrast kontrolü gerektirir.
- [[sablon-repo-ve-musteri-proje-reposu-ayrimi]] — Kontrast/görsel düzeltmelerinden
  genellenebilir olanlar şablon reposuna geri işlenir, müşteriye özel olanlar müşteri
  reposunda kalır.

## Kaynaklar

- 2026-08-29.md
