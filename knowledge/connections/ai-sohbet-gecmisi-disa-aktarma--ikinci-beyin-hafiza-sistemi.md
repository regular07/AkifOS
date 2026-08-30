---
connects: [ai-sohbet-gecmisi-disa-aktarma, ikinci-beyin-hafiza-sistemi]
sources: [import-2026-08-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

## Bağlantı

İkinci beyin sistemi normalde yalnızca kurulumdan sonraki oturumları hatırlar; kurulumdan önceki aylarca birikmiş sohbet geçmişi dışarıda kalır. Platform export'ları (Claude.ai Privacy → Export data, ChatGPT Data Controls, Gemini için Google Takeout) bu boşluğu kapatan girdi kaynağıdır: `geçmiş import` skill'i indirilen zip/json'u yerel olarak sistemin günlük log formatına çevirir.

## Ana Fikir

Dışa aktarma ile hafıza sistemi arasındaki köprü tamamen yereldir — export dosyası kullanıcının kendi e-postasına gelir, `geçmiş import` onu hiçbir yere yüklemeden `daily/` loglarına dönüştürür, `compile.py` de bunları kalıcı kavram makalelerine derler. Böylece "ikinci beyin" sadece ileriye değil geriye doğru da doldurulabilir; sistemin değeri, ne kadar geçmiş bağlamı içselleştirebildiğiyle orantılı artar.
