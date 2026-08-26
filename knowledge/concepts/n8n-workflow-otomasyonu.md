---
title: n8n Workflow Otomasyonu
aliases: [n8n, n8n workflow]
tags: [otomasyon, workflow, n8n]
sources: [import-2025-07-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# n8n Workflow Otomasyonu

n8n, node tabanlı görsel bir arayüzle iş akışları (workflow) kurmayı sağlayan
bir otomasyon platformudur. Her workflow, birbirine bağlı node'lardan oluşur;
her node bir tetikleyici (ör. cron zamanlayıcı), bir veri işleme adımı veya bir
dış servis çağrısı temsil eder. Workflow'lar JSON formatında saklanır ve elle
düzenlenebilir.

## Önemli Noktalar

- Her node'un workflow içinde benzersiz bir ID'si olmalı; eski/eksik ID'ler
  modern n8n sürümleriyle uyumsuzluğa yol açabilir.
- Zamanlama için Cron node yapısı n8n sürümleri arasında değişebilir, güncel
  formata taşınmalı.
- IF node'ları yeni koşul yapısını kullanacak şekilde modernize edilmeli.
- Dış servislerden (ör. AI modeli) gelen yanıtlar parse edilirken hata
  yönetimi eklenmeli; parse başarısız olursa varsayılan bir değere düşülmeli.
- Orijinal mesaj/mail metadata'sı workflow boyunca korunmalı ki sonraki
  node'lar bu bilgiye erişebilsin.

## Detaylar

Örnek bir kullanım senaryosunda: Gmail IMAP üzerinden gelen mailler
tetikleyici olarak kullanılıyor, içerik OpenAI API'ye gönderilip
özetleniyor/sınıflandırılıyor, ardından sonuç bir Telegram Bot mesajı olarak
kullanıcıya iletiliyor. Bu tür workflow'larda credential'lar (Gmail IMAP,
OpenAI API key, Telegram Bot token) ayrı ayrı yapılandırılmalı ve chat ID gibi
alıcıya özel değerler placeholder yerine gerçek değerlerle değiştirilmeli.

## İlgili Kavramlar

- [[openai-api-entegrasyonu]] — n8n workflow'larında AI destekli işleme adımı
  olarak OpenAI API çağrıları kullanılıyor.
- [[telegram-bot-entegrasyonu]] — işlenen sonuçlar Telegram Bot üzerinden
  kullanıcıya bildirim olarak gönderiliyor.

## Kaynaklar

- import-2025-07-part-001.md
