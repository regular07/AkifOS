---
connects: [cloudflare-pages-ile-statik-site-yayinlama, github-pages-ile-statik-site-yayinlama]
sources: ["import-2026-03-part-001.md"]
created: 2026-08-26
updated: 2026-08-26
---

## Bağlantı
Kullanıcı aynı landing page dosyalarını önce Cloudflare Pages üzerinden yayınlamaya çalıştı; domain bağlama sırasında DNS çakışması yaşayınca alternatif olarak GitHub Pages'e yöneldi.

## Ana Fikir
İki servis de statik HTML/CSS/JS dosyalarını ücretsiz yayınlıyor, ancak domain bağlama ve DNS otomasyonu deneyimleri farklılaştığında biri diğerine tamamlayıcı/yedek çözüm olarak devreye giriyor: Cloudflare Pages özel domain + otomatik DNS için, GitHub Pages ise repo başına ayrı proje linkleri (ör. `kullaniciadi.github.io/proje`) üretmek için tercih ediliyor.
