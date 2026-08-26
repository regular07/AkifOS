---
title: GitHub Pages ile Statik Site Yayınlama
aliases: ["GitHub Pages", "github.io hosting"]
tags: ["hosting", "deployment", "github", "statik-site"]
sources: ["import-2026-03-part-001.md"]
created: 2026-08-26
updated: 2026-08-26
---

# GitHub Pages ile Statik Site Yayınlama

GitHub Pages, bir GitHub reposundaki statik dosyaları (`index.html`, `css/`, `js/`) ücretsiz bir URL üzerinden yayınlayan servistir. Kullanıcı adıyla aynı isimde açılan `kullaniciadi.github.io` reposu ana portföy sayfası olurken, farklı isimli her repo kendi alt yolunda (`kullaniciadi.github.io/repo-adi`) ayrı bir proje olarak yayınlanır. Dosyalar Git komutları bilmeden GitHub'ın web arayüzünden "Upload files" ile de yüklenebilir, bu da teknik bilgisi az kullanıcılar için uygundur.

## Önemli Noktalar
- Ana profil sitesi için repo adı tam olarak `kullaniciadi.github.io` olmalı; kullanıcı adı sonradan değiştirilirse bu adres ve tüm eski linkler bozulur.
- Ek projeler ayrı repo olarak açılır ve repo adı URL'nin alt yolunu belirler (`/repo-adi`); URL'ye ekstra `/` eklemek yeterli değildir, gerçek bir repo gerekir.
- Repo/URL isimlerinde Türkçe karakter kullanılmamalı (`kuaför` yerine `kuafor`), aksi halde URL çirkin yüzde-kodlamalı hale gelir.
- Aktivasyon: Settings → Pages → Source: "Deploy from a branch" → `main` seçilip kaydedilir, birkaç dakika içinde site yayına girer.
- Bilgisayarı olmayan/tablet kullanan kullanıcılar için dosya indirip yükleme yerine GitHub web arayüzünde doğrudan "kopyala-yapıştır" ile dosya oluşturma alternatif bir yöntemdir.

## Detaylar
Kullanıcı `demetsen23` / `regular07` hesabıyla birden fazla landing page'i (kafe, restoran, kuaför vb.) ayrı repolar halinde yayınlamayı planladı. Her sektör için ayrı repo açılıp `regular07.github.io/kafe` gibi bağımsız bir demo linki üretilmesi, bu linklerin freelance platformlarında (Bionluk, Fiverr) müşteriye "canlı önizleme" olarak gönderilmesi amaçlandı. Ana repo (`regular07.github.io`) ilk aşamada deneme amaçlı bir örnek landing page ile dolduruldu, sonrasında gerçek bir portföy ana sayfasına dönüştürülmesi planlandı. Claude'un GitHub hesabına doğrudan bağlanıp dosya gönderemeyeceği, bu yüzden dosyaların manuel olarak (indirilip yüklenerek ya da kopyala-yapıştır ile) aktarılması gerektiği netleştirildi.

## İlgili Kavramlar
- [[cloudflare-pages-ile-statik-site-yayinlama]] — GitHub Pages'e alternatif, domain bağlama ve DNS otomasyonu açısından farklılaşan bir ücretsiz statik hosting seçeneğidir.
- [[landing-page-freelance-pazarlama-stratejisi]] — Üretilen landing page örnekleri GitHub Pages üzerinden yayınlanarak müşterilere gösterilecek portföy/demo linklerine dönüştürülür.

## Kaynaklar
- import-2026-03-part-001.md
