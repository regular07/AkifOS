---
connects: [excel-otomatik-hesaplama-tablosu, excel-python-ile-iteratif-dosya-uretimi]
sources: [2026-08-28.md]
created: 2026-08-28
updated: 2026-08-28
---

## Bağlantı

Otomatik hesaplama tablosu kavramı, bir Excel sayfasının *içindeki* deseni tanımlar: renk kodlu veri girişi hücreleri, formülle hesaplanan sütunlar, `=SUM(...)` toplam satırı, kümülatif referanslar. Python ile iteratif üretim kavramı ise bu tablonun *tümünü* — sekmeleri, başlıkları, biçimi, formülleri — bir script'in oluşturmasını sağlar; ihtiyaç değiştikçe script yeniden çalıştırılıp dosya yeniden türetilir.

## Ana Fikir

Elle kurulan bir tablo deseni, kod tarafından üretildiğinde tekrarlanabilir ve evrilebilir hale gelir: yeni bir sekme veya sütun eklemek, sayfayı sıfırdan biçimlendirmek yerine script'e birkaç satır eklemeye indirgenir. Bunun bedeli, elle yapılan düzenlemelerin script tekrar çalıştığında kaybolabilmesidir; bu yüzden kalıcı yapısal değişiklikler script'e yazılmalıdır.
