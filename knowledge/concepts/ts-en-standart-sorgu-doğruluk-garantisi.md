---
title: TS EN Standart Sorgusu ve Doğruluk Garantisi
aliases: [standart sorgu, doğruluk kuralı, TS EN PDF koleksiyonu, standart-sorgu skill, 102 PDF, 5 markdown özeti, yanlış cevap yasak]
tags: [standart, yapı-kimyasalları, kalite-kontrol, skill, doğruluk, yapay-zeka]
sources: [2026-08-30.md]
created: 2026-08-30
updated: 2026-08-30
---

# TS EN Standart Sorgusu ve Doğruluk Garantisi

Yapı kimyasalları kalite kontrol işinin temelini oluşturan TS EN standartlarına (EN 12004/998-1
/13687/13566/13888/1015 ve türevleri) yönelik sorulara cevap verme tekniği. Kural basit ama kesin:
**yanlış cevap absolut yasak**; doğru olandan emin değilse "bilmiyorum, referans al" cevabı.

## Önemli Noktalar

- **Koleksiyon:** 102 PDF standart + 5 markdown özeti (OneDrive: `~/Library/CloudStorage/OneDrive-Kişisel/Yapıkim. Standartlar/standartlar özetleri/standart pdf`)
  - Merkezi depo, PDF'ler sınıflandırılmış (EN 12004, EN 1015, EN 998, EN 13566, EN 13687, EN 13888, EN 1346, EN 13820, EN 14411, vb.)
  - 5 markdown özeti: temel standartların önemli maddeleri, test yöntemleri, sınıflandırma tabloları

- **Doğruluk kuralı:** Yapay zeka'nın bu alandaki riski, eğitim setindeki hatalı/eski bilgiyi
  güvenle sunması. Örneğin EN 12004'ün revision'u değişti, eski C2S sınıfı güncellendi, CE AVCP
  yapısı zaman zaman revize oldu. Yanlış bilgi → müşteri ürün kabul etmiyor → fabrika durdurma
  → mali zarar. **Kaynağı referans alınmadıkça asla kesin cevap verilmeyecek.**

- **Skill tasarımı:** `/standart-sorgu` komutu, soruda hangi standart ve hangi madde olduğu net ise
  PDF'den ya da markdown'dan çıkarılan bilgiyi sunar; eğer belirsizse ("EN 12004'te yapışma mi
  varsa kaç saat?") — önce sınıflandırmayı (hangi EN?) ve bağlamı (ürün tipi, test adı) sorar.

- **Açık başlık:** Markdown özetleri (.xlsx'ten ve hafızadan) ne kadar güncel? EN standardları 3-5
  yılda revision alıyor; koleksiyon periyodik kontrol/güncelleme gerekliyor.

## Detaylar

Vault'ta daha önce (`yapi-kimyasallari-urun-standartlari` makalesinde) standartlar hakkında
bilgi toplandı: EN 12004-1/2, EN 998-1, EN 1015-1/2/3/... CE-TSE yapısı, test codes (kayma,
flexural strength, adhesion, vb.). Şimdi bu bilgi "sorgulanabilir hale getirme" adımı atılıyor:
102 PDF'yi kategorize et, başlıca maddeleri markdown'a çıkart, `/standart-sorgu` skill'inde
("yanlış cevap yasak") sistem olarak düzenle.

Ön koşul: markdown özetleri tamamlanacak (bkz. yapılacaklar). Sonrasında `/standart-sorgu`
kullanıldığında arama yüksek kaliteli, referanslı ve güvenli olur.

## İlgili Kavramlar

- [[yapi-kimyasallari-urun-standartlari]] — Vault'ta derlenmiş TS EN standartları hakkındaki
  detaylı makale (sınıflandırma, test yöntemleri, CE-AVCP, revision tarihleri).
- [[yapay-zeka-skill-template-sistemi]] — `/standart-sorgu` bu sistemin 6 skill'inden biri;
  doğruluk garantili yapay zeka şablonu.
- [[hammadde-sap-kalite-kontrol-formati]] — TS EN standardlarında tanımlanan test parametreleri
  SAP QP02'de kodlanır (örn: EN 12004 adhesion → QP02'de ADHE karakteristik).
- [[ty-ak-test-standart-kod-referansi]] — Fabrika içi TY.AK test yöntemlerinin TS EN standart
  karşılıkları (örn: TY.AK.160 viskozite = EN 1346).

## Kaynaklar

- 2026-08-30.md ("standart sorgu skill'i kuralı: yanlış cevap absolut yasak")
- OneDrive: `~/Library/CloudStorage/OneDrive-Kişisel/Yapıkim. Standartlar/standartlar özetleri/standart pdf` (102 PDF + 5 markdown)
- 2026-08-26.md, 2026-08-28.md (eski standart sorguları)
