---
title: Multi-AI Agent Orkestrasyonu
aliases: [AI Orkestra, çoklu yapay zeka ajan sistemi, multi-agent sistem]
tags: [yapay-zeka, otomasyon, agent, orkestrasyon]
sources: [import-2026-04-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# Multi-AI Agent Orkestrasyonu

Multi-AI Agent Orkestrasyonu, birden fazla özelleşmiş yapay zeka ajanının sırayla
devreye girip birbirinin çıktısını girdi olarak kullandığı bir sistem tasarımıdır.
Amaç, tek bir büyük görevi alt görevlere bölüp her adımı o adıma özel bir ajana
devrederek daha tutarlı ve yönetilebilir bir sonuç üretmektir. Sistem bir
Anthropic API anahtarıyla çalışır ve kullanıcı yalnızca görev tanımını girer.

## Önemli Noktalar

- Dört ajan sırayla çalışır: Planlayıcı (görevi alt adımlara böler), Araştırmacı
  (bilgi üretir), Yazar (içeriğe dönüştürür), Editör (nihai çıktıyı gözden geçirir).
- Her ajanın çıktısı bir sonraki ajana girdi olarak aktarılır; bu "zincir düşünce"
  (chain of thought) tarzı bir veri akışı oluşturur.
- Kullanım için Anthropic API anahtarı (`sk-ant-api03-...`) gereklidir.
- Kullanıcı yalnızca görevini (blog yazısı, rapor, araştırma, plan vb.) tanımlar
  ve orkestrasyonu tek bir buton ile başlatır.

## Detaylar

Sistem, karmaşık bir görevi tek bir prompt ile tek seferde çözmek yerine, her
alt görevi kendi bağlamına özel bir ajana devrederek çözme mantığına dayanır.
Bu sıralı devir mekanizması, her ajanın kendi uzmanlık alanında (planlama,
araştırma, yazım, editörlük) daha odaklı çalışmasını sağlar ve nihai çıktının
kalitesini artırmayı hedefler.

## İlgili Kavramlar

- [[n8n-workflow-otomasyonu]] — n8n de benzer şekilde birden fazla node'un
  sırayla veri aktararak çalıştığı bir otomasyon zinciri kurar.
- [[openai-api-entegrasyonu]] — orkestrasyondaki her ajan, bir AI API'sine
  (burada Anthropic) çağrı yaparak kendi adımını gerçekleştirir.

## Kaynaklar

- import-2026-04-part-001.md
