---
title: Selüloz Eter Viskozite–Dozaj Eşdeğerliği
aliases: [MHEC HPMC geçişi, selüloz eter ikamesi, viskozite sınıfı dozaj, potens oranı, TY.AK.160 dozaj yorumu, Tylose Walocel dönüşümü]
tags: [yapi-kimyasallari, formulasyon, kalite-kontrol, seluloz-eter, deney-tasarimi]
sources: [import-2026-07-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# Selüloz Eter Viskozite–Dozaj Eşdeğerliği

Bir reçetedeki selüloz eteri başka bir tip veya viskozite sınıfıyla değiştirirken "aynı kg = aynı performans" varsayımı hatalıdır. Selüloz eterlerde viskozite, konsantrasyonla kabaca c^3,5–4,5 kuvvet ilişkisiyle artar; yani küçük bir doz değişimi büyük bir viskozite (dolayısıyla su tutma / sarkma direnci) değişimi yaratır. Yüksek viskoziteli bir ürün, daha düşük viskoziteli bir muadille "eşit ağırlık" mantığıyla değiştirilirse kaybedilen potens telafi edilemez. MHEC→HPMC gibi bir geçişte ayrıca kimyasal sınıf da değiştiği için iki değişken aynı anda hareket eder.

## Önemli Noktalar

- **TY.AK.160 (selüloz eter viskozite tayini) potens farkını somut gösterir:** her viskozite sınıfı farklı konsantrasyonda test edilir — <20 mPa·s → %4,75 (25 g); 20–80 → %2,85 (15 g); 100–60.000 → %1,9 (10 g); >60.000 → %1 (5 g). 60.000'lik ürün %1, 20.000'lik ürün %1,9 konsantrasyonda ölçülür → kabaca **~1,9× potens farkı**: aynı ağırlıkta eşit etki vermezler.
- **Vaka (weber.kol Standart Gri):** eski reçetede Tylose MH 60004 P6 (4,16 kg, ≈60.000 mPa·s, MHEC) + Tylose MHF 10015 P4 (1,3 kg, ≈10.000 mPa·s, MHEC) = 5,46 kg iki uçlu karışım (biri su tutmada güçlü/kayma orta, diğeri kaymada güçlü/su tutma orta). Yeni reçete: tek Walocel MKS 20000 PF30 (HPMC) 5,98 kg — yalnızca +%9,5.
- **Kaba hedef hesabı:** 60.000'lik kısmı 20.000 sınıfına çevirmek için 4,16 × (1,9 / 1) ≈ 7,9 kg; zaten aynı potens sınıfındaki 10.000'lik kısım 1,3 kg değişmeden kalır → toplam ≈ **9,2 kg** (mevcut 5,98 kg'ın ~%54 üzeri). Yani deneme reçetesindeki Walocel muhtemelen düşük dozlanmıştır.
- **Kimyasal sınıf etkisi:** aynı dozajda MHEC genelde su tutma, viskozite kararlılığı ve dağılabilirlikte HPMC'den güçlüdür; MHEC→HPMC geçişinde eşdeğer performans için genelde biraz daha yüksek doz gerekir. Ölçüm koşulu farkı (Brookfield vs Höppler, farklı %, farklı üretici) düz sayısal viskozite karşılaştırmasını yanıltır.
- **Gradasyon endişesi yersizdir:** selüloz eterin reçetedeki payı çok küçüktür (~%0,2–0,3), kendi tane boyutu ürünün toplam PSD eğrisini anlamlı değiştirmez. Risk yalnızca kıvam/performans (su tutma, açık zaman, kayma) tarafındadır.

## Detaylar

TY.AK.160'taki konsantrasyon–viskozite tablosu bir **laboratuvar test standardizasyonudur**, doğrudan bir formülasyon/dozaj rehberi değildir; ondan türetilen ~1,9× oranı kaba bir yaklaşımdır ve saha testiyle doğrulanmalıdır. Müdüre sunumda bu "kesin doğru doz budur" değil, "test yönteminin kendi mantığı bile potens farkının göz ardı edildiğini gösteriyor, doğrulanmalı" şeklinde çerçevelenmelidir. (Not: kullanıcının bahsettiği "TY.AK.190" diye bir kod yoktur; kastedilen TY.AK.160'tır.)

Doğrulama için tek nokta yerine küçük bir deney tasarımı (DOE) önerilir: Deneme 1 = 5,98 kg (mevcut/kontrol), Deneme 2 = 7,5 kg (ara nokta), Deneme 3 = 9,2 kg (hesaplanan hedef). Üçü de aynı koşullarda — açık zaman (TY.AK.009 / EN 1346), su tutma (TY.AK.225 veya eşdeğeri) ve kayma (TY.AK.161) testleriyle — karşılaştırılır. Su/çimento oranı ve karıştırma parametresi (TY.AK.170 veya ürünün QP02 karışım oranı) sabit tutulup yalnızca selüloz eter miktarı değiştirilerek tek değişken izole edilir. Ayrıca deneme öncesi eski reçeteyle bir referans/baseline partisi verisi (PSD, viskozite, açık zaman, kayma) alınıp "öncesi/sonrası" yan yana kaydedilmelidir.

İki değişkenin (kimyasal sınıf + viskozite profili) aynı anda değişmesi, sonuç iyi ya da kötü çıksa da "hangisi sorumlu" sorusunu doğurur — bu bilinen bir kör noktadır. Bu yüzden deneme partisinde açık zaman ve kayma sonuçları ayrı ayrı ve referans partiyle birlikte kaydedilmelidir. 1 kg ürün bazına ölçeklenmiş deneme reçetelerinde selüloz eter miktarı yalnızca 2–4 g mertebesindedir; 0,01 g hassasiyetli terazi kullanılmazsa tartım hatası deneyin sonucunu domine eder.

## İlgili Kavramlar

- [[seluloz-eterler-yapi-kimyasallarinda]] — Bu makaledeki dozaj kararı, selüloz eterlerin DS/MS, jelleşme sıcaklığı ve viskozite–molekül ağırlığı mekanizmalarına dayanır; oradaki teori burada sayısal karara dönüşür.
- [[deneme-uretimi-alternatif-hammadde-recete-degisikligi]] — Dört üründe yürütülen alternatif hammadde denemesinin tüm ürünlerde ortak olan değişimi tam olarak bu selüloz eter ikamesidir; dozaj eşdeğerliği o denemenin en kritik performans riskidir.
- [[recete-olceklendirme-ve-fabrika-entegrasyonu]] — Hesaplanan hedef dozaj, laboratuvar denemesi için reçete 1 kg (veya küçük parti) bazına ölçeklenirken kullanılır; ölçekleme makalesindeki tartım hassasiyeti uyarısı burada kritik hale gelir.
- [[ty-ak-test-standart-kod-referansi]] — TY.AK.160 (viskozite tayini) bu eşdeğerlik hesabının çıkış noktası, TY.AK.009/161/225 ise doğrulama testleridir.

## Kaynaklar

- import-2026-07-part-002.md
