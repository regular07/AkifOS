---
title: İkinci Beyin Kalıcı Hafıza Sistemi (Obsidian + Claude Code)
aliases: [second brain, beyin.md, avenoxbeyin, kalıcı AI hafızası, companion memory, flush.py compile.py, memory must be a mechanism not a discipline]
tags: [yapay-zeka, kisisel-sistem, bilgi-yonetimi, otomasyon, obsidian, claude-code]
sources: [import-2026-08-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# İkinci Beyin Kalıcı Hafıza Sistemi (Obsidian + Claude Code)

Obsidian not uygulamasını Claude Code ile birleştirip, yapay zeka oturumlarının kendini otomatik hatırladığı kalıcı bir "ikinci beyin" kuran kurulum tarifi (`SETUP.md`, `avenoxai/avenoxbeyin` deposu). Normal bir AI sohbeti her oturumda kullanıcıyı unutur; bu sistem konuşmaları özetleyip günlük loglara, oradan da birbirine bağlı bilgi makalelerine dönüştürerek ertesi oturumda bağlama (context) otomatik yükler. Tasarım ilkesi açıkça şudur: "memory must be a mechanism, not a discipline" — hafıza kullanıcının disiplinine değil, çalışan bir mekanizmaya dayanmalı.

## Önemli Noktalar

- **İki katmanlı otomasyon:** oturum bitince `flush.py` konuşmayı özetleyip `daily/2026-08-26.md` gibi bir günlük dosyaya yazar; günde bir kez `compile.py` bu günlükleri okuyup `knowledge/` altında bağlantılı kavram makalelerine derler.
- **Hook'lar:** `session-start.sh` her yeni oturumda önceki `Last-Session.md`, `Threads.md`, `Kurallar.md` içeriğini bağlama enjekte eder; `session-end.sh` hafıza güncellenmeden biten oturum için bir işaretçi bırakıp sonraki açılışta hatırlatır; `prompt-counter.sh` ve `pre-compact.sh` diğer hook'lardır.
- **Companion (ortak) hafızası:** `🔮 850-Companion` klasöründe Core.md (kim olduğu), Kurallar.md (kullanıcının düzeltmeleri buraya not düşülür), Last-Session.md, Threads.md dosyaları tutulur.
- **API anahtarı gerektirmez:** temel sistem mevcut Claude aboneliğini kullanır; mem0 adlı anlamsal arama katmanı tamamen opsiyoneldir (ücretsiz API anahtarı ister).
- **v1 → v2 farkı:** v1 hafızayı elle güncellemeye (disiplin) dayanıyordu ve başarısız oluyordu; v2'nin tüm değeri `flush.py` + `compile.py` otomasyonundadır. Kurulum var olan v1'i bozmadan yükseltir, dosya üzerine sessizce yazmaz.

## Detaylar

Kurulum önce kullanıcıya sorular sorar (isim, meslek, AI ortağının adı, opsiyonel klasörler: hedefler/para/sağlık/zihin, mem0 istenip istenmediği), sonra klasör iskeleti (emoji'li gelen kutusu, projeler, bilgi tabanı, companion), otomasyon parçaları, başlangıç hafıza dosyaları ve isteğe bağlı masaüstü uygulama ikonu (🧠) oluşturur. Vault yerel bir git deposuna çevrilir (uzak sunucuya gönderilmez) ki hatalı düzenlemeler geri alınabilsin. Son adım bir doğrulama raporudur.

Sınırlamalar: sistem Claude Code'un diske gerçek dosya yazmasını ve `avenoxai/avenoxbeyin` deposundan script indirmesini gerektirir — üçüncü taraf koda güven gerekir. Şu an yalnızca macOS'ta test edilmiştir; Linux yolu yazılmış ama gerçek bir Linux masaüstünde doğrulanmamıştır. `geçmiş import` ve `beyin-doktor` ek skill'lerdir (eski sohbetleri içe aktarma ve arıza teşhisi).

## İlgili Kavramlar

- [[beyin-sistemi-degraded-mod-kurulumu]] — GitHub script'leri olmadan kurulduğunda bu sistemin otomasyon çekirdeği (`flush.py`/`compile.py`) devre dışı kalır ve sistem işlevsel olarak v1'e geri döner.
- [[ai-sohbet-gecmisi-disa-aktarma]] — `geçmiş import` özelliği, dışa aktarılmış Claude/ChatGPT/Gemini sohbetlerini bu sistemin günlük loglarına çevirerek hafıza tabanını geçmiş veriyle doldurur.
- [[adhd-yapay-zeka-destekli-gorev-yonetimi]] — Her ikisi de bilişsel yükü (hatırlama, öncelik, karar) kullanıcıdan alıp yapay zeka destekli bir dış sisteme devretme fikrini paylaşır.
- [[inbox-dump-hizli-gorev-yakalama]] — Kurulumun oluşturduğu `📥 000-Inbox` klasörü, kullanıcının aklına geleni sürtünmesiz yakaladığı insan tarafındaki giriş noktasıdır.
- [[derle-komutu-manuel-bilgi-derleme]] — `compile.py` ücretli API anahtarı olmadan çalışmayınca bu sistemin gecelik derleme adımı, kullanıcının tetiklediği `/derle` komutuyla elle yürütülür.

## Kaynaklar

- import-2026-08-part-002.md
