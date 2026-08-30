---
connects: [sap-qm-kalite-kontrolde-kalan-stok-sorun-giderme, hammadde-sap-kalite-kontrol-formati]
sources: [import-2026-07-part-001.md]
created: 2026-08-28
updated: 2026-08-28
---

# SAP QM Kalite Kontrol Stok Sorun Giderme ↔ SAP QP02 Kalite Kontrol Formatı

## Bağlantı

QP02 formatı, bir hammaddenin hangi karakteristiklerde (elek analizi, nem, alt/üst sınır) kontrol edileceğini tanımlayan statik şablondur; ama bu şablonun arkasında bir muayene partisi (inspection lot) açılmazsa veya kısmi onaylanırsa, stok "kalite kontrolünde" görünmeye devam eder ve QP02 ekranında hiçbir kayıt bulunamaz. Sorun giderme süreci, bu iki durumu (doküman şablonu vs. gerçek sistem statüsü) ayırt edip kayıp stoğu bulmayı sağlar.

## Ana Fikir

Bir kalite kontrol formatının var olması, sistemde her zaman buna karşılık gelen aktif bir kayıt (muayene partisi) olduğu anlamına gelmez — format ile gerçek işlem geçmişi (hareket türleri, kısmi kullanım kararları) arasında sapma oluşabilir. Bu sapmayı bulmak, formatı bilmekten farklı bir beceri (SAP işlem ekranlarında iz sürme) gerektirir.
