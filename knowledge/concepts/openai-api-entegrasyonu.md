---
title: OpenAI API Entegrasyonu
aliases: [OpenAI API, OpenAI entegrasyonu]
tags: [openai, api, entegrasyon]
sources: [import-2025-07-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# OpenAI API Entegrasyonu

OpenAI API'yi bir otomasyon workflow'una entegre ederken doğru parametre
adlarının kullanılması ve modelden dönen yanıtın güvenilir şekilde işlenmesi
gerekir. API'den gelen serbest metin veya JSON yanıtlar, sonraki adımlarda
kullanılabilmesi için parse edilir ve hata durumlarına karşı korunur.

## Önemli Noktalar

- API çağrısı yapılırken kullanılan parametre adlarının güncel API
  sürümüyle eşleşmesi gerekir; eski parametre adları hata üretir.
- Modelden dönen yanıt JSON ise, bu yanıt ayrı bir parse adımında
  ayrıştırılmalı.
- Parse işlemi başarısız olursa akışın kırılmaması için varsayılan bir
  değere düşülmeli (hata yönetimi).
- API key gibi kimlik bilgileri credential olarak ayrı saklanmalı, workflow
  dosyasına gömülmemeli.

## Detaylar

n8n gibi platformlarda OpenAI node'u genellikle bir "Yanıt Parse" adımıyla
birlikte kullanılır: model çıktısı önce ham metin olarak alınır, ardından
JSON.parse benzeri bir adımla yapılandırılmış veriye dönüştürülür. Bu adım
başarısız olursa akışın devam edebilmesi için bir fallback/varsayılan değer
tanımlanır.

## İlgili Kavramlar

- [[n8n-workflow-otomasyonu]] — OpenAI API çağrıları n8n workflow'u içinde bir
  işleme node'u olarak kullanılıyor.
- [[telegram-bot-entegrasyonu]] — OpenAI'dan gelen işlenmiş sonuç, Telegram
  mesajı olarak kullanıcıya iletiliyor.

## Kaynaklar

- import-2025-07-part-001.md
