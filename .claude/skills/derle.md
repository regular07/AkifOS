---
name: derle
description: Günlük logları kalıcı kavram makalelerine derle (manuel bilgi derleme)
---

# /derle — Manuel Bilgi Derleme

`compile.py` otomasyonu (gecelik derleme) ücretli API anahtarı eksikliğinden çalışmadığında, kullanıcının tetiklediği bu komutu çalıştırarak günlük logları kalıcı kavram makalelerine işler.

## Kullanım

```
/derle
```

Şunları yapar:
1. `daily/YYYY-MM-DD.md` dosyalarında yeni günlükleri tarar
2. Kalıcı değeri olan konuları tespit edip `knowledge/concepts/` altına kavram makalesi oluşturur
3. Mevcut makaleleri günceller (çelişkili kopyalar yerine merge)
4. `knowledge/index.md` ve `knowledge/log.md` dosyalarını güncelleştir
5. Bağlantı dosyaları (`knowledge/connections/`) oluşturur

## Örnek

Sabah `/derle` çalıştırıldıktan sonra:

```
Derleme yapıldı:
- Yeni kavramlar: web-demo-gorsel-secimi-ve-metin-kontrasti (2026-08-29.md'den)
- Güncellenen: uretmeden-sat-web-tasarim-satis-hunisi
- Bağlantılar: 1 dosya oluşturuldu
```

## Kalite Ayarı

Manuel derleme için model Sonnet'e yükseltilir ve effort "high" seçilir (kalite kritik, otomatik yedek yok).

## İlgili Kavramlar

- [[derle-komutu-manuel-bilgi-derleme]] — Bu komutun sistem içindeki yeri ve neden gerekli olduğu
- [[ikinci-beyin-hafiza-sistemi]] — Derleme, bu sistemin özü
