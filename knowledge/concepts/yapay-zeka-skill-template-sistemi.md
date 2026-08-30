---
title: Yapay Zeka ile Skill Template Sistemi ve Operasyonal Komutlar
aliases: [skill sistemi, template komutlar, /derle, /mobile-menu-fix, /hero-mobile-gap-fix, /text-contrast-qa, /qp02-lookup, /standart-sorgu, /recete-olcekle, skill'leştirme]
tags: [yapay-zeka, skill, otomasyon, template, vault-sistemi, operasyon]
sources: [2026-08-30.md]
created: 2026-08-30
updated: 2026-08-30
---

# Yapay Zeka ile Skill Template Sistemi ve Operasyonal Komutlar

Vault'ta yapılan her işin ardından o işi tekrar edebilecek bir `/komut` template'i oluşturarak
benzer işleri otomatik hale getirme stratejisi. Amaç: kalıcı hafıza + yapay zeka = yeniden keşif
değil, şablon ile hızlı çalıştırma.

## Önemli Noktalar

- **Skill = executable template:** Her yapılan iş bir `/skill` komutu haline gelir. Örn:
  `/derle` (daily loglardan kavram çıkarma), `/mobile-menu-fix` (mobil menü düzeltme),
  `/hero-mobile-gap-fix` (hero bölümü responsive gap), `/text-contrast-qa` (metin kontrastı QA),
  `/qp02-lookup` (SAP QP02 sorgusu), `/standart-sorgu` (TS EN standart bilgi), `/recete-olcekle`
  (reçete ölçekleme).

- **Amaç: yeniden keşfi azaltmak:** ilk defa bir sorunu çözerken ayrıntı önemli, dokümante
  edildikten sonra aynı sorunla karşılaştığında template'ten çalıştırılır — zaman kayıp olmaz,
  kalite tutarlı kalır.

- **6 skill hedefi (2026-08-30):**
  - `/mobile-menu-fix` — mobil menü geçişi/responsive görev
  - `/hero-mobile-gap-fix` — hero bölümü Redmi Note gibi cihazlarda gap sorunu
  - `/text-contrast-qa` — arka plan üzerine metin kontrolü (kontrastı)
  - `/qp02-lookup` — SAP QP02 kalite kontrol karakteristik sorgusu
  - `/standart-sorgu` — TS EN standart bilgi ve test referansı (doğruluk garantili)
  - `/recete-olcekle` — laboratuvar reçetesi → fabrika ölçeğine oranlama

- **Teknik altyapı:** `.claude/skills/` klasörü altında `.md` ya da `.sh` formatlı dosyalar;
  kullanıcı skill adını yazınca Claude Code otomatik template'i yükler.

## Detaylar

Vault'un amacı "kalıcı hafıza" olmak. Ama hafıza kullanılmazsa "tozlanmış kütüphane" haline gelir.
Bu stratejide her derlenmiş kavram bir skill'e dönüştürülerek hafızanın aktif kul... edilmesi sağlanır.
Örneğin "text-contrast-qa" ilk defa kahve sitesi demosunda bulunmamış, şimdi skill olunca Müşteri-B,
Müşteri-C sitesi QA'larında otomatik uygulanır.

Skill template'inin yapısı basit olmalı: (1) Görev tanımı, (2) Ön koşullar, (3) Adımlar, (4) Çıktı.
Açık başlıklar: skill'ler henüz yazılmamış (planlama aşaması); 6 skill'in öncelik sırası ve
`.claude/skills/` klasör yapısı netleştirilecek.

## İlgili Kavramlar

- [[derle-komutu-manuel-bilgi-derleme]] — Skill sistemi içinde `/derle` ilk operasyonal komut;
  daily loglardan kavramlar çıkartıp knowledge base'e işleme template'i.
- [[ts-en-standart-sorgu-doğruluk-garantisi]] — `/standart-sorgu` skill'i, standartlara yönelik
  sorulara "yanlış cevap yasak" kuralıyla cevap veren template.
- [[recete-olceklendirme-ve-fabrika-entegrasyonu]] — `/recete-olcekle` skill'inin detaylı
  referans dokümanı (lab → fabrika ölçeklendirme adımları).
- [[web-demo-gorsel-secimi-ve-metin-kontrasti]] — `/text-contrast-qa` skill'inin ilk bulgusu
  (kahve sitesi demosunda ortaya çıkan kontrast sorunu).

## Kaynaklar

- 2026-08-30.md (Skill'leştirme stratejisi, 6 skill hedefi)
- `.claude/skills/` (henüz oluşturulmamış)
