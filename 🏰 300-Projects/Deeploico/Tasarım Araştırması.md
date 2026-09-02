---
title: Deeploico Web Tasarım Araştırması
created: 2026-09-02
modified: 2026-09-02
type: note
status: active
tags: [deeploico, web-tasarim, arastirma]
---

# Deeploico — Web Tasarım Araştırması

Mimar: Fable. Patron: Akif. Bu dosya Akif'in "10.000 dolarlık site gibi fikirler
istiyorum, araştır, örnek göster, GitHub repo bul" isteğinin karşılığı. Amaç:
Deeploico'nun **kendi portfolyo + hizmet sitesi** — müşteriye "ben bu kaliteyi
veririm" kanıtı. Deploy: GitHub Pages (statik).

Şu anki başlangıç seviyesi: https://regular07.github.io/standart-paket/

---

## 0. Özet (önce bunu oku)

Üç yön öneriyorum, üçü de gerçekten yapılabilir, üçü farklı his:

- **Yön A — "Editöryel Sükûnet":** beyaz/krem zemin, dev serif başlıklar, çok
  boşluk, az ama sinematik hareket. Dergi gibi. Düşük risk, en hızlı çıkar.
- **Yön B — "Tech Studio":** koyu zemin, ince sans tipografi, ince çizgiler,
  yoğun ama zarif mikro-animasyon, smooth scroll. "Pahalı ajans" hissi en güçlü
  burada. Orta risk.
- **Yön C — "Bold Creative":** kocaman tipografi, 1-2 canlı marka rengi,
  asimetrik bento grid, oyunbaz imleç. Cesur, akılda kalıcı. En yüksek efor/risk.

**Stack önerisi tek cümle:** Astro + Tailwind CSS ile statik üret, hareket için
Lenis (smooth scroll) + GSAP (artık %100 ücretsiz), GitHub Actions ile GitHub
Pages'e otomatik deploy — hafif, hızlı, mevcut `standart-paket` altyapısıyla uyumlu.

---

## 1. Bir siteyi "10.000 dolarlık" gösteren şey ne?

YouTube "high-ticket website" içerikleri ve ajans kırılımlarında dönüp dolaşıp
aynı 8 madde çıkıyor. Hiçbiri sihir değil, hepsi disiplin:

1. **Tipografi hiyerarşisi.** Hero başlıkları masaüstünde 80px+; net bir
   ölçek (başlık / alt başlık / gövde / etiket); tek bir kaliteli font ailesi,
   iyi satır aralığı (line-height), harf aralığı ayarlı. Ucuz siteler her yeri
   16px yapar; pahalı siteler kontrastı abartır.
2. **Boşluk (whitespace).** İçerik nefes alıyor. Bölümler arası büyük dikey
   boşluk, geniş kenar boşlukları. Boşluk = güven sinyali; "acele etmedik".
3. **Mikro-etkileşim.** Butona gelince yumuşak geçiş, link altı çizgisinin
   soldan sağa dolması, kart hover'da hafif kalkma/gölge, imleç değişimi.
   150–400ms, `ease` eğrili, asla sıçramayan.
4. **Scroll koreografisi.** İçerik scroll'la sahneye giriyor: yazı aşağıdan
   belirir, görsel maskeden açılır, sayılar sayar. Smooth scroll (Lenis)
   tekerlek hissini "sinematik" yapıyor — bu tek başına siteyi bir kademe yukarı
   çeker.
5. **Özel görsel dil.** Stok fotoğraf değil: gerçek iş görselleri, tutarlı
   renk gradasyonu/filtre, özel ikon seti, tek bir doku/arka plan imzası.
   Deeploico için: gerçek proje ekran görüntüleri + tutarlı çerçeveleme.
6. **Hız.** Lighthouse 90+; görseller optimize (WebP/AVIF, lazy load); font
   flash yok. Yavaş site pahalı hissettirmez, bozuk hissettirir.
7. **Grid disiplini.** Her şey görünmez bir ızgaraya oturuyor. Hizalar tutuyor,
   kenarlar aynı hatta. Bento grid (asimetrik modüler kartlar) 2026'nın
   hâkim düzeni.
8. **Bir imza anı.** Tek bir "vay" momenti — 3D obje, WebGL hero, dev tipografi
   animasyonu. Her yere değil, sadece bir yere. Gerisi sakin.

> Karşıt uç (ucuz görünme sebepleri): 16px her yer, dar boşluk, merkeze
> yığılmış içerik, template hero + stok fotoğraf, hover'sız butonlar, ani
> `display:none` geçişler, optimize edilmemiş 2MB PNG.

Kaynaklar: [Brand Vision — 2025 Website Cost Breakdown](https://www.brandvm.com/post/2025-website-cost),
[Fiverr — Website Design Costs 2025](https://www.fiverr.com/resources/guides/graphic-design/website-design-costs),
[SliderRevolution — Award-Winning Website Design](https://www.sliderrevolution.com/design/award-winning-websites/)

---

## 2. 2025–2026 ajans/portfolyo trendleri

- **Bento grid** — Japon bento kutusundan esinli asimetrik kart bloklarıyla
  içerik düzeni. Portfolyo ve "hizmetler" bölümü için ideal.
- **Dev tipografi** — hero'da 80–200px başlık, çoğu zaman tek kelime + alt satır.
- **Dark mode** varsayılan ya da toggle; koyu zemin + tek accent renk.
- **Dokulu minimalizm** — düz beyaz değil; kâğıt/grain dokusu, hafif noise,
  yumuşak gölge. "Sıcak minimal".
- **Motion & video** — hero'da sessiz döngü video, scroll-tetikli reveal,
  sayfa geçiş animasyonları (view transitions).
- **Hikâye anlatımı** — proje kartı değil, "vaka çalışması": problem → süreç →
  sonuç, dergi serimi gibi.
- **Retro-fütürizm / 3D imza anı** — tek bir yerde 3D obje veya WebGL, her yerde
  değil.
- **Performans + sürdürülebilirlik** — yalın kod, optimize görsel; hız artık
  tasarım kararının parçası.

Kaynaklar: [Envato — Portfolio design trends 2026](https://elements.envato.com/learn/portfolio-trends),
[Figma — Web Design Trends 2026](https://www.figma.com/resource-library/web-design-trends/),
[TheeDigital — Web Design Trends 2026](https://www.theedigital.com/blog/web-design-trends),
[Colorlib — Portfolio Design Trends 2026](https://colorlib.com/wp/portfolio-design-trends/)

---

## 3. Canlı örnek siteler (incele, hisset)

| # | Site | Neden iyi |
|---|---|---|
| 1 | [basement.studio](https://basement.studio/) | Koyu "tech studio" arketipinin ders kitabı: ince tipografi, ince çizgiler, ağır ama zarif animasyon, "işi olan mühendis" havası. **Yön B'nin referansı.** |
| 2 | [Obys Agency](https://obys.agency/) | Editöryel + deneysel: dev serif tipografi, cesur düzen bozmaları, güçlü görsel sistem. Hikâye anlatımı çok kuvvetli. **Yön A/C arası.** |
| 3 | [Locomotive (Montreal)](https://locomotive.ca/en) | Smooth scroll'u dünyaya yayan ajans (kendi kütüphanesini yazdılar). Sinematik scroll koreografisi nasıl olur, canlı örnek. |
| 4 | [Lusion](https://lusion.com/) | WebGL / 3D / akışkan geçişler, scroll'a bağlı sahne kurgusu. "İmza anı" trendinin uç örneği — Deeploico için ilham, birebir hedef değil. |
| 5 | [REJOUICE](https://rejouice.com/) | Awwwards ödül canavarı. Büyük tipografi + bol boşluk + minimal renk + kusursuz ritim. "Az ama pahalı" dengesi. **Yön A/C referansı.** |
| 6 | [Foundry (UK)](https://www.foundryuk.com/) | Galeri odaklı portfolyo: siyah-beyaz-gri palet, katı grid, minimalist zarafet. Sade ve profesyonel — düşük riskli hedef. **Yön A referansı.** |
| 7 | [David Langarica](https://www.davidlangarica.dev/) | Tek kişilik portfolyo ama "ajans seviyesi" hissettiren, dergi serimi gibi vaka çalışmaları. Deeploico'nun boyutuna en yakın gerçekçi hedef. |
| 8 | [Cuberto](https://cuberto.com/) | Oyunbaz imleç, büyük renkli tipografi, akıcı geçişler. **Yön C'nin referansı** — cesur, akılda kalıcı, marka gibi. |
| 9 | [Awwwards — Design Agencies galerisi](https://www.awwwards.com/websites/design-agencies/) | Sürekli güncel referans havuzu. Haftada bir 10 dakika bak, göz kalibre olur. |

**Akif için pratik izleme yöntemi:** her siteyi aç, sadece scroll et, "burada ne
oldu da hoşuma gitti?" diye not al. 3-4 site sonra hangi yöne çekildiğin belli olur.

---

## 4. GitHub repoları

### 4a. Şablon / başlangıç projeleri

| Repo | Yıldız | Ne işe yarar (Deeploico) |
|---|---|---|
| [onwidget/astrowind](https://github.com/onwidget/astrowind) | ~5.9k | Astro + Tailwind, 2022–2025 en çok yıldızlı Astro teması. Lighthouse 90+, SEO/sitemap/OG hazır. Deeploico'nun **iskelet + hız temeli** için birebir. Tasarımı sade — üstüne kendi görsel dilini giydirirsin. |
| [manuelalferez/astrofy](https://github.com/manuelalferez/astrofy) | ~1k+ | Astro + Tailwind kişisel portfolyo: Blog, CV, Proje bölümü, RSS hazır. CV sayfası ihtiyacını (Dashboard'da "CV sayfası" sırada) doğrudan karşılar. |
| [Ladvace/astro-bento-portfolio](https://github.com/Ladvace/astro-bento-portfolio) | ~380 | Astro + bento-grid tek sayfa portfolyo. Motion + GSAP + Lenis + Rive entegre. **Bento düzeni + animasyon stack'ini bir arada** görmek için canlı referans (birebir kopyalama, yapı öğren). |
| [Gothsec/Portfolio](https://github.com/Gothsec/Portfolio) | ~250 | Astro + React + TS + Tailwind, Figma ile elde tasarlanmış. Formspree ile çalışan iletişim formu (statik sitede backend'siz form çözümü) + temiz kod yapısı. |
| [JaumeGelabert/agency-template](https://github.com/JaumeGelabert/agency-template) | ~100+ | Next.js + Tailwind + React, açıkça "ajan sitesi" için yapılmış ücretsiz şablon. Bölüm kurgusu (hizmetler, süreç, ekip, CTA) için içerik iskeleti örneği. |
| [arthelokyo/astrowind](https://github.com/arthelokyo/astrowind) | fork | AstroWind'in Astro v7 + Tailwind v4 güncel forku. En yeni sürümle başlamak istersen. |
| [amnashanwar/awesome-portfolios](https://github.com/amnashanwar/awesome-portfolios) | ~3k+ | Yaratıcı portfolyo sitelerinin küratörlü listesi. İlham havuzu — "hangi yön" kararına yardımcı. |
| [emmabostian/developer-portfolios](https://github.com/emmabostian/developer-portfolios) | ~30k+ | Geliştirici portfolyoları listesi. Aynı amaç: göz kalibrasyonu. |

### 4b. Hareket / etkileşim kütüphaneleri

| Repo | Yıldız | Ne işe yarar |
|---|---|---|
| [darkroomengineering/lenis](https://github.com/darkroomengineering/lenis) | ~15.7k | Smooth (yumuşak) scroll. **Tek satır kurulumla** sitenin "sinematik" hissini bir kademe yükseltir. Yön B'nin bel kemiği, A ve C'de de kullanılır. |
| [GSAP (greensock)](https://github.com/greensock/GSAP) | ~20k | Endüstri standardı animasyon kütüphanesi. **2025'te Webflow ile %100 ücretsiz oldu** — SplitText, ScrollTrigger, MorphSVG dahil tüm eklentiler bedava, ticari kullanım serbest. Scroll reveal, metin animasyonu, sayaç — hepsi bununla. |
| [motion (eski Framer Motion)](https://github.com/motiondivision/motion) | ~27k+ | React/JS için deklaratif animasyon. Eğer stack React'e kayarsa (Astro içinde ada olarak) mikro-etkileşimler için en rahat API. |
| [withastro/astro](https://github.com/withastro/astro) | ~50k+ | Ana framework. Yerleşik **View Transitions** ile sayfa geçiş animasyonları JS'siz gelir. |
| [Codrops / tympanus demoları](https://tympanus.net/codrops/) | — | Repo değil ama: kopyala-yapıştır seviyesinde hero animasyonu, hover efekti, scroll reveal demoları. GSAP ücretsiz eklenti demoları burada. |
| [studio-freight örnekleri (darkroom)](https://github.com/darkroomengineering) | — | Lenis'i yazan ekip; başka scroll/animasyon yardımcıları ve gerçek proje örnekleri. |

---

## 5. Üç Somut Yön

### Yön A — "Editöryel Sükûnet"

- **Benzediği siteler:** Foundry, REJOUICE, David Langarica.
- **His / atmosfer:** Sakin, güvenli, "işini bilen". Bir mimarlık dergisi
  açmış gibi. Aceleye getirilmemiş.
- **Tipografi + renk:** Zemin krem/kırık beyaz (`#FAF9F6`), metin neredeyse
  siyah (`#1A1A1A`), tek accent (koyu yeşil ya da lacivert). Başlık: büyük
  serif (ör. Fraunces, Instrument Serif) 72–120px. Gövde: temiz sans (Inter).
- **Ana etkileşimler:** Scroll'la yazı aşağıdan yumuşak belirir; görseller
  maskeden açılır; link hover'da alt çizgi soldan dolar; smooth scroll (Lenis)
  hafif. Abartı yok, sadece incelik.
- **Yapım eforu (Faz 0 döngüsü):** **Düşük.** ~2 Sonnet kod lane (hero +
  vaka/proje bölümü) + 1 test + 1 gate. Placeholder görsellerle 1 referans koşu.
- **Risk:** Düşük. "Fazla sade / cılız" görünme tehlikesi — tipografi ölçeği ve
  boşluk cömert tutulmazsa etkisini kaybeder. Çözüm: kontrastı abart.

### Yön B — "Tech Studio"

- **Benzediği siteler:** basement.studio, Locomotive.
- **His / atmosfer:** Koyu, hassas, mühendislik. "Bu kişi hem tasarlar hem
  kodlar". Deeploico'nun yazılım + sektör harmanı anlatısına en yakın.
- **Tipografi + renk:** Zemin çok koyu (`#0B0B0C`), metin açık gri (`#E6E6E6`),
  tek canlı accent (elektrik mavisi / neon yeşil), ince ayraç çizgileri
  (`rgba(255,255,255,0.08)`). Font: geometrik sans (Geist, Söhne benzeri).
  Başlıklar orta-büyük, çok tight harf aralığı.
- **Ana etkileşimler:** Lenis smooth scroll belirgin; GSAP ScrollTrigger ile
  bölümler pinlenir, sayılar sayar, satırlar kelime kelime belirir (SplitText);
  kart hover'da ince kenar parlar; özel imleç (küçük nokta + hover'da büyür).
  Bir imza anı: hero'da hafif hareketli grid ya da tek 3D obje.
- **Yapım eforu:** **Orta.** ~3 kod lane (hero + animasyon katmanı + portfolyo
  grid) + test + gate. Animasyon lane'i biraz daha hassas — Opus'a gidebilir.
  Görseller Faz 1'de (Higgsfield) gerçek ağırlığını alır.
- **Risk:** Orta. Aşırı animasyon = yavaş + yorucu. Kural: her animasyon 400ms
  altı, `prefers-reduced-motion` desteği, mobilde animasyon azaltılır. Lighthouse
  90 altına düşerse kırp.

### Yön C — "Bold Creative"

- **Benzediği siteler:** Cuberto, Obys Agency.
- **His / atmosfer:** Cesur, enerjik, akılda kalıcı. Deeploico bir "ajans
  markası" gibi konuşur, freelancer gibi değil. En "10k dolar" görünen ama en
  riskli.
- **Tipografi + renk:** 1 zemin (beyaz ya da tek doygun renk — ör. sıcak
  turuncu / kobalt), dev display font (Clash Display, Boldonse) 120–220px,
  asimetrik bento grid, büyük yuvarlak köşeli kartlar. 2. accent renk vurucu.
- **Ana etkileşimler:** Oyunbaz büyük imleç (hover'da "VIEW" yazısına dönüşür);
  bento kartlar hover'da hafif eğilir/parallax; sayfa geçişleri renkli perde
  animasyonu; dev başlık scroll'la yatay kayar. Smooth scroll şart.
- **Yapım eforu:** **Yüksek.** ~3–4 kod lane + özel imleç + geçiş sistemi +
  test + gate. Muhtemelen 2 referans koşu. Görsel dil olmadan iskeleti bile
  "boş" durur — Higgsfield'a en çok ihtiyaç duyan yön.
- **Risk:** Yüksek. Cesur renk + dev tipografi kötü uygulanınca "amatör" ile
  "cesur" arasındaki çizgi ince. Tutarlı grid ve tek net konsept şart. Müşteri
  kitlesi (yapı kimyasalları KOBİ'leri) fazla "sanatsal" bulabilir — bu yön
  Deeploico'yu daha genç/yaratıcı müşteriye konumlar.

### Karşılaştırma

| | A — Editöryel | B — Tech Studio | C — Bold Creative |
|---|---|---|---|
| His | Sakin, güvenli | Hassas, mühendis | Cesur, enerjik |
| Zemin | Krem/beyaz | Çok koyu | Renkli/beyaz |
| Animasyon | Az, ince | Yoğun ama zarif | Oyunbaz, gösterişli |
| Efor (Faz 0) | Düşük | Orta | Yüksek |
| Risk | Düşük | Orta | Yüksek |
| Higgsfield ihtiyacı | Orta | Orta-Yüksek | Yüksek |
| Hedef müşteriye uyum | Yüksek (KOBİ güven) | Yüksek (yazılım anlatısı) | Orta (genç/yaratıcı) |

**Fable'ın önerisi:** **B ile başla, A'yı yedek tut.** B, Deeploico'nun "yazılım
+ sektör harmanı" hikâyesini görsel olarak anlatır ve en güçlü "pahalı ajans"
sinyalini verir; riski animasyon disipliniyle yönetilebilir. C'yi ikinci
müşteri projesi için sakla.

---

## 6. Stack Önerisi (Deeploico portfolyo sitesi)

**Katman:**

- **Framework:** [Astro](https://astro.build) + Tailwind CSS. Neden: HTML üretir,
  varsayılan sıfır JS, Lighthouse 90+ kolay, bileşen mantığı var ama React
  zorunlu değil. `standart-paket` zaten statik — aynı zihniyet.
- **Hareket:** [Lenis](https://github.com/darkroomengineering/lenis) (smooth
  scroll, ~15KB) + [GSAP](https://gsap.com) + ScrollTrigger + SplitText (2025'ten
  beri hepsi ücretsiz, ticari serbest). Gerekirse Astro **View Transitions** ile
  sayfa geçişi (ekstra kütüphane yok).
- **Görsel:** Faz 0 placeholder → Faz 1 Higgsfield. Format WebP/AVIF, Astro
  `<Image>` ile otomatik optimize.
- **Form:** Statik sitede backend yok → [Formspree](https://formspree.io) veya
  Web3Forms (ücretsiz kota). Gothsec/Portfolio bunu gösteriyor.
- **Font:** Değişken font, `woff2`, self-host (Google Fonts CDN değil — hız + gizlilik).

**GitHub Pages'e deploy:**

1. Ayrı repo: `regular07/deeploico` (veya mevcut `regular07.github.io` altına
   `/deeploico` yol — ilk adımda karar; ayrı repo daha temiz).
2. `astro.config.mjs` içinde `site` ve `base` ayarlanır (proje sayfası ise
   `base: '/deeploico'`).
3. `.github/workflows/deploy.yml` — Astro'nun resmi `withastro/action`'ı: her
   `main` push'unda build alır, `gh-pages`'e/Pages artifact'ına atar.
4. Repo Settings → Pages → Source: "GitHub Actions".
5. İlk "hello world" deploy'u canlı URL ile doğrulanmadan kod lane açılmaz
   (Yazılım Döngüsü kuralı: "gate GREEN olmadan lane spawn etme").

Bu yol `standart-paket` ile aynı altyapı ailesinde — yeni bir şey öğrenme
maliyeti düşük, mevcut git push izinleri geçerli.

---

## 7. Sonraki Adım

Akif döndüğünde:

1. **Yön seç.** Bölüm 3'teki 8 siteyi aç, scroll et, hangisine çekildiğini söyle.
   Fable'ın önerisi B (Tech Studio). Seçim 5 dakika.
2. **Fable ilk spec'i yazar** — en küçük dikey dilim: *"landing hero + hizmetler
   bento (3 kart) + 3 proje kartı + iletişim CTA, placeholder görsellerle,
   seçilen yönün tipografi/renk sistemiyle"*.
3. **Deploy yolu önce:** `deeploico` reposu + boş Astro + GitHub Actions +
   "hello world" canlı → URL doğrula.
4. **Onay #1** (spec özeti) → kod lane'leri (2–3 Sonnet) → test → gate →
   entegrasyon → **Onay #2** (önizleme) → deploy.
5. `Döngü-Log.md`'ye referans koşu kaydı. Konsol + Miro senkron.

**İlk somut hamle, yönden bağımsız:** `deeploico` GitHub reposu + Astro iskelet +
Actions deploy + canlı "hello world" URL. Bu her üç yön için de aynı; yön kararı
sadece tipografi/renk/animasyon katmanını etkiler, altyapıyı değil.

---

## Kaynak listesi

- [Brand Vision — 2025 Website Cost Breakdown](https://www.brandvm.com/post/2025-website-cost)
- [Fiverr — Website Design Costs 2025](https://www.fiverr.com/resources/guides/graphic-design/website-design-costs)
- [SliderRevolution — Award-Winning Websites](https://www.sliderrevolution.com/design/award-winning-websites/)
- [Envato — Portfolio Trends 2026](https://elements.envato.com/learn/portfolio-trends)
- [Figma — Web Design Trends 2026](https://www.figma.com/resource-library/web-design-trends/)
- [TheeDigital — Web Design Trends 2026](https://www.theedigital.com/blog/web-design-trends)
- [Colorlib — Portfolio Design Trends 2026](https://colorlib.com/wp/portfolio-design-trends/)
- [Wavespace — Best Website Design Examples](https://www.wavespace.agency/blog/best-website-design-examples)
- [Awwwards — Design Agencies](https://www.awwwards.com/websites/design-agencies/)
- [CSS-Tricks — GSAP is Now Completely Free](https://css-tricks.com/gsap-is-now-completely-free-even-for-commercial-use/)
- [Webflow Blog — GSAP 100% Free](https://webflow.com/blog/gsap-becomes-free)
- [Orpetron — 10 Award-Winning Design Agency Websites](https://orpetron.com/blog/10-award-winning-design-agency-websites-setting-the-standard/)
