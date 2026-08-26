---
title: Excel Otomatik Hesaplama Tablosu
aliases: [excel formül tablosu, kümülatif stok takibi, excel kalan hesaplama]
tags: [excel, formül, stok-takibi, veri-girisi]
sources: [import-2026-04-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# Excel Otomatik Hesaplama Tablosu

Excel Otomatik Hesaplama Tablosu, kullanıcının yalnızca belirli hücrelere veri
girdiği, geri kalan sütunların ve toplam satırının formüllerle otomatik
hesaplandığı bir tablo tasarım desenidir. Renk kodlaması (sarı: veri girişi,
mavi: otomatik hesaplanan, yeşil: toplam) hangi hücrelerin elle doldurulacağını
görsel olarak ayırt eder. Kümülatif stok takibi gibi ay bazlı biriken
değerlerin izlenmesi için formüller bir önceki satıra referans verir.

## Önemli Noktalar

- Sarı hücreler elle veri girişi içindir (ör. Red Ürün ve Rejenere Edilen
  sütunları); mavi hücreler formülle otomatik hesaplanır (ör. `=B-C`).
- Toplam satırı `=SUM(...)` formülleriyle tüm sütunları otomatik toplar ve
  genelde yeşil arka planla vurgulanır.
- Kümülatif stok takibi için formül bir önceki ayın kalanını taşır:
  `Şubat = Ocak'ın kalanı + Şubat'ın red ürünü - Şubat'ın rejenere edileni`
  (ör. `=D5+B6-C6`), yani her ay bir öncekine referans verir.
- Boş bırakılan aylarda formülün hata vermemesi için `""` (boş metin) kontrolü
  eklenir.
- Ürün bazlı detay gerektiğinde (aynı ay içinde birden fazla ürün red/rejenere
  edilebiliyorsa) tek sütun yeterli olmaz; ayrı bir detay sayfası veya
  ürün başına ayrı sayfa + SUMIF ile toplama yapısı önerilir.

## Detaylar

Örnek senaryo bir "Red Ürün / Rejenere Edilen / Kalan" stok takip tablosudur.
Başlangıçta Kalan sütunu basitçe `=B-C` (o ayın red ürünü eksi rejenere edileni)
olarak tasarlanmış, ardından kullanıcı ihtiyacını netleştirince kümülatif hale
getirilmiştir: her ayın kalanı, bir önceki ayın kalan stoğuna o ayın red ürünü
eklenip rejenere edilen düşülerek hesaplanır. Ürün bazlı takip ihtiyacı ortaya
çıktığında (hangi ürünün rejenere edildiğinin bilinmesi gerektiği için) tek
sütunlu yapı yetersiz kalmış; çözüm olarak ayrı bir detay sayfasında
Ay/Ürün Adı/Red Ürün/Rejenere Edilen kayıtları tutulup ana tabloya SUMIF ile
aktarılması ya da her ürün için ayrı sayfa açılıp bir TOPLAM sayfasında
birleştirilmesi seçenekleri değerlendirilmiştir.

## İlgili Kavramlar

- [[excel-grafik-olusturma]] — bu tablodaki veri aralığı (başlık satırı dahil)
  doğrudan bir sütun grafiğin veri kaynağı olarak kullanılır.

## Kaynaklar

- import-2026-04-part-001.md
