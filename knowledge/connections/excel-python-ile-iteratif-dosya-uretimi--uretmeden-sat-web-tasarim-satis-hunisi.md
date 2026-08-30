---
connects: [excel-python-ile-iteratif-dosya-uretimi, uretmeden-sat-web-tasarim-satis-hunisi]
sources: [2026-08-28.md]
created: 2026-08-28
updated: 2026-08-28
---

## Bağlantı

"Üretmeden sat" hunisinin işleyen parçası bir Excel dosyasıdır: Satış Planı.xlsx, altı sekmesiyle (Özet & Strateji, Fiyatlandırma, Teklif Hesaplayıcı, Basic Paket Kapsam, Müşteri Takip, Teknik Notlar) huninin fiyatlandırmasını, tekliflerini ve müşteri takibini yürütür. Bu dosya elle biçimlendirilmek yerine Python ile üretilip vault ve OneDrive'da saklanır; huninin ihtiyaçları netleştikçe (yeni paket kademeleri, dolacak teknik başlıklar) script yeniden çalıştırılarak güncellenir.

## Ana Fikir

Bir satış süreci, üzerinde çalışıldıkça değişen bir plandır; onu yöneten aracın da aynı hızda değişebilmesi gerekir. Planlama dosyasını kod ile üretmek, satış modelinin evrimini (kapsam yazımı, kademe ekleme, hesaplayıcı güncelleme) dosyayı sıfırdan düzenlemeden takip etmeyi mümkün kılar.
