---
title: SAP QM'de Kalite Kontrolde Kalan Stok Sorun Giderme
aliases: [QA32, QA33, MB51, MB5B, MB53, muayene partisi bulma, kalite kontrol stoğu asılı kalması, 321 hareket türü]
tags: [yapi-kimyasallari, kalite-kontrol, sap]
sources: [import-2026-07-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# SAP QM'de Kalite Kontrolde Kalan Stok Sorun Giderme

Bir hammadde MB52 stok listesinde "kalite kontrolünde" olarak görünmesine rağmen QP02 ekranında hiçbir muayene partisi çıkmadığında, sorunun kaynağını bulmak için sırasıyla farklı SAP işlemleri (QA32/QA33, MMBE, MB53, MB51, MB5B) denenmesi gerekir. Tipik kök neden, silobus/tanker girişinde kalite kontrolden serbest stoğa düşüm yapılırken eksik miktar girilip onaylanmasıdır (kısmi/parsiyel kullanım kararı); kalan miktar sistemde asılı kalır.

## Önemli Noktalar

- QP02 doğrudan arama ekranı değildir, belirli bir muayene partisi (inspection lot) numarası ister; önce **QA32/QA33** ile malzeme+fabrika+depo yeri girilip **tüm statü kutucukları** (Oluşturuldu, Serbest bırakıldı, Tamamlandı vb.) işaretli bırakılarak geniş arama yapılmalıdır.
- Parti (batch) takibi aktif olmayan hammaddelerde (bu vakada Portland çimento) parti numarasıyla arama yapılamaz; **MMBE/MB53** (stoka genel bakış) bu durumda sadece stok tipi toplamını (Serbest/Kalite Kontrolünde/Bloke) gösterir, parti bazlı kırılım vermez.
- En güvenilir yöntem **MB51** (malzeme belge listesi) ekranında **hareket türü 321** (Kalite Kontrol ↔ Serbest Kullanılabilir) satırlarını kronolojik incelemektir: birbirini dengeleyen (eşit +/-) çiftler normal transferdir, asıl kayıp mal girişi (101 hareketi) ile düşüm (321 çıkışı) arasındaki miktar farkından kaynaklanır.
- **MB5B** (stok karşılaştırma) ekranında "Özel stok" ve "Depo yeri/parti stoku" radyo butonları karıştırılırsa depo yeri alanı kırmızı hata verip sıfırlanır; normal (özel stok olmayan) bir hammadde için doğru seçenek "Depo yeri/parti stoku"dur.
- Düzeltme, QA02/QA12 (muayene partisi karar ekranı) üzerinden değil — eğer altta bir QM lotu hiç yoksa — **MIGO** ile 321/322 hareket türü kullanılarak doğrudan stok tipi transferiyle yapılır; bu işlem yetki gerektirdiği için genelde depo/lojistik veya SAP anahtar kullanıcısı tarafından yürütülür.

## Detaylar

Araştırma sırası pratikte şöyle işler: QA32/QA33'te lot bulunamazsa, bu genelde stoğun bir muayene partisine hiç bağlanmadığı, manuel bir stok tipi değişikliğiyle (MIGO/MB1B, 321 hareket türü) doğrudan Q statüsüne alındığı anlamına gelir. Bu durumda MMBE ile stok genel görünümüne bakılır; sağ tık/çift tık ile parti detayına inilemiyorsa (parti takibi kapalı), sıradaki adım MB51'de malzeme+fabrika+depo yeri filtresiyle tüm hareketleri çekip 321 satırlarını gözle veya Excel'e aktararak (Liste → İhracat → Elektronik tabloya) kümülatif toplamaktır.

Vakada saptanan somut senaryo: silobus ile gelen çimento kalite kontrol stokuna düşmüş, kullanıcı düşümü onaylarken tam miktarı değil eksik bir miktarı girip onaylamış, kalan (bu örnekte 2.450 KG) miktar sistemde kalite kontrol stokunda asılı kalmıştır. Bu tür "kısmi kullanım kararı" durumları, MB51'deki 321 hareketlerinin mal girişi (101) miktarıyla birebir eşleşip eşleşmediği kontrol edilerek yakalanır.

## İlgili Kavramlar

- [[hammadde-sap-kalite-kontrol-formati]] — Bu sorun giderme süreci, QP02 formatında tutulan muayene partisi/kalite kontrol kayıtlarının SAP tarafındaki işlemsel (transaction) karşılığını tamamlar.
- [[yapi-kimyasallari-urun-standartlari]] — Fabrika içi üretim kontrolü (FPC) kapsamında hammaddenin kalite kontrol statüsünden serbest kullanılabilir stoğa geçişi, standartların öngördüğü sürekli kalite güvence sürecinin bir parçasıdır.

## Kaynaklar

- import-2026-07-part-001.md
