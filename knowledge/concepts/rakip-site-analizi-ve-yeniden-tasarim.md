---
title: Rakip Site Analizine Dayalı Yeniden Tasarım
aliases: ["Site referans alarak yeniden tasarım", "Ürün filtreleme mindmap"]
tags: ["web-tasarim", "rakip-analizi", "urun-filtreleme", "telif-hakki"]
sources: ["import-2026-03-part-001.md"]
created: 2026-08-26
updated: 2026-08-26
---

# Rakip Site Analizine Dayalı Yeniden Tasarım

Mevcut bir sitenin (antalyayangin.com.tr) kaynak kodunu birebir kopyalamak yerine, sitenin yapısını (bölümler, kategoriler, gezinme akışı) referans alıp tamamen orijinal HTML/CSS/JS ile yeniden inşa etme yaklaşımıdır. Site sahibi tarafından net ürün bilgisi verilmediği için önce hizmetler bölümündeki kategorilerden yola çıkarak bir mindmap/ürün ağacı çıkarılır, ardından navbar'a eklenecek "Ürünler" sayfası bu kategorilere göre filtrelenebilir hale getirilir.

## Önemli Noktalar
- Birebir kaynak kodu kopyalama telif hakkı ihlali riski taşır; bunun yerine aynı bölüm/akış yapısı sıfırdan, temiz kodla yeniden yazılır.
- Site 403 döndürüp doğrudan erişime kapalı olduğunda, sayfanın `Ctrl+U` (view-source) ile alınan HTML çıktısı analiz için kullanılabiliyor.
- Hedef sitenin kendi özel CSS/JS dosyaları (`app.css`, `bootstrap.min.css`, `sal.css`, `slick.css`) yerel ve kopyalanamaz olduğundan, görsel atmosfer (renk paleti, tipografi, kurumsal his) korunarak Bootstrap 5 tabanlı temiz bir yapı kuruluyor.
- Ürün bilgisi eksikliğinde önce hizmetler bölümündeki kategoriler çıkarılıp 5 ana grupluk bir ürün mindmap'i (Algılama & İhbar, Söndürme Sistemleri, Yangın Durdurucu Ürünler, Kapı & Perde, Duman & Oksijen) oluşturuluyor; ürün detayları site sahibinden parça parça toplanıyor.
- Çok sayfalı site mimarisi (index, hizmetler, urunler, hakkimizda, iletisim) ve `urunler.html?kategori=...` gibi URL query param'lı filtreleme yapısı planlanıyor.

## Detaylar
Kullanıcı, tanıdığı bir yangın güvenlik firmasının (antalyayangin.com.tr) sitesini müşteri adına yeniden tasarlamak istedi; asıl talep navbar'a bir "Ürünler" butonu eklemek ve bu ürünleri hizmetler bölümündeki sistemlere göre filtrelenebilir kılmaktı. Site doğrudan erişime kapalı olduğu için kullanıcı `Ctrl+U` ile view-source çıktısını paylaştı, bu üzerinden site analiz edilip 5 kategorilik mindmap ve çok sayfalı dosya mimarisi (`index.html`, `hizmetler.html`, `urunler.html`, `hakkimizda.html`, `iletisim.html`, `css/style.css`, `js/main.js`, `js/products.js`) çıkarıldı. İlk üretim adımında kırmızı/koyu kurumsal tema ile `index.html`, `style.css` ve `main.js` yazıldı; hizmetler sayfasının 13 hizmet kartıyla birlikte devamı planlandı.

## İlgili Kavramlar
- [[landing-page-freelance-pazarlama-stratejisi]] — Bu proje, önceki oturumlarda pratik amaçlı üretilen örnek landing page'lerin öğrenildiği tekniklerin gerçek bir müşteri işine uygulanmasıdır.
- [[github-pages-ile-statik-site-yayinlama]] — Çok sayfalı bu site de tamamlandığında benzer statik hosting yöntemleriyle yayınlanması beklenir.

## Kaynaklar
- import-2026-03-part-001.md
