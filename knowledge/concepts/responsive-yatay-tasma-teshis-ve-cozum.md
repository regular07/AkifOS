---
title: Responsive Sitede Yatay Taşma (Horizontal Scroll) Teşhis ve Çözüm
aliases: ["yatay scroll sorunu", "sağdan boşluk", "mobil taşma", "horizontal overflow"]
tags: ["css", "responsive", "debugging", "web-tasarim", "mobil"]
sources: ["standart-paket reposu — 2026-08-30/31 oturumu"]
created: 2026-08-31
updated: 2026-08-31
---

# Responsive Sitede Yatay Taşma (Horizontal Scroll) Teşhis ve Çözüm

Bir web sitesinde mobilde "sağa sola kaydırılabiliyor", "sağdan boşluk kalıyor" gibi
şikayetlerin kök nedeni neredeyse her zaman aynı ailedendir: bir eleman viewport
genişliğini aşıyor ve tarayıcı bunu yatay scrollbar'a çeviriyor. Sorun genelde tahminle
değil, ölçerek bulunur.

## Kesin Teşhis Yöntemi (tahmin etmeden)

Tarayıcı konsolunda/JS ile şu iki değeri karşılaştır — eşit değillerse taşma kanıtlanmış
olur:

```js
document.documentElement.scrollWidth   // gerçek içerik genişliği
window.innerWidth                       // görünür viewport genişliği
```

Hangi elemanın taştığını bulmak için tüm DOM'u tara:

```js
document.querySelectorAll('*').forEach(el => {
  const r = el.getBoundingClientRect();
  if (r.right > window.innerWidth + 1) console.log(el, r.right);
});
```

Bu iki adım, "hangi CSS kuralı taşmaya sebep oluyor" sorusunu dakikalar içinde
kesinleştirir; aksi halde CSS'te rastgele deneme-yanılma yapılır.

## En Sık Rastlanan 4 Sebep

1. **`box-sizing` eksikliği** — Varsayılan `content-box` modelde `width:%100` + `padding`
   eklendiğinde padding genişliğin ÜSTÜNE eklenir, kutu taşar. Çözüm:
   `*, *::before, *::after { box-sizing: border-box; }` — hem kendi CSS dosyasında hem
   (eğer bir framework/CDN'e güveniliyorsa) ekstra güvenlik için ayrıca tanımla; CDN
   yüklenemezse (yavaş ağ, engelleyici) framework'ün kendi reset'i devre dışı kalır.

2. **`html`+`body` ikisine birden `overflow-x:hidden` gerekir, sadece body yetmez.**
   CSS spec'ine göre `html`'in overflow'u `visible` ise `body`'nin overflow'u viewport'a
   "propagate" edilmesi gerekir, ama bu her tarayıcı/durumda güvenilir çalışmıyor.
   Sadece `body`'ye koymak teorik olarak yeterli olsa da, pratikte gerçek taşmayı
   engellemeyebiliyor — canlı ölçümle (`scrollWidth` testi) doğrulandı.

3. **`position: fixed` elemanlar, ebeveynin `overflow:hidden`'ından muaf.** Fixed
   elemanlar viewport'a göre konumlanır, normal akıştaki ebeveyninin klip kutusunun
   "dışında" sayılır. Yani `body{overflow-x:hidden}` bir navbar'ın (fixed) İÇİNDEKİ
   taşmayı klipleyemez — o navbar'ın kendi üzerine ayrıca `overflow-x:hidden` (ve
   gerekiyorsa `max-width:100vw`) koymak gerekir.

4. **Flex/grid öğelerinin `min-width:auto` varsayılanı.** Bir flex item içeriği
   büzülmeye izin vermeyip konteynerden taşabilir. `min-width:0` bu varsayılanı ezer ve
   öğenin gerçekten küçülebilmesini sağlar (özellikle navbar brand metni, arama kutuları
   gibi metin ağırlıklı öğelerde kritik).

## Çelişkili Kural: `html`'de overflow vs `position:fixed` bug'ı

Bazı eski mobil tarayıcılarda (özellikle eski iOS Safari) `html` elementine overflow
tanımlamak, `position:fixed` elemanlar için yeni bir "containing block" yaratıp onların
viewport yerine yanlış bir kutuya göre konumlanmasına (ör. sayfa ortasında asılı kalma)
sebep olabiliyor. Bu, "html'e overflow-x:hidden koyma" tavsiyesiyle doğrudan çelişir.

**Pratik çözüm — ikisini birden uygula, çelişmeden:**
- `html` VE `body`'ye `overflow-x:hidden` koy (taşma sorununu kökten çözer, modern
  tarayıcılarda bu bug artık nadir).
- Fixed pozisyonlu her elemana (navbar, floating buton vb.) AYRICA kendi üzerinde
  `overflow-x:hidden; max-width:100vw` ekle — bu, olası eski-tarayıcı bug'ına karşı
  bağımsız bir güvenlik katmanı olur, `html`'deki kuralla çakışmaz.

## Yardımcı Pratikler

- **Grid'lerde sabit px matematiği yerine `repeat(auto-fit, minmax(min(100%, Npx), 1fr))`
  kullan** — manuel `calc(33% - Xrem)` hesapları round-off hatasıyla kolayca taşar.
  `min()` fonksiyonu içerik hiçbir zaman konteynerden büyük olamayacağını garantiler.
- **Kasıtlı yatay kaydırma (carousel/slider) ile kazara taşmayı ayır.** Bir slider'ın
  kendi `overflow-x:auto` olması sorun değil — konteynıra hapsedilmiş, sayfa geneline
  sızmıyor olması yeterli (yukarıdaki teşhis testiyle doğrula).
- **`background-attachment: fixed` (parallax hero) mobilde performans/uyumluluk sorunu
  yaratır** (özellikle iOS Safari) — `@media (max-width: 768px)` ile `scroll`'a
  düşürülmeli.
- **CSS cache-busting**: `style.css?v=N` gibi bir versiyon parametresi, her önemli
  değişiklikte tarayıcının eski dosyayı cache'ten sunmasını engeller. Kullanıcı "hala
  düzelmedi" dediğinde çoğu zaman gerçek sebep budur — canlı sunucudaki dosyayı `curl` ile
  doğrudan kontrol etmek, tarayıcı cache'i ile gerçek kod farkını ayırt eder.

## İlgili Kavramlar
- [[github-pages-ile-statik-site-yayinlama]] — Bu teşhis süreci GitHub Pages'te yayınlanan
  bir kafe sitesi (standart-paket reposu) üzerinde uygulandı.
- [[landing-page-freelance-pazarlama-stratejisi]] — Responsive kalite, freelance demo
  linklerinin müşteriye güven vermesi için kritik.

## Kaynaklar
- standart-paket reposu — 2026-08-30/31 oturumu (navbar/hero/slider taşma sorunlarının
  adım adım teşhisi ve çözümü)
