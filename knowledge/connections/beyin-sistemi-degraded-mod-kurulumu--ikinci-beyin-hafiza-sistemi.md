---
connects: [beyin-sistemi-degraded-mod-kurulumu, ikinci-beyin-hafiza-sistemi]
sources: [import-2026-08-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

## Bağlantı

İkinci beyin sisteminin bütün "otomatik hatırlama" vaadi iki Python script'ine (`flush.py` özetleme, `compile.py` derleme) dayanır ve bu ikisi yalnızca `avenoxai/avenoxbeyin` deposundan gelir. Degraded mod kurulumu GitHub'a hiç dokunmadan çalıştığı için bu çekirdek eksik kalır; geriye yalnızca klasör iskeleti, companion dosyaları ve önceki oturum bağlamını enjekte eden `session-start.sh` kalır.

## Ana Fikir

Bir sistemin tasarım ilkesi ("memory must be a mechanism, not a discipline") ile fiili kurulum biçimi ayrılabilir: degraded modda mekanizma düşer, disiplin geri gelir ve sistem işlevsel olarak v1'e döner. Bu yüzden orta yol — repoyu elle indirip Claude Code'a lokal klasör olarak vermek — hem network/güven kısıtlamasını aşar hem de sistemi tam haliyle çalıştırır; script içerikleri diskte okunabildiği için üçüncü taraf koda körü körüne güvenmek de gerekmez.
