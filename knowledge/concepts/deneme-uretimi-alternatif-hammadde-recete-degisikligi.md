---
title: Deneme Üretimi ve Alternatif Hammadde Reçete Değişikliği
aliases: [alternatif fantom hammadde, deneme üretimi reçete karşılaştırması, weber.kol alternatif CE, maliyet optimizasyonu reçete, eski-deneme-önerilen üç sütun sunumu, Arbocel çıkarma, çimento uçucu kül ikamesi]
tags: [yapi-kimyasallari, formulasyon, uretim, maliyet, sunum]
sources: [import-2026-07-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# Deneme Üretimi ve Alternatif Hammadde Reçete Değişikliği

Kuru harç üreticilerinde reçeteler dönemsel olarak "alternatif hammadde" deneme üretimleriyle revize edilir; SAP'te bu alternatifler çoğu zaman "fantom" kodlarla (ör. 6ALT-RDP-11, 6ALT-CAFO-02) girilir. Dört weber.kol seramik yapıştırıcısında (6DUT26140 Standart Gri Ç2, 6DUT26141 Serakol Gri Ç1, 6DUT26142 Flex Porselen Gri Ç1-1, 6DUT26143 XL Flex Gri Ç1; hepsi 2600 kg / 104×25 şarj) eş zamanlı yürütülen bir deneme, ölçekleme dosyasındaki (o_lc_ekleme.xlsx) orijinal reçetelerle karşılaştırılarak analiz edilmiştir. Değişikliklerin çoğu maliyet azaltmaya yöneliktir ve bir kısmı ürün kalitesini riske atar.

## Önemli Noktalar

- **Tüm ürünlerde ortak:** farklı Tylose (MHEC) tipleri → tek Walocel MKS 20000 PF30 (HPMC) konsolidasyonu; VINNAPAS ve Kalsiyum Formiat alternatif fantom kodlarına geçiş; Casucol Fix 1 (nişasta eteri) → Emset KH-6.
- **Serakol Gri en "temiz" deneme:** çimento, kalker, uçucu kül, taş tozu, Emset KH-6 miktarları birebir aynı; yalnızca 3 kimyasalın (VINNAPAS, Ca-formiat, selüloz eter) kodu/tipi değişmiş, miktarlar sabit (selüloz eter 7,02 kg → 7,02 kg).
- **Standart Gri ve XL Flex Gri'de potens riski:** eski reçetede 60.000 + 10.000 mPa·s'lik iki MHEC karışımı vardı, yeni reçetede tek 20.000 mPa·s HPMC; miktar neredeyse sabit tutulduğu için yüksek viskoziteli bileşenin potens kaybı telafi edilmemiş (bkz. viskozite–dozaj eşdeğerliği).
- **XL Flex Gri'de yapısal değişiklikler:** ARBOCEL PWC 500 elyaf takviyesi (3,9 kg) tamamen kaldırılmış (çatlak köprüleme/kayma davranışı riski), Casucol Fix 1 çıkarılıp Emset KH-6 eklenmiş, iki VINNAPAS grade tek kaleme birleşmiş, kalker +3,38 kg ile toplam telafi edilmiş.
- **Flex Porselen Gri'de bağlayıcı sistemi değişikliği:** çimento 1040 → 780 kg (−260 kg, ≈ −%25) ve reçeteye 260 kg uçucu kül eklenmiş — bu bir katkı değişimi değil, hidratasyon kimyasını doğrudan etkileyen bağlayıcı ikamesidir; en yüksek performans riski burada ve XL Flex'teki fiber çıkarımındadır.

## Detaylar

Değişiklikler bir bütün olarak maliyet optimizasyonudur: hammadde konsolidasyonu (çok tipli selüloz/RDP → tek kalem), pahalı katkının azaltılması (elyaf çıkarma), çimentonun kısmen uçucu külle ikamesi. Şirket için olumlu, ancak açık zaman, su tutma, kayma ve esneklik gibi performans özelliklerini riske atabilir. Elyafın ve uçucu külün kasıtlı olarak değiştirildiği (gözden kaçma olmadığı) teyit edilmiştir.

**Müdüre sunum stratejisi:** üç sütunlu karşılaştırma — *eski reçete / deneme reçetesi / önerilen test reçetesi*. Üçüncü sütun "yeni reçete" değil "test edilmesi önerilen hipotez" olarak sunulur (henüz pilot doğrulaması yoksa kesin çözüm gibi sunmak geri adım riski taşır). Her satıra bir "neden" eklenir: gözlemlenen sorun (ret oranı, uygulama zorluğu, standart uyumsuzluğu) → önerilen değişiklik → neden çözer. Deneme üretimi bir köprü/hikâye olarak anlatılır: geçmiş → deney → öneri. Kapanışta somut talep olur: küçük ölçekli pilot üretim için onay.

**Katkının değeri ve etik çerçeve:** sunumun asıl değeri genel standart bilgisi tekrarı değil, yerel/pratik gözlemdir — "bu kimyasal bu oranda bizim üretim hattımızda / iklimimizde / hammadde kaynağımızda şu sorunu çıkarabilir, şöyle test edip doğrulayabiliriz". Şirketin özel reçete oranları dışarıya (AI dahil) aktarılmaz; sunumda araç veya araştırma süreci değil, sonuç ve kişinin kendi yorumu öne çıkarılır ("standartları inceledim, literatürü taradım").

## İlgili Kavramlar

- [[seluloz-eter-viskozite-dozaj-esdegerligi]] — Denemenin tüm ürünlerde ortak olan değişimi selüloz eter ikamesidir; "aynı kg = aynı performans değil" sorunu Standart ve XL Flex'te doğrudan geçerlidir.
- [[recete-olceklendirme-ve-fabrika-entegrasyonu]] — Deneme ve önerilen reçeteler, laboratuvar denemesi için ölçekleme dosyasındaki oran mantığıyla küçük partiye (ör. 1 kg) ölçeklenir.
- [[kalker-kayma-sorunu-vaka-analizi]] — Her ikisi de kök neden / kör nokta çalışmasıdır; kalker vakasında tespit edilen "aynı anda birden fazla değişkenin hareket etmesi" kör noktası bu denemede (kimya sınıfı + viskozite profili + bağlayıcı) tekrar ortaya çıkar.
- [[ty-ak-test-standart-kod-referansi]] — Deneme partilerinin değerlendirilmesi TY.AK.009 (açık zaman), TY.AK.161 (kayma) ve su tutma testleriyle yapılır.

## Kaynaklar

- import-2026-07-part-002.md
