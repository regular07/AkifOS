---
title: Telegram Bot Entegrasyonu
aliases: [Telegram Bot, Telegram entegrasyonu]
tags: [telegram, bot, entegrasyon]
sources: [import-2025-07-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# Telegram Bot Entegrasyonu

Bir workflow'un sonucunu kullanıcıya bildirmek için Telegram Bot API
kullanılabilir. Bot token ve hedef chat ID doğru yapılandırıldığında,
işlenmiş veriler Markdown formatlı mesajlar olarak kullanıcıya iletilir.

## Önemli Noktalar

- Mesajın gönderileceği chat ID placeholder değil, gerçek chat ID ile
  değiştirilmeli.
- Bot token credential olarak ayrı saklanmalı.
- Markdown formatlama kullanılarak mesajlar daha okunaklı hale getirilebilir.
- Mesaj içeriğine orijinal kaynağa ait metadata (ör. mail bilgisi) eklenerek
  bağlam korunabilir.

## Detaylar

Telegram Bot entegrasyonu genelde bir workflow'un son adımı olarak kullanılır:
önceki node'larda işlenen veri (ör. bir AI modelinin özetlediği içerik)
Markdown formatında biçimlendirilip Telegram mesajı olarak gönderilir. Bu
sayede kullanıcı, otomasyonun sonucunu anlık olarak takip edebilir.

## İlgili Kavramlar

- [[n8n-workflow-otomasyonu]] — Telegram Bot node'u n8n workflow'unun bildirim
  adımı olarak kullanılıyor.
- [[openai-api-entegrasyonu]] — Telegram'a gönderilen mesajın içeriği OpenAI
  API'den gelen işlenmiş sonuçtan oluşuyor.

## Kaynaklar

- import-2025-07-part-001.md
