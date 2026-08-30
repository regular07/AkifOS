---
title: /derle Komutu ile Manuel Bilgi Derleme
aliases: [derle komutu, manuel compile, /derle, compile.py yerine manuel derleme, API'siz bilgi derleme]
tags: [yapay-zeka, kisisel-sistem, bilgi-yonetimi, obsidian, claude-code, otomasyon]
sources: [2026-08-28.md]
created: 2026-08-28
updated: 2026-08-28
---

# /derle Komutu ile Manuel Bilgi Derleme

İkinci beyin sisteminin gecelik `compile.py` otomasyonu ücretli bir API anahtarı gerektirdiğinde ve bu anahtar yoksa devreye alınan, kullanıcının komutla tetiklediği manuel derleme yöntemidir. Kullanıcı `/derle` yazdığında model, günlük loglardaki oturum özetlerini okuyup kalıcı değeri olan kavramları `knowledge/` altındaki bağlantılı makalelere işler. Böylece otomatik zamanlayıcı çalışmasa bile bilgi tabanı elle ama düzenli biçimde büyümeye devam eder.

## Önemli Noktalar

- **Tetikleyici sorun:** `compile.py` 25 saattir `claude-exit-1` ile başarısızdı; kök neden derleyicinin ayrı ücretli API anahtarı istemesi, kullanıcının ise ücret nedeniyle API kullanmama kararıydı.
- **Karar:** API kurmak yerine `/derle` komutu tanımlandı; derleme artık zamanlanmış görev değil, kullanıcının istediği anda başlattığı bir işlem.
- **Bölünme:** `flush.py` (oturum → günlük log) ve companion hafıza dosyalarının (Last-Session.md, Threads.md, Kurallar.md) otomatik güncellenmesi bozulmadan sürer; yalnızca günlük log → kavram makalesi adımı manuele döner.
- **Kalite ayarı:** manuel derleme için model Sonnet'e yükseltildi ve effort "high" seçildi, çünkü tek seferlik toplu iş kalitesi önemli.
- **Risk:** derleme artık kullanıcı disiplinine bağlı; `/derle` çağrılmazsa günlük loglar birikir ve bilgi tabanı güncelliğini yitirir.

## Detaylar

Bu yaklaşım, ikinci beyin sisteminin "hafıza bir mekanizma olmalı, disiplin değil" ilkesinden kısmi bir taviz olarak görülebilir: `flush.py` mekanizması korunduğu için ham konuşma kaydı hâlâ otomatik tutulur, fakat kavramsallaştırma katmanı yeniden insan tetiğine bağlanır. Pratikte bu, degraded mod kurulumundan farklıdır; degraded modda `compile.py` script'i hiç kurulmamışken, burada script mevcut ama API erişimi olmadığı için çalıştırılamıyor ve yerini oturum içi manuel bir derleme protokolü alıyor.

Manuel derleme oturumunda izlenen akış, otomatik derleyicinin mantığını taklit eder: yalnızca aday makaleleri Grep/Read ile incele, indeksi tek bağlam olarak kullan, her günlükten 2-6 kavram çıkar, çelişkili kopya yerine mevcut makaleyi güncelle, `index.md` ve `log.md` dosyalarını güncelle.

## İlgili Kavramlar

- [[ikinci-beyin-hafiza-sistemi]] — Bu komut, o sistemin `compile.py` otomasyon katmanının API erişimi olmadan çalışamadığı durumda onun yerine geçen elle çalıştırılan alternatiftir.
- [[beyin-sistemi-degraded-mod-kurulumu]] — Her ikisi de `compile.py` devre dışıyken bilgi tabanını canlı tutma sorununu ele alır; degraded modda script hiç yokken burada script var ama API'siz çalıştırılamıyor.
- [[ai-sohbet-gecmisi-disa-aktarma]] — Dışa aktarılıp içe alınan eski sohbetler de sonuçta bu manuel derleme adımından geçerek kavram makalelerine dönüşür.

## Kaynaklar

- 2026-08-28.md
