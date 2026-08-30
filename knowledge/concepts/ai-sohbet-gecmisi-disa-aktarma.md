---
title: AI Sohbet Geçmişini Dışa Aktarma (Claude, ChatGPT, Gemini)
aliases: [export data, veri dışa aktarma, conversations.json, chat.html, Google Takeout Gemini, geçmiş import, sohbet yedeği alma]
tags: [yapay-zeka, veri-yonetimi, gizlilik, yedekleme, claude-code]
sources: [import-2026-08-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# AI Sohbet Geçmişini Dışa Aktarma (Claude, ChatGPT, Gemini)

Üç büyük yapay zeka sohbet platformundan eski konuşmaları indirmenin (export) yolları. Bu veri hem kişisel yedek hem de ikinci beyin sistemine `geçmiş import` ile aktarım için gerekir; import işlemi tamamen yerel çalışır, hiçbir yere yüklenmez.

## Önemli Noktalar

- **Claude.ai:** sol alttaki isim baş harfleri → Settings → Privacy → "Export data". İşlem bitince hesaba kayıtlı e-postaya indirme linki gelir; link teslimattan 24 saat sonra dolar, dolarsa export tekrar tetiklenip yeni link istenir.
- **ChatGPT:** profil ikonu → Settings → Data Controls → Export Data → Confirm Export. Birkaç dakika içinde e-postaya zip linki gelir; zip içinde `conversations.json` (ham veri) ve `chat.html` (tarayıcıda okunabilir hali) bulunur.
- **Gemini:** ayrı "export" düğmesi yoktur; `takeout.google.com` (Google Takeout) üzerinden "Gemini Apps Activity" (eski adıyla "Bard") verisi seçilip indirilir.
- **Ortak desen:** her üçünde de export asenkrondur — talep edilir, hazırlanınca e-posta ile indirme linki gönderilir.
- **beyin.md bağlantısı:** vault kurulduktan sonra Claude Code'a `geçmiş import` yazıp indirilen zip/json yolunu vermek yeterlidir; ChatGPT/Claude/Gemini dışa aktarımını yerel olarak günlük loglara çevirir.

## Detaylar

Gizlilik açısından üç export da kullanıcının kendi hesabından, kendi e-postasına teslim edilir; üçüncü tarafa aktarım yoktur. `geçmiş import` skill'i bu dosyaları alıp `daily/` altındaki günlük log formatına dönüştürür, böylece `compile.py` sonradan bunları kalıcı kavram makalelerine derleyebilir — yani geçmiş sohbetler de ikinci beyin bilgi tabanına dahil olur. Bu skill degraded modda (GitHub script'leri olmadan) mevcut değildir.

## İlgili Kavramlar

- [[ikinci-beyin-hafiza-sistemi]] — Dışa aktarılan sohbetler `geçmiş import` ile bu sistemin günlük loglarına beslenir ve derleyici tarafından bilgi tabanına dahil edilir.
- [[beyin-sistemi-degraded-mod-kurulumu]] — `geçmiş import` skill'i repodan geldiği için degraded modda kaybolur; export dosyaları elde edilse bile otomatik dönüştürme yapılamaz.

## Kaynaklar

- import-2026-08-part-002.md
