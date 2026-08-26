---
connects: [n8n-workflow-otomasyonu, telegram-bot-entegrasyonu]
sources: [import-2025-07-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

## Bağlantı

n8n workflow'ları, işlenen verinin sonucunu kullanıcıya iletmek için son adımda
Telegram Bot node'unu kullanır.

## Ana Fikir

Telegram Bot entegrasyonu, n8n workflow'unun bildirim katmanıdır: önceki
node'larda (ör. OpenAI ile) işlenen veri, Markdown formatlı bir mesaj olarak
belirlenen chat ID'ye gönderilir.

## Kaynaklar

- import-2025-07-part-001.md
