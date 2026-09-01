---
name: not-defteri-isleme
description: "📥 000-Inbox/Dump/Not Defteri.md dosyasındaki ham notları (konuşma özetleri, Granola transkriptleri, iş fikirleri, görsellerle anlatılan görevler) okuyup ayrıştırır ve doğru yerlere (Threads.md, Todoist, knowledge/concepts, proje dosyaları, Bütçe Takibi) dağıtır. \"not defterini işle\", \"dump'ı işle\", \"notlarımı dağıt\" dendiğinde ya da Not Defteri.md'de işlenmemiş içerik fark edildiğinde kullan."
---

# Not Defteri İşleme — Yakala → Ayrıştır → Dağıt

Akif `📥 000-Inbox/Dump/Not Defteri.md` dosyasına düzensiz, ham notlar atıyor — biriyle
konuştuğu bir şey, Granola toplantı kaydı, "şurada şunu şurada bunu yapacağım" tarzı iş
fikirleri, bazen görsellerle. Amaç: bu ham notu Akif'in kendisi düzenlemesin, ben okuyup
doğru yerlere dağıtayım, dosyayı tekrar boş/temiz bırakayım.

## Ne Zaman Çalışır
- Akif "not defterini işle" derse
- Akif "Granola kaydını işle" derse (transkript Not Defteri'ne yapıştırılmış olabilir)
- Bir oturumda Not Defteri.md'de yeni/işlenmemiş içerik fark edersem, sormadan işleyip
  kısaca özet geçebilirim ("not defterindeki şunu şuraya taşıdım" gibi)

## Adımlar

1. **Oku:** `📥 000-Inbox/Dump/Not Defteri.md`'yi baştan sona oku. "---" ayraçlı başlangıç
   satırından sonraki her yeni blok potansiyel bir işlenmemiş girdi.

2. **Sınıflandır** — her girdi için:
   - **Kişiyle konuşma/duyum notu** → önemliyse ilgili Threads.md thread'ine ekle (yoksa
     yeni thread aç), önemsizse (arşivlik bilgi) knowledge/concepts'e kısa bir makale
   - **Granola/toplantı transkripti** → HAM METNİ olduğu gibi taşıma, damıt: kararlar,
     aksiyon maddeleri, önemli cümleler çıkar; doldurma/gevezelik kısmını at. Sonucu
     ilgili Threads.md thread'ine veya knowledge/concepts'e yaz
   - **Görev/yapılacak iş** (tek satırlık, net) → Todoist'e ekle (uygun etiketle: ev, iş vb.)
   - **Proje işi, görsellerle anlatılan "şurada şunu yap"** → ilgili projenin kendi
     alanına (🏰 300-Projects/<proje>/ altında bir TODO/görev dosyası, ya da o proje zaten
     Threads.md'de bir thread olarak takip ediliyorsa oraya) yaz. Görseller varsa dosya
     yolunu not et, silme
   - **Yapı Kimyasalları işi** — bunları İKİYE ayır (Akif'in kuralı, 2026-09-01):
     - **Tek seferlik, başı-sonu belli** (reçete değişikliği, standart özeti çıkarma,
       deneme üretimi, araç kurulumu) → `🏰 300-Projects/Yapı Kimyasalları 101/Proje Bazlı
       İşler.md`
     - **Tekrarlayan, dönemsel** (aylık rapor, periyodik kontrol kaydı, düzenli SAP girişi)
       → `🏰 300-Projects/Yapı Kimyasalları 101/Rutin İşler.md`
     - Emin değilsen sor — proje/rutin ayrımı yanlış olursa iş yanlış yerde kaybolur.
   - **Para/harcama bilgisi** → `🔐 400-Vault/Bütçe Takibi.md`'ye işle
   - **Belirsiz/önemsiz** → knowledge/concepts'e küçük bir not olarak düş, en azından kaybolmasın

3. **Bağlantı kur:** Yeni yazdığın her not, ilgili varsa mevcut Threads.md thread'ine veya
   knowledge/concepts makalesine `[[wikilink]]` ile bağlansın — kopuk bilgi bırakma.

4. **Dashboard.md'yi güncelle** eğer işlenen içerik durum panosunu etkiliyorsa (yeni görev,
   kapanan iş, önemli karar).

5. **Not Defteri'ni temizle:** İşlenen girdiyi dosyadan SİL (kopyası zaten doğru yere
   taşındı, burada tutmaya gerek yok — inbox'un amacı "boş kalmak"). Dosyanın en altına
   kısa bir "İşlendi" logu düşebilirsin (tarih + nereye taşındığı, tek satır), ama ham
   içeriği tekrar tekrar tutma.

6. **Akif'e özet ver:** Ne işlendi, nereye gitti — kısa liste. Uzun anlatma.

## Önemli
- Ham bilgiyi kaybetme — sınıflandırırken emin değilsen knowledge/concepts'e düş, silme.
- Görsel dosya yollarını asla silme, sadece referans ver.
- İşlemeden önce emin değilsen (örn. bu bilgi hangi projeye ait) kısa bir soru sor,
  tahmin etme — ama çok sık sorma, bariz olanları kendin karar ver.
