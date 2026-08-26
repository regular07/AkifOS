---
title: Cloudflare Pages ile Statik Site Yayınlama
aliases: ["Cloudflare Pages", "Cloudflare Workers & Pages"]
tags: ["hosting", "deployment", "cloudflare", "statik-site"]
sources: ["import-2026-03-part-001.md"]
created: 2026-08-26
updated: 2026-08-26
---

# Cloudflare Pages ile Statik Site Yayınlama

Cloudflare Pages, HTML/CSS/JS gibi statik dosyaları "Direct Upload" (Upload assets) yöntemiyle sürükle-bırak şeklinde yayına almayı sağlayan ücretsiz bir hosting servisidir. Domain zaten Cloudflare'de kayıtlıysa DNS eşleştirmesi otomatik yapılır ve SSL sertifikası ile CDN dahil ücretsiz sunulur. "Workers & Pages" panelinde "Pages" sekmesi ile "Workers" sekmesi karıştırılabilir; statik site için doğru seçim Pages'tir.

## Önemli Noktalar
- "Create application" → "Pages" sekmesi → "Upload assets" / "Direct Upload" akışı Git bağlamadan dosya yüklemeye izin verir.
- Yanlışlıkla "Workers" sekmesinden deploy edilirse site boş görünebilir; doğru sekme kontrol edilmeli.
- Deploy sonrası verilen `*.pages.dev` adresi test için kullanılabilir, ardından "Custom Domains" ile satın alınan domain bağlanır.
- Aynı domain için DNS'te çakışan eski bir A/CNAME kaydı varsa (ör. başka bir servise ait `www` kaydı) "Add domain" işlemi hata verir; çakışan kayıt dikkatlice tespit edilip silinmelidir.
- Domain bağlanamıyorsa geçici çözüm olarak `*.workers.dev` / `*.pages.dev` adresi reklam ve portföy paylaşımı için kullanılabilir.

## Detaylar
Bir oturumda kullanıcı retro temalı bir landing page'i (`index.html`, `style.css`, `script.js`) Cloudflare Pages üzerinden yayınlamaya çalıştı. İlk denemede proje yanlışlıkla Workers olarak oluşturuldu; "Visit" butonuyla test edilerek sitenin gerçekte çalışıp çalışmadığı doğrulandı. Ardından `demosentia.com` domainini bağlarken mevcut bir A kaydı (`75.2.120.200`) çakışma yarattı; bu kayıt silinirken İkas e-ticaret entegrasyonuna ait `www` CNAME kaydına dokunulmaması gerektiği vurgulandı. Domain sorunları çözülemeyince kullanıcı ücretsiz `workers.dev` alt alan adını, gerçek domainleri ileride müşterilere satana kadar geçici vitrin olarak kullanmaya karar verdi.

## İlgili Kavramlar
- [[github-pages-ile-statik-site-yayinlama]] — Aynı statik siteyi yayınlamak için değerlendirilen alternatif, ücretsiz ve GitHub repo tabanlı bir hosting yöntemidir.
- [[landing-page-freelance-pazarlama-stratejisi]] — Cloudflare Pages'te yayınlanan örnek landing page'ler, freelance pazarlamada müşteriye gösterilecek canlı demo olarak kullanılır.

## Kaynaklar
- import-2026-03-part-001.md
