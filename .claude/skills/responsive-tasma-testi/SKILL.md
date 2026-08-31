---
name: responsive-tasma-testi
description: Bir web sitesinde mobilde yatay kaydırma / "sağdan boşluk" / taşma şikayeti geldiğinde tahmin etmeden, ölçerek teşhis koyar ve bilinen 4 sebebi sırayla kontrol eder. "sağa sola scroll atıyor", "mobilde kısılıyor", "sağdan boşluk kalıyor", "responsive bozuk" gibi ifadeler geçtiğinde kullan.
---

# Responsive Yatay Taşma Testi

Web sitesi/landing page mobilde "sağa sola kayıyor", "sağdan boşluk var", "küçültünce
bozuluyor" gibi bir şikayet geldiğinde bu skill'i çalıştır. Amaç: CSS'te rastgele deneme-
yanılma yapmadan, ÖLÇEREK gerçek sebebi bulmak.

Detaylı arka plan bilgisi için: [[responsive-yatay-tasma-teshis-ve-cozum]]
(`knowledge/concepts/responsive-yatay-tasma-teshis-ve-cozum.md`)

## Adım 1 — Kesin Teşhis (tahmin etme, ölç)

Chrome uzantısı (`claude-in-chrome`) ile canlı siteyi aç, aşağıdaki JS'i çalıştır:

```js
JSON.stringify({
  innerWidth: window.innerWidth,
  docScrollWidth: document.documentElement.scrollWidth,
  overflowMiktari: document.documentElement.scrollWidth - window.innerWidth
})
```

- `docScrollWidth === innerWidth` ise taşma YOK — kullanıcı büyük ihtimalle tarayıcı
  cache'i görüyor, Adım 5'e (cache) atla.
- `docScrollWidth > innerWidth` ise gerçek taşma var, miktarı not al, Adım 2'ye geç.

## Adım 2 — Taşan Elemanı Bul

```js
var offenders = [];
document.querySelectorAll('*').forEach(function(el) {
  var r = el.getBoundingClientRect();
  if (r.right > window.innerWidth + 1) {
    offenders.push({tag: el.tagName, cls: el.className, right: Math.round(r.right)});
  }
});
JSON.stringify(offenders.slice(0, 20))
```

Çıktıdaki class isimlerinden hangi bileşenin (slider, navbar, kart grid'i vb.) sorumlu
olduğunu belirle.

## Adım 3 — Bilinen 4 Sebebi Sırayla Kontrol Et

1. **`box-sizing: border-box` var mı?** Hem projenin kendi CSS dosyasında hem
   (framework kullanılıyorsa) CDN'e bağımlı kalmadan tanımlı mı? Yoksa ekle:
   ```css
   *, *::before, *::after { box-sizing: border-box; }
   ```

2. **`html` VE `body` ikisinde birden `overflow-x: hidden` var mı?** Sadece body'de
   olması teorik olarak yeterli olsa da pratikte güvenilmez — ikisine de ekle:
   ```css
   html, body { overflow-x: hidden; width: 100%; }
   ```

3. **Taşan eleman `position: fixed` bir kutunun İÇİNDE mi?** (navbar, floating buton vb.)
   Fixed elemanlar `body`'nin overflow klibinden muaf olur. O elemanın KENDİSİNE ayrıca
   ekle:
   ```css
   #navbar-veya-fixed-eleman { overflow-x: hidden; max-width: 100vw; }
   ```

4. **Taşan eleman flex/grid içinde bir metin/input mu?** `min-width: 0` ekle (flex
   item'ların varsayılan `min-width:auto` davranışı büzülmeyi engelleyip taşmaya sebep
   olabilir).

## Adım 4 — Düzelt, Commit Et, Deploy Bekle

Düzeltmeyi yap, commit mesajında hangi sebebi (1-4'ten hangisi) düzelttiğini belirt.
GitHub Pages kullanılıyorsa deploy'un bitmesini bekle:

```bash
until curl -s "https://KULLANICI.github.io/REPO/style.css" | grep -q "ARANAN-KURAL"; do sleep 5; done
```

## Adım 5 — Cache Kontrolü (tahmin ETME, kanıtla)

Kullanıcı "hala düzelmedi" derse önce SUNUCUDAKİ dosyayı kontrol et — kodun gerçekten
yanlış mı yoksa tarayıcı cache'i mi eski gösteriyor, ayırt et:

```bash
curl -s "https://KULLANICI.github.io/REPO/style.css?nocache=$(date +%s)" | grep "ARANAN-KURAL"
```

Sunucu doğruysa: `style.css?v=N` cache-busting parametresini bir artır, kullanıcıya
gizli sekmede test etmesini söyle.

## Adım 6 — Canlıda Doğrula (varsayma, kanıtla)

Deploy bittikten sonra Adım 1'i TEKRAR çalıştır (cache-busting query param'lı URL ile,
`?nocache=timestamp`), `docScrollWidth === innerWidth` eşitliğini görmeden "düzeldi"
deme.

## Bilinen Çelişki: html'de overflow-x vs position:fixed bug'ı

Eski mobil tarayıcılarda (özellikle eski iOS Safari) `html` elementine overflow
tanımlamak `position:fixed` elemanların yanlış konumlanmasına (örn. navbar'ın sayfa
ortasında asılı kalması) sebep olabilir. Çözüm ikisini birden yapmak, çelişmez:
`html`+`body`'ye `overflow-x:hidden` KOY, AYRICA her fixed elemanın kendi üzerine de
`overflow-x:hidden; max-width:100vw` koy (Adım 3.2 ve 3.3).

## İlgili
- [[responsive-yatay-tasma-teshis-ve-cozum]] — bu skill'in dayandığı kavram makalesi, daha fazla arka plan ve örnek için.
