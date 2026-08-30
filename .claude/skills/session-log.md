---
name: session-log
description: Oturum mesajlarını saatli transkript olarak kaydet
---

# Session Log — Saatli Transkript

Her mesajı timestamp'li şekilde kaydeder. Sabah "saat 12'de ne konuştuk?" diye sorabilirsin.

## Kullanım

```
/session-log
```

Şu anki oturum transcript'ini `daily/YYYY-MM-DD-transcript.md` dosyasına yazar:

```
2026-08-28 | 21:45 | Dündar: "Otomatik derleyici kuruldu"
2026-08-28 | 21:46 | Akif: "Akşam 22 ve sabah 11'de derleyici çalışsın"
2026-08-28 | 21:47 | Dündar: "Tamam. Mutfağa git!"
```

Sonra sabah açıldığında:
- "Saat 21:45'te ne konuştuk?" → Transkript'te bulunur
- "Şunlar olmuştu dediğimde doğru mu?" → Saatler ile verify edilebilir

## Otomatik Çalışma

Oturum sonunda derleyici (`compile.py`) otomatik çalıştırılıp transcript kaydedilir.
