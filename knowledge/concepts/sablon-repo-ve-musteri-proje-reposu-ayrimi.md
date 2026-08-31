---
title: Şablon Reposu ile Müşteri Proje Reposunun Ayrılması
aliases: [basic-template reposu, şablon altyapısı, base template repo, müşteri proje reposu, iki repo iş akışı, standart-paket reposu]
tags: [web-tasarim, git, freelance, is-akisi, sablon]
sources: [2026-08-29.md]
created: 2026-08-31
updated: 2026-08-31
---

# Şablon Reposu ile Müşteri Proje Reposunun Ayrılması

Freelance web tasarım işinde her müşteri sitesini sıfırdan kurmamak için iki ayrı git
reposu tutulur: yeniden kullanılabilir bir **şablon/base template reposu**
(`basic-template`) ve o şablondan türetilen **müşteri projesi reposu** (ör. `cafe`).
Kafe sitesi oturumunda ikisi paralel geliştirilmiş ve değişikliklerden sonra her ikisi
ayrı ayrı push edilmiştir.

## Önemli Noktalar

- **İki repo, iki rol:** `basic-template` genel iskeleti (bölüm yapısı, responsive kurallar,
  hover efektleri) taşır; müşteri reposu yalnızca içerik, marka ve görselle özelleştirilir.
- **Şablonda çözülen sorun bir daha çözülmez:** görsel/kontrast QA, box-sizing, overflow
  gibi tekrarlayan düzeltmeler şablona geri işlenirse sonraki müşteride hazır gelir.
- **İki repo da push edilmeli:** oturum sonu iş akışında `cd .../cafe && git push` ve
  `cd .../basic-template && git push` ayrı adımlardır; biri unutulursa şablon geride kalır.
- **"Üretmeden sat" hızını bu ayrım sağlar:** demo aşamasının hızlı ve düşük maliyetli
  olması, hazır bir şablondan başlamaya bağlıdır.
- **Geçici çalışma dizinleri kalıcı repo değildir:** `/tmp/...` altında geliştirme yapılıyorsa
  push edilmeyen değişiklikler kaybolur; commit/push disiplini kritiktir (bu oturumda 9 commit).

## Detaylar

Şablon reposu, "üretmeden sat" hunisindeki açık teknik başlıklardan biri olan "şablon
altyapısı" sorusunun somut cevabıdır. Şablon güncellendikçe (yeni bölüm tipi, yeni QA
kuralı, yeni cihaz düzeltmesi) her yeni müşteri demosu daha az elle müdahale gerektirir.
Buna karşılık müşteriye özel deneyler (renk, görsel, metin) müşteri reposunda kalmalı,
şablona sızmamalıdır; aksi halde şablon bir müşterinin kimliğine bağlanır. Şablona geri
işlenecek şeyler yalnızca genellenebilir teknik iyileştirmelerdir.

## İlgili Kavramlar

- [[uretmeden-sat-web-tasarim-satis-hunisi]] — Bu iki-repo ayrımı, huninin "şablon
  altyapısı" açık başlığını çözer ve demo adımının hızlı/ucuz olmasını mümkün kılar.
- [[yapay-zeka-skill-template-sistemi]] — Şablon reposu koddaki tekrarı, skill sistemi ise
  iş adımlarındaki tekrarı azaltır; ikisi aynı "bir kez çöz, tekrar kullan" ilkesinin
  farklı katmanlarıdır.
- [[github-pages-ile-statik-site-yayinlama]] — Müşteri reposu QA sonrası bu tür statik
  yayın servisinde canlıya alınıp demo linki olarak paylaşılır.

## Kaynaklar

- 2026-08-29.md
