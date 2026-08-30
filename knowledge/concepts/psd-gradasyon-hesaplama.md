---
title: PSD ve Gradasyon Hesaplaması
aliases: [Particle Size Distribution, Fuller-Thompson formülü, tane boyutu dağılımı, EKK n katsayısı, reçete ağırlıklı teorik PSD]
tags: [yapi-kimyasallari, kalite-kontrol, formulasyon, istatistik]
sources: [import-2026-06-part-001.md, import-2026-07-part-001.md]
created: 2026-08-26
updated: 2026-08-28
---

# PSD ve Gradasyon Hesaplaması

PSD (Particle Size Distribution / tane boyutu dağılımı), bir toz malzemenin parçacıklarının boyutlara göre nasıl dağıldığını gösterir ve kuru harç/yapı kimyasalları formülasyonunda su ihtiyacı, işlenebilirlik ve mekanik dayanımı doğrudan etkiler. Gradasyon ise PSD'nin elek analizi ile somutlaştırılmış, agrega karışımlarının Fuller-Thompson/Andreasen-Andersen formülüne göre değerlendirilmesidir. Elek üstü kalan gram değerlerinden kümülatif geçen yüzdeye dönüştürülüp bir hedef eğriyle (Fuller) kıyaslanır.

## Önemli Noktalar

- Elek analizinde ölçülen "elek üstü kalan %" değerleri önce kümülatif kalan %'ye, sonra `100 − kümülatif kalan` formülüyle kümülatif geçen %'ye çevrilir; bu son sütun PSD/gradasyon eğrisini oluşturur.
- Fuller-Thompson formülü: `P(d) = (d / D_max)^n × 100`; burada d elek boyutu, D_max karışımdaki en büyük tane boyutu, n gradasyon katsayısı, P(d) o boyuttan küçük tanelerin ideal yüzdesidir.
- n katsayısı ürün tipine göre tahmin edilebilir (ince sıva 0.25-0.30, seramik yapıştırıcısı 0.30-0.40, beton 0.50) ama en doğru yöntem **En Küçük Kareler (EKK)** ile gerçek ölçüm verisinden hesaplamaktır: `log(P/100) = n × log(d/D_max)` doğrusallaştırması üzerinden `n = Σ(x·y) / Σ(x²)` formülüyle bulunur (x=log(d/D_max), y=log(P/100), tava ve D_max hariç ara elekler kullanılır).
- Spec (alt-üst sınır) belirlemede istatistiksel yöntem kullanılabilir: gerçek ölçümlerin ortalaması ± 2×standart sapma, %95 güven aralığını verir; ancak üretim stabilitesi bozulan dönemlerde (kayma sorunu gibi) sorunsuz dönemin verisi referans alınmalıdır.
- Ar-Ge/kıyaslama amaçlı kullanılan Excel şablonlarında spec orta noktasından değil, gerçek ölçüm verisinden EKK ile n hesaplamak tercih edilir çünkü farklı fabrika/kalker kaynaklarını karşılaştırmaya izin verir.
- Rutin üretimde elek analizi hiç yapılmayan ürün gruplarında (ör. seramik yapıştırıcısı/weber.kol serisi) **reçete ağırlıklı teorik PSD** yöntemi kullanılır: her hammaddenin (kalker, çimento, kimyasallar) kendi ölçülmüş elek dağılımı reçetedeki ağırlık oranıyla çarpılıp toplanır; veri bulunmayan çok ince katkılar (çimento, RDP, selüloz eter) "tamamen ince, tümü tava" varsayılır.
- Hem ölçülmüş gerçek parti verisinden (ampirik n) hem reçete ağırlıklı teorik hesaptan (teorik n) çıkarılan n katsayıları karşılaştırıldığında, ampirik n teorik n'den sistematik olarak biraz (örn. sıva grubunda ~0.04) daha yüksek çıkabilir — bu, "ince bileşenler her elekten tam geçer" varsayımının hafif iyimser olduğuna işaret eder ve formülasyon çalışmalarında düzeltme faktörü olarak kullanılabilir.
- Elek bazında spec aralığı, sadece kaba agreganın katkı verdiği eleklerde hammaddenin kendi ölçülmüş min-max (p5-p95) aralığının ürünün reçetedeki hammadde oranıyla ölçeklenmesiyle kurulabilir; en ince elekte (tava) ise tüm reçete bileşenleri (agrega + bağlayıcı + kimyasallar) birlikte değerlendirilip tümleyen (100 − diğer sınırların toplamı) olarak hesaplanır.

## Detaylar

Elek analizi pratikte şu adımlarla PSD'ye dönüştürülür: (1) her elekte kalan gram, toplam numune gramına bölünüp yüzdeye çevrilir (% kalan), (2) büyük elekten küçüğe doğru bu yüzdeler kümülatif olarak toplanır (kümülatif kalan %), (3) `100 − kümülatif kalan %` işlemiyle kümülatif geçen % (asıl PSD/S-eğrisi) bulunur. D10/D50/D90 gibi referans noktalar bu eğriden okunur (D50: malzemenin yarısının altında kaldığı boyut).

Gradasyon formülünün mantığı: `d/D_max` oranı bir eleğin en büyük taneye göre göreli küçüklüğünü verir (0-1 arası), `n` üssü bu oranın eğrisini ince veya kaba tarafa kaydıran bir "ayar düğmesi"dir — n küçüldükçe eğri ince tarafa, büyüdükçe kaba tarafa kayar. Karışım (reçete) PSD'si, her hammaddenin kümülatif geçen eğrisinin reçetedeki ağırlık oranıyla çarpılıp toplanmasıyla (ağırlıklı ortalama) hesaplanır: `P_karışım(d) = Σ(oran_i × P_i(d))`.

Su oranı tahmini, hammaddelerin D50 ve yoğunluğundan spesifik yüzey alanı (`S ≈ 6/(ρ×D50)`) hesaplanıp ağırlıklı toplanmasıyla (`S_karışım`) ve ampirik bir katsayı ile (`W% = k×S_karışım×100 + W_min`) yapılabilir; ancak bu teorik değer genelde fabrika pratiğindeki gerçek su oranından (HPMC su tutması, kireç söndürme reaksiyonu, buharlaşma gibi etkiler nedeniyle) düşük çıkar ve kıvam testiyle (yayılma çapı) doğrulanmalıdır.

## İlgili Kavramlar

- [[yapi-kimyasallari-urun-standartlari]] — EN 1015-1 (elek analizi) ve EN 12808 serisi gibi test standartları, PSD/gradasyon hesaplamasının dayandığı elek analizini resmi olarak tanımlar.
- [[kalker-kayma-sorunu-vaka-analizi]] — Bir C2 yapıştırıcısında yaşanan kayma (slip) sorunu, kalker agreganın tava payındaki (ince fraksiyon) PSD değişimiyle kök neden analizi yapılarak açıklanmış ve spec revizyonu bu hesaplama yöntemiyle önerilmiştir.
- [[recete-olceklendirme-ve-fabrika-entegrasyonu]] — Reçete ağırlıklı teorik PSD hesaplaması, ölçeklendirme dosyasındaki hammadde ağırlık oranlarını doğrudan girdi olarak kullanır.

## Kaynaklar

- import-2026-06-part-001.md
- import-2026-07-part-001.md
