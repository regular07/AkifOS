---
title: İkinci Beyin Sisteminin Degraded Mod / Offline Kurulumu
aliases: [degraded mode, FAST PATH fallback, GitHub script'leri olmadan kurulum, PHASE 0 fallback, repoyu elle indirip verme, network kısıtlaması aşma]
tags: [yapay-zeka, kisisel-sistem, kurulum, guvenlik, claude-code]
sources: [import-2026-08-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# İkinci Beyin Sisteminin Degraded Mod / Offline Kurulumu

İkinci beyin kurulum tarifinin (`SETUP.md`), GitHub'a hiç erişmeden çalıştırılan senaryosu. "FAST PATH" adımı (`git clone`) başarısız olur ya da atlanırsa dosya kendiliğinden "PHASE 0'dan fallback" + "degraded mode" moduna geçer; ekstra bir şey icat etmeye gerek yoktur, bu davranış tarifin içinde tanımlıdır. Üç hook script'i (`session-start.sh`, `prompt-counter.sh`, `session-end.sh`) ve `settings.json` dosyanın içinde tam metin gömülü olduğundan `curl` olmadan doğrudan diske kopyalanır.

## Önemli Noktalar

- **Kaybedilenler = repodan gelen parçalar:** `flush.py` (otomatik günlük log yok), `compile.py` (`knowledge/` klasörü hiç dolmaz), `pre-compact.sh` hook'u, `beyin-doktor` ve `geçmiş-import` skill'leri.
- **Korunanlar:** klasör iskeleti, `CLAUDE.md` yönlendirici dosyası, `🔮 850-Companion` hafıza dosyaları (Core.md, Last-Session.md, Threads.md, Kurallar.md), çalışan `session-start.sh` (önceki oturum bağlamını enjekte eder) ve `session-end.sh` (yalnızca "hafızayı güncellemeyi unutma" hatırlatıcısı bırakır).
- **Pratik sonuç:** hafıza güncelleme yeniden kullanıcının/oturum içi elle işin sorumluluğuna kalır; sistem işlevsel olarak v1'e ("hafıza bir mekanizma değil, bir disiplin") geri döner.
- **Orta yol:** script'leri körü körüne `curl`'lemek yerine önce `flush.py`/`compile.py` içeriğini GitHub'da okuyup güvenip güvenmediğine karar ver; güvenliyse FAST PATH ile kur.
- **En temiz çözüm — repoyu elle indirme:** `avenoxai/avenoxbeyin` deposunu tarayıcıdan "Download ZIP" veya Claude Code dışında `git clone` ile indir, lokal klasör olarak Claude Code'a ver ("bu klasördeki SETUP.md'yi uygula, GitHub'dan hiçbir şey indirme"). Network kısıtlaması tamamen aşılır ve sistem "tam" (v1'e düşmeyen) haliyle kurulur.

## Detaylar

Repoyu elle vermek yalnızca "GitHub'dan indirme" adımını çözer: FAST PATH'teki `git clone` ve PHASE 4'teki tek tek `curl` komutları gereksiz kalır, Claude Code dosyaları `raw.githubusercontent.com` yerine indirilmiş `template/.claude/` klasöründen kopyalar. Homebrew/Obsidian kurulumu (PHASE 1) veya mem0 API anahtarı alma (PHASE 8, `mem0.ai`) farklı domainlerdir; network kısıtlaması onları da etkiliyorsa ayrıca elle çözmek gerekir. Manuel indirilen repo sonradan otomatik güncellenmez; yükseltme gerekince tekrar elle indirilir.

Güvenlik avantajı: dosyalar zaten diskte olduğu için `template/.claude/hooks/*.sh` ve `template/.claude/scripts/*.py` içerikleri açılıp okunabilir — üçüncü taraf koda körü körüne güvenmek yerine ne yaptığı görülerek karar verilir.

## İlgili Kavramlar

- [[ikinci-beyin-hafiza-sistemi]] — Bu, o sistemin GitHub erişimi olmayan ya da üçüncü taraf koda güvenmek istemeyen kullanıcı için tasarlanmış kurulum varyantıdır; degraded modda sistemin otomasyon çekirdeği eksilir.
- [[github-pages-ile-statik-site-yayinlama]] — Her ikisinde de bir GitHub deposunun içeriğini yerel olarak elde edip kullanma pratiği vardır; burada repo kod kaynağı, orada yayın hedefidir.
- [[derle-komutu-manuel-bilgi-derleme]] — Her ikisinde de `compile.py` derleme katmanı devre dışıdır (burada hiç kurulmamış, orada API'siz çalışamıyor) ve derleme oturum içi manuel bir işleme devredilir.

## Kaynaklar

- import-2026-08-part-002.md
