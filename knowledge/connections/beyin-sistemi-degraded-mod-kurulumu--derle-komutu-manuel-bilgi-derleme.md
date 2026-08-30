---
connects: [beyin-sistemi-degraded-mod-kurulumu, derle-komutu-manuel-bilgi-derleme]
sources: [2026-08-28.md]
created: 2026-08-28
updated: 2026-08-28
---

## Bağlantı

Her iki durumda da ikinci beyin sisteminin `compile.py` derleme katmanı çalışmaz ve bilgi tabanı kendiliğinden dolmaz. Fark, arızanın yerindedir: degraded modda script GitHub'dan hiç indirilmemiştir; `/derle` senaryosunda script diskte kuruludur ama ayrı ücretli API anahtarı olmadığı için çalıştırılamaz. Ortak çözüm, kavramsallaştırmayı bir oturum içi manuel işleme (kullanıcının tetiklediği derleme) devretmektir.

## Ana Fikir

`compile.py`'nin devre dışı kalması tek bir çözümü değil bir yelpazeyi doğurur: repoyu elle indirip tam kurulum yapmak (degraded modun orta yolu) veya derlemeyi tümüyle manuel `/derle` komutuna bağlamak. İkisi de "otomatik mekanizma yoksa disipline geri dönülür" gerçeğini paylaşır; `/derle` bu disiplini hiç değilse tek komuta indirip tekrarlanabilir kılar.
