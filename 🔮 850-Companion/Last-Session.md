# Son Oturum — 2026-08-31: standart-paket Sıfırdan Yeniden Yazımı + Responsive Debug Metodolojisi

**Odak:** Cafe web sitesi tamamen sıfırdan yazıldı (yeni repo: `standart-paket`), art arda
gelen mobil taşma/hizalama sorunları teşhis edilip kalıcı bir test metodolojisine dönüştürüldü.

## Yapılanlar

### 1. standart-paket Reposu — Sıfırdan Yazım
Eski `cafe` reposu tamamen terk edildi (yamalarla uğraşmak yerine baştan yazıldı).
Yeni repo: `regular07/standart-paket`, canlı: https://regular07.github.io/standart-paket/

- **Stack:** HTML5 + Bootstrap 5.3 (CSS) + Swiper.js 11 (kaydırmalı kartlar) + vanilla JS
- **Bölümler:** Navbar, Hero (parallax + overlay), Öne Çıkanlar slider, filtrelenebilir+
  aranabilir Menü, Yorumlar, Rezervasyon formu, Footer (sosyal medya + WhatsApp), sabit
  WhatsApp/scroll-top butonları
- **SEO:** Meta description/keywords, Open Graph, Twitter Card, canonical, JSON-LD
  `CafeOrCoffeeShop` structured data, robots.txt, sitemap.xml
- **Kod stili:** Her bölümde "ne işe yarıyor, neden böyle" açıklayan yorum satırları
  (kullanıcı özellikle istedi — başka bir yazılımcı review'da rahat gezinsin diye)

### 2. Art Arda Gelen Responsive Bug'lar — Hepsi Kök Sebebine İnilerek Çözüldü
- Navbar ortada asılı kalma → `html`de `overflow-x:hidden` fixed-position'ı bozuyordu
- Hero'da üstten cream boşluk → `body{padding-top:76px}` hack'i navbar fixed olduğu için
  body'nin arka planını görünür bırakıyordu; kaldırıldı, hero navbar arkasına uzatıldı
- Hero overlay/background-position → yatay gradient "boşluk" hissi veriyordu, düzleştirildi;
  background-position fincan odaklı yapıldı (center 38%)
- **Navbar mobilde yatay scroll** → asıl kök sebep: `html`nin overflow-x'i "visible"
  bırakıldığında body'nin overflow-x:hidden'i viewport'a HER ZAMAN propagate edilmiyor
  (canlı JS testiyle kanıtlandı: docScrollWidth 343 vs innerWidth 331). Çözüm: html+body
  ikisine birden overflow-x:hidden + fixed elemanların (navbar) kendi üzerine ayrıca
  overflow-x:hidden/max-width:100vw + box-sizing:border-box kendi CSS'te de tanımlandı
  (CDN'e bağımlı kalmasın diye)
- Her düzeltmede tarayıcı cache'i sorun çıkardı → style.css?v=N cache-busting parametresi
  eklendi, sunucu-tarafı `curl` doğrulaması alışkanlık haline getirildi

### 3. Yeni Skill + Knowledge Kalıcılaştırıldı
- **Skill:** `.claude/skills/responsive-tasma-testi/SKILL.md` — 6 adımlı test protokolü
  (ölç → taşan elemanı bul → 4 bilinen sebebi kontrol et → düzelt → cache kontrolü →
  canlıda doğrula). Artık "sağa sola scroll atıyor" tarzı şikayetlerde otomatik tetiklenir.
- **Knowledge:** `knowledge/concepts/responsive-yatay-tasma-teshis-ve-cozum.md` — JS ile
  ölçüm teknikleri, 4 sebep, html'de overflow-x vs position:fixed çelişkisinin çözümü

### 4. OneDrive Sync Sorunu (tekrar gözlemlendi)
`🔮 850-Companion/` klasöründeki dosyalar zaman zaman "online-only" takılı kalıp
okunamıyor (ETIMEDOUT). Sebep muhtemelen OneDrive.app'in arka planda kendi kendine
kapanması — sadece File Provider extension'ı ayakta kalıyor, ana sync motoru değil.
`open -a OneDrive` ile yeniden açmak geçici olarak çözüyor ama kalıcı değil.

## Açık Sorunlar

1. **OneDrive.app kendiliğinden kapanıyor** — kalıcı çözüm bulunmadı, oturum başında
   kontrol edip gerekirse yeniden açmak gerekebilir.
2. Yapı Kimyasalları standart skill'leri hâlâ tamamlanmadı (102 PDF + 5 markdown özeti
   bekliyor) — bu oturumda hiç dokunulmadı.
3. Eski `cafe` reposu artık kullanılmıyor, ama silinmedi de — GitHub'da duruyor.

## Sırada

- Kullanıcı standart-paket sitesini telefonda son kez test edecek
- Yapı Kimyasalları standart skill'lerine dönülmesi gerekiyor (uzun süredir bekliyor)
- Diğer sektörler için de aynı `standart-paket` şablonu türetilebilir (kuaför, restoran vb.)

## Ton

Kullanıcı sorunu bizzat DevTools'a girip ölçerek doğruluyor, tahminimi kabul etmiyor —
bu iyi bir şey, "kanıtla" kültürü oturdu. Sorun çözülünce net ve sıcak teşekkür ediyor
("eline sağlık sorunum düzeldi").
