---
title: Excel Grafik Oluşturma
aliases: [excel sütun grafik, excel column chart, excel veri görselleştirme]
tags: [excel, grafik, veri-gorsellestirme]
sources: [import-2026-04-part-001.md]
created: 2026-08-26
updated: 2026-08-26
---

# Excel Grafik Oluşturma

Excel Grafik Oluşturma, bir veri tablosundaki değerleri sütun/bar grafik olarak
görselleştirme sürecini kapsar. Doğru eksen yönü (Y ekseninde sayısal değerler,
X ekseninde kategoriler), veri aralığı seçimi ve seri/renk ayarları grafiğin
okunabilirliğini belirler. Kaynak tablo güncellendikçe grafik otomatik olarak
yeniden çizilir.

## Önemli Noktalar

- Grafik için veri aralığı seçilirken başlık satırı mutlaka dahil edilmelidir;
  aksi halde seriler legend'da isimsiz görünür.
- Dikey sütun grafikte Y ekseni sayısal değerleri (0, 1000, 2000...), X ekseni
  kategorileri (ör. ay isimleri) gösterir — bu, "yatay bar" ile karıştırılmamalı.
- Ekle → Grafik → Sütun Grafik → Kümelenmiş Sütun (Clustered Column) yolu
  çoklu seri (ör. Red Ürün, Rejenere Edilen, Kalan) karşılaştırması için uygundur.
- "Veri Seç" (Select Data) ile yatay eksen etiketleri (ör. ay isimleri) ayrıca
  atanabilir.
- Her seriye ayrı dolgu rengi ve eksene başlık (ör. "Ton") eklenerek grafik
  netleştirilir.

## Detaylar

Kullanıcı önce grafik yönünü yanlış anlayıp "yatay bar" (aylar solda dikey
sıralı, tonaj altta yatay) istemiş gibi yorumlanmış; netleştirme sonrası asıl
istenenin standart dikey sütun grafik (X ekseninde aylar, Y ekseninde tonaj)
olduğu ortaya çıkmıştır. Bu, grafik yönü tercihlerinin sözel tarifte
belirsizleşebildiğini ve netleştirme gerektirdiğini gösteren bir örnektir.

## İlgili Kavramlar

- [[excel-otomatik-hesaplama-tablosu]] — grafik, bu formüllü tablonun verisini
  kaynak olarak kullanır ve veri girildikçe otomatik güncellenir.

## Kaynaklar

- import-2026-04-part-001.md
