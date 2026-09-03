---
title: Aylık Rapor — SAP Veri Çekme Adımları
created: 2026-09-03
modified: 2026-09-03
type: note
status: active
tags: [yapi-kimyasallari, rutin, aylik-rapor, sap]
---

# Aylık Rapor — SAP Veri Çekme Adımları

İş yerindeki fiziksel not defterinden (12–15 Mart sayfaları) aktarıldı. Aylık raporu
hazırlamak için üç SAP ekranı: **rejenere ekranı**, **SAP Replica (hammadde)**, **KPI doldurma**.
`[?]` = el yazısından tam okunamayan, işyerinde teyit edilecek yer.

İlgili: [[Rutin İşler]] → Aylık Rapor Hazırlığı · fabrika kodu her yerde **6052**.

---

## 1) SAP Rejenere Ekranı (rejenere tüketim raporu)

**Amaç:** seçilen ayda rejenere edilmiş ürünlerin tüketim raporunu çekmek.

1. **SQ00** gir (SAP Query ekranı). Komut kutusuna `sq00` yazıp Enter — "SAP sorgusu: Sorguları başlat".
   ![[ekler/rejenere-01-sq00-easy-access.jpg]]
2. Açılan **"kullanıcı grubu sorgusu: Başlat"** ekranında, üst menüde **"Ortam"** → **"Çalışma alanları"**.
   ![[ekler/rejenere-02-ortam-calisma-alanlari.jpg]]
3. Açılan **"Çalışma alanları"** kutusunda **"Standart alan (üst birime bağlı)"**ı seç → **"Seç"**. (Ekran adı: "kullanıcı grubu sorgusu: Başlangıç ekranı".)
   ![[ekler/rejenere-03-standart-alan-sec.jpg]]
4. **"TR_QM_001 kullanıcı grubu sorgusu: Başlangıç ekranı"** açılır (kullanıcı grubu `TR_QM_001 : SGWM QM Team`). Listeden **`TR_QM_REJ_TUK` — "Rejenere Tüketim Raporu"** satırını seç → üst araç çubuğundaki **"Yürüt (F8)"** (saat benzeri yeşil ikon) butonuna bas.
   ![[ekler/rejenere-04-sorgu-listesi-rej-tuk.jpg]]
   > Not: aynı listede **`TR_QM_HAMM_TUK` — "KK İçin Hammadde Tüketim Raporu"** var; SAP Replica / hammadde kısmı bununla ilişkili olabilir, kontrol et.
5. **"Rejenere Tüketim Raporu"** filtre ekranı açılır — "Rapora özgü seçimler" bölümü. Her satır **baş / son** aralığı:
   ![[ekler/rejenere-05-filtre-ekrani.jpg]]
   | Alan | baş | son |
   |---|---|---|
   | Belgedeki kayıt tarihi | çekilecek ayın 1'i (örn `01.07.2026`) | ayın son günü, **dahil** (örn `31.07.2026`) |
   | İşlem türü (stok yönetimi) | `261` | `262` — genelde otomatik dolu gelir; boşsa elle yaz |
   | Üretim yeri | `6052` (Antalya fabrika kodu) | `6052` |
   | Depo yeri | `2000` | `3000` |
   | Parti no / Sipariş no / Malzeme no | boş | boş |
   | Çıktı belirtimi → Düzen | boş | — |
6. Alttaki kutucuklar boş → sol üstteki **"Yürüt"** butonuna bas.
7. Çıkan ekranda seçilen ayın rejenere edilmiş ürünleri listelenir.

**Excel'e alma ve dosyalama** (13 Mart sayfası, el yazısı kısmen okunaklı `[?]`):

8. Ekrana rejenere edilmiş ürünler listelenir. "Rejenere Tüketim Raporu" başlığının hemen üstündeki araç çubuğunda **sondan 6. buton = "Görünüm"**. Ona bas → açılan menüden **"Excel Inplace"** seç (diğer seçenekler: "Liste çıktısı", "Izgara"). Tüm veri Excel'e aktarılır.
   ![[ekler/rejenere-06-sonuc-listesi-excel-inplace.jpg]]
9. Excel "ALV içindeki Çalışma Sayfası - Uyumluluk Modu" olarak açılır. Alttaki sheet'ler: `Format, Header, Pivot, Sub1…Sub10, RawData, RawHeader`. **`RawData` hariç tüm sheet'leri sil** (RawHeader dahil). Kalan tek sheet = ham veri.
   ![[ekler/rejenere-07-excel-sheet-temizligi.jpg]]
10. **Farklı kaydet** → **Masaüstü**'ne, isim formatı: **`REJENERE AY_YIL`** (örn `REJENERE TEMMUZ_2026`).

### Ham veriyi Yücel formatına dönüştürme (3 Eylül — ŞUBAT/MAYIS/TEMMUZ dosyalarından çözüldü)

Ham `RawData` = **17 sütun**. Yücel'in aylık rapora koyduğu format = **10 sütun + altında özet blok**.
Referans: `ŞUBAT REJENERE`, `MAYIS REJENERE` dosyaları.

**11. Fazla 7 sütunu sil** (kalan 10 zaten doğru sırada, taşıma yok):
`Sipariş` · `Mlz.blg.` · `İTü` (hep 261) · `Depo yeri` (boş) · `TÖB` · `TÖB` · `Mal giriş miktarı`

**12. 2 başlığı yeniden adlandır** (ikisi de "Malzeme numarası" diye geliyor):
- B sütunu → **Üretilen Ürün** (rejenere sırasında üretilen/harcanan ana ürün)
- E sütunu → **Rejenere Edilen Ürün** (içine karıştırılan geri-dönüşüm malzemesi)
- Kalan 8 başlık aynı: `Malzeme · Kayıt trh. · Malzeme · ÜY · DpYr · Parti · Miktar · SÖB`

Ham → Yücel sütun eşlemesi: `C→A Malzeme` · `D→B Üretilen Ürün` · `E→C Kayıt trh.` · `G→D Malzeme` · `H→E Rejenere Edilen Ürün` · `I→F ÜY` · `J→G DpYr` · `L→H Parti` · `M→I Miktar` · `Q→J SÖB`

**13. Özet bloğu** — veri satırlarının 2 satır altına. Her satırı sırayla sınıflandır (ilk uyan):
1. Rejenere Edilen Ürün = `6YK2` (KUM MALİYETLİ YIKAMA KALSİDİ) → **ÜRÜN İÇİNE 6YK2**
2. Üretilen Ürün = `KALKER` (`6HD0516`) → **KALKER İÇİNE ÜRÜN**
3. Rejenere Edilen Ürün = deneme malzemesi (kod `6DUT…`, adında "- 0,7 M-4 K" tarzı param) → **ÜRÜN İÇİNE DENEME ÜRETİMİ**
4. Hiçbiri → **ÜRÜN İÇİNE ÜRÜN**

Her kategori = o satırların **Miktar** toplamı (eksi/iade satırı varsa işaretiyle). O ay hiç görülmeyen kategoriyi yazma.

**14. Genel Toplam + sheet adı:**
- En alta `Genel Toplam` satırı, formül `=SUM(...)` (kategori hücrelerini kapsar).
- Sheet adını aya göre değiştir: **`TEMMUZ REJENERE`** (ham "RawData" adı kalmasın).
- Son kontrol: Yücel'in son aylık rapor mailindeki eke bak — sütun sırası/başlık/özet birebir mi?

**Temmuz 2026 doğrulaması:** 20 veri satırı · ÜRÜN İÇİNE 6YK2 = 6.400 · KALKER İÇİNE ÜRÜN = 5.530 · ÜRÜN İÇİNE ÜRÜN = 2.200 · **Genel Toplam = 14.130 kg**. Akif'in düzelttiği dosya kontrol edildi, tüm toplamlar doğru; tek eksik: sheet adı hâlâ `RawData` idi.

Görselli tam anlatım: sunum `Aylik-Rapor-Rejenere-Raporu-Hazirlama.html` (Adım 10–14) · [Artifact](https://claude.ai/code/artifact/708b83a4-0c63-4fe5-ac52-b8348dd70be6)

---

## 2) SAP Replica (hammadde çekme)

**Amaç:** seçilen ay için tüm hammadde malzemelerini Excel olarak almak.

1. **QM** `[?]` işlemine gir.
2. Açılan ekrandan **tarih aralığı** seç (örn `01.06` – `01.07` — ay başından ay başına).
3. **Fabrika kodu:** `6052`.
4. **3. kutudan** "giriş" tık'ını seç. `[?]`
5. **"Göster"** butonuna bas. (Program "yanıt vermiyor" haline geçecek — **hiçbir şeye dokunma**, bekle.)
6. Tüm malzemeler ekrana geldiğinde **dosya adını gir** → `Hammadde_Haziran_2026` (ay/yıl güncellenir) → **"Excel olarak aktar"** butonuna bas.
7. Genelde hata verir; **2–3 kere daha** "Excel olarak aktar"a bas. Sonra **bilgisayara restart at**.
8. Restart sonrası herhangi bir Excel dosyası aç → soldaki **"kurtarılan dosyalar"** bölümünden aktardığın dosyayı bulabilirsin.

---

## 3) KPI Doldurma

1. Attığın (aktardığın) dosyayı **"farklı kaydet"** ile kaydetmeyi unutma.
2. Sonrasında **Yücel'in geçmişte attığı mail formatında** düzenle (aylık rapor maili).
3. **KPI doldurma adımları not defterine yazılmamış** — Akif'in kafasında ("zaten biliyorsun"
   notu var). Bir dahaki hazırlıkta adımları buraya ekle.

---

## Ekran görüntüleri (eklenecek)

Akif işyerinde çekip gönderecek; her biri `ekler/` klasörüne kaydedilip ilgili adıma gömülecek.
Faydalı olacak kareler:

- **Rejenere:** ✅ tamam (7 ekran görüntüsü: SQ00 → Ortam → Standart alan → sorgu listesi → filtre → sonuç/Excel Inplace → sheet temizliği). Kalan tek belirsiz: adım 11 "Yücel formatına getirme" — KPI doldurma ile birlikte netleşecek.
- **SAP Replica:** QM `[?]` açılış ekranı · tarih + fabrika (6052) + "3. kutu giriş tık" ekranı · "Göster" butonu · malzeme listesi + "Excel olarak aktar" butonunun yeri
- **KPI:** Yücel'in referans mail formatı (bir örnek ay)

## Özet akış

Rejenere tüketim raporu (SQ00) → Excel `REJENERE AY_YIL` (masaüstü) · Hammadde (SAP Replica / QM) →
Excel `Hammadde_Ay_Yıl` · her iki excel Yücel'in formatına getirilir → KPI doldurulur →
Yücel'in mail formatında aylık rapor gönderilir.
