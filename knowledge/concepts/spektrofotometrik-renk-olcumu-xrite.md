---
title: Spektrofotometrik Renk Ölçümü (X-Rite) ve Göz Kararı Sorunu
aliases: [X-Rite, spektrofotometre, CIE Lab, CIE L*a*b*, delta E, ΔE, renk farkı, beyazlık indeksi, sarılık b* değeri, göz kararı renk kontrolü, illuminant gözlemci]
tags: [kalite-kontrol, renk-olcumu, yapi-kimyasallari, metroloji, derz-dolgu]
sources: [import-2026-08-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# Spektrofotometrik Renk Ölçümü (X-Rite) ve Göz Kararı Sorunu

Spektrofotometre (X-Rite gibi) bir yüzeyin spektral yansımasını ölçüp rengi sayısal olarak (CIE L*a*b*) ifade eder; iki renk arasındaki fark ΔE ile nicelenir. Kuru harç / derz dolgu üretiminde renk kontrolü "göz kararı" ile yapıldığında parti-parti tutarlılık nesnel olarak izlenemez — beyaz ürün için bile beyazlık/sarılık bir kalite parametresidir. Cihazsal ölçüme geçiş önerisi hem teknik bir iyileştirme hem de kariyer için somut bir "iş vakası"dır.

## Önemli Noktalar

- **CIE L*a*b*:** L* açıklık (0 siyah – 100 beyaz), a* yeşil–kırmızı ekseni, b* mavi–sarı ekseni. ΔE iki renk arasındaki toplam (öklidyen) farktır; kalite toleransı bir ΔE eşiğiyle tanımlanır.
- **Ölçüm koşula bağlıdır:** illuminant (ör. D65) ve gözlemci açısı (2° / 10°) standartlarına göre yapılır; kıyaslama ancak aynı koşulda anlamlıdır. Spektral yansıma ölçüldüğü için metamerizm (farklı ışıkta farklı görünme) de yakalanır.
- **Beyaz üründe renk bir kalite parametresidir:** beyazlık indeksi ve b* (sarıya kayma) parti sapmasını gösterir; "renkli mi, değil mi" ikili yargısı yetersizdir.
- **TS EN 13888 (derz dolgu) gibi standartlar parti-parti tutarlılığı dolaylı olarak bekler;** nesnel renk ölçümü olmadan bu tutarlılık kanıtlanamaz. Yalnızca beyaz üretilip pigment (demir oksitler, kobalt mavisi) kullanılmıyorsa, ayrıca pigment kimyası bilgi boşluğu oluşur.
- **İş vakasına dönüştürme:** göz kararı → spektrofotometre önerisi, cihaz maliyeti vs. önlenen müşteri şikâyeti/iade (ROI) ve rakip firma uygulamasıyla desteklenir; DMAIC (Ölç–Analiz–İyileştir) projesi olarak da işler.

## Detaylar

Kalite kontrol müdürünün göz kararını yeterli görmesi çoğu zaman çalışanı aşan bir karardır. Yine de ölçüm mantığını (CIE Lab, ΔE hesabı, illuminant/gözlemci standartları) kendi başına öğrenip kısa bir öneri/karşılaştırma notu hazırlamak; hem teknik bilgiyi kanıtlar hem de "sorunu görüp kabaca dayatmadan öneren" bir profil çizer — yönetici pozisyonuna geçişte tam da bu tutum aranır. ISO/IEC 17025'in kalibrasyon ve ölçüm belirsizliği maddeleri bu öneriye teknik dayanak sağlar: cihazsal ölçüm sonuçlarına da bir belirsizlik bandı eklenir, ama bu bant göz kararının tekrarlanamazlığından çok daha küçüktür ve dokümante edilebilir.

## İlgili Kavramlar

- [[kalite-kontrol-kariyer-sertifikasyonlari]] — göz kararı vs cihazsal ölçüm karşılaştırması, Six Sigma Green Belt için gerçek bir DMAIC projesine ve mülakatta anlatılacak somut "kalite sistemini iyileştirdim" örneğine dönüştürülür.
- [[yapi-kimyasallari-urun-standartlari]] — TS EN 13888 derz dolgu ürününde renk/beyazlık parti tutarlılığı örtük bir performans beklentisidir; nesnel renk ölçümü bu gerekliliği karşılamanın yoludur.
- [[hammadde-sap-kalite-kontrol-formati]] — b* / beyazlık indeksi ve ΔE, SAP QP02 kalite kontrol planına alt/üst sınırlı, ölçülebilir bir kontrol karakteristiği olarak eklenebilecek parametrelerdir.

## Kaynaklar

- import-2026-08-part-001.md
