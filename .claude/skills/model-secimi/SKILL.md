---
name: model-secimi
description: Akif'in "hangi işte hangi model" kararını kendisi vermek zorunda kalmaması için — büyük/yeni bir iş başladığında görev türünü analiz edip doğrudan hangi modele geçmesi gerektiğini (ve tam komutu) söyler. Alt-ajan (subagent) dağıtımında ise model seçimini otomatik yapar, kullanıcıya sormaz. "hangi model", "model seç", "bunun için hangisi" gibi ifadeler geçtiğinde ya da yeni büyük bir görev başlarken kullan.
---

# Model Seçimi — Akif İçin Otomatik Karar

Akif yazılım/AI bilgisi az olduğu için "hangi işte hangi model kullanılır" kararını
kendisi vermek istemiyor — bu karar HER ZAMAN Claude tarafından verilmeli, kullanıcıya
"hangi model istersin" diye sorulmamalı.

## Elindeki modeller (Akif'in erişimi olan)

- **Fable 5** — en güçlü, en pahalı. Mimari/büyük karar.
- **Opus 5** — güçlü, araştırma/analiz için.
- **Sonnet 5** — dengeli, günlük iş için varsayılan.
- **Haiku 4.5** — en hızlı/ucuz, rutin/otomasyon işleri için.

## Karar Tablosu

| Görev türü | Model | Belirti/anahtar kelimeler |
|---|---|---|
| Mimari planlama, marka/isim kararı, büyük stratejik seçim, "nasıl kurulsun" soruları | **Fable** | "plan yapalım", "nasıl olsun", isim/marka/kimlik kararları |
| Derin araştırma, kod/sistem anlama, "bu nasıl çalışıyor" | **Opus** | "incele", "araştır", "analiz et", bilinmeyen bir sistemi öğrenme |
| Günlük iş, orta karmaşıklıkta görev, çoğu konuşma | **Sonnet** (varsayılan) | özel bir işaret yoksa buradan başla |
| Basit/rutin/tekrarlayan iş, özetleme, şablon kopyalama, arka plan otomasyonu | **Haiku** | günlük özet, basit düzenleme, "sadece şunu yap" |

**Temel kural:** Pahalı model sadece DÜŞÜNSÜN (karar/analiz), rutin iş ucuz modele gitsin.

## İKİ FARKLI UYGULAMA YOLU (bunları karıştırma)

### 1. Ana konuşma modeli (Akif'in terminalde kullandığı model)
Claude Code'da model `/model <isim>` komutuyla değiştirilir — bunu SADECE Akif kendi
terminalinde yazabilir, Claude bunu onun yerine çalıştıramaz. O yüzden görev:

**Yeni, büyük/farklı türde bir iş başladığında (mimari karar, derin araştırma vb.)
Akif'e otomatik olarak söyle:** "Bu iş için `/model fable` yazıp geçersen daha iyi olur"
gibi net, tek satırlık bir öneri ver — neden sorma, direkt söyle. Rutin işlerde hiçbir
şey söyleme, mevcut modelle devam et (gereksiz kesinti Akif'in DEHB'si için kötü).

### 2. Alt-ajan (subagent) dağıtımı — Agent tool ile
Bir alt görevi Agent tool ile bir subagent'a devrederken, `model` parametresini karar
tablosuna göre SEN (Claude) otomatik seç — Akif'e hiç sorma, bu tamamen görünmez
çalışmalı. Örnek: derin bir kod incelemesi subagent'a veriliyorsa `model: "opus"` ver.

**Kritik kural — sessiz miras bırakma:** Ana konuşma pahalı bir modeldeyken (Fable/Opus)
Agent tool çağrısında `model` parametresi boş bırakılırsa, alt-ajan da aynı pahalı modeli
miras alabilir. Bu yüzden ana model pahalıysa `model` parametresini HER ZAMAN açıkça
ucuz bir katmana ayarla (Sonnet/Haiku), asla boş bırakıp mirasa güvenme. Gerçekten
yargı gerektiren nadir bir alt görev varsa bilinçli olarak pahalı modeli seç, ama bu
istisna olmalı, varsayılan değil.

**Devretme de bedava değil:** Limitler/kota sağlıklıyken ve iş küçükse, ana döngünün
işi kendisi elle yapması subagent'a devretmekten daha ucuz olabilir — devretme kendi
context/koordinasyon maliyetini taşır. Sadece iş gerçekten paralelleştirilebilir,
büyük veya bağlamdan izole edilebilirse devret.

## Nasıl Davranmalı
- Akif'e asla "hangi modeli istersin" diye SORMA — bu onun tam kaçınmak istediği şey.
- Görev türünü kendin analiz et, kararı sen ver, sonucu bildir.
- Ana konuşma modeli değişikliği gerekiyorsa tek cümlelik net öneri (`/model X`), tartışmaya açma.
- Emin değilsen varsayılan Sonnet'te kal, gereksiz model değişikliği önerme.
