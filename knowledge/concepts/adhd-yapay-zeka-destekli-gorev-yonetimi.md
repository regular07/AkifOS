---
title: ADHD İçin Yapay Zeka Destekli Görev Yönetimi
aliases: [ADHD Claude kullanımı, görev bölme, body doubling, şimdi ne yapmalıyım modu, Todoist planlama, Microsoft To Do Planner, prim görevleri takibi, beyin boşaltma kutusu]
tags: [uretkenlik, gorev-yonetimi, adhd, yapay-zeka, kisisel-sistem]
sources: [import-2026-07-part-002.md]
created: 2026-08-28
updated: 2026-08-28
---

# ADHD İçin Yapay Zeka Destekli Görev Yönetimi

ADHD'li bir kullanıcının yapay zeka (Claude) ve görev uygulamalarını birlikte kullanarak dikkat dağınıklığı, karar yorgunluğu ve "başlayamama" sorunlarını azaltmasına yönelik bir çalışma sistemi. Temel fikir: büyük ve belirsiz işleri küçük somut adımlara bölmek, her an tek bir görevi görünür kılmak, kararları sınırlı seçeneğe indirmek ve aklına geleni anında dışarı yazıp sonra düzenlemek. Görev takibi için Claude'a bağlı olan Todoist pratik bir seçenektir.

## Önemli Noktalar

- **Görev bölme:** büyük hedefleri ("EN 12004'ü bitir") yapay zekaya 15–20 dakikalık alt görevlere böldürüp doğrudan görev listesine ekletmek; tek seferde büyük işle uğraşmak yerine küçük adımlarla ilerlemek yorgunluğu azaltır.
- **Karar yorgunluğunu devretme:** birden çok seçenek arasında sıkışınca "3 seçenek sun, birini öner" demek; sonsuz analiz yerine sınırlı bir karar noktasına gelmek.
- **"Şimdi Ne Yapmalıyım?" tek görev modu:** uzun liste yerine ekranda tek bir görev; "şimdi değil, sıraya al" ile suçluluk duymadan atlama; en üstte kategori/tarih düşünmeden tek satır yazılan hızlı not (beyin boşaltma) kutusu — düşünceyi kaybetmeden kafadan çıkarmak.
- **Body doubling / hesap verebilirlik:** bir işe otururken yapay zekaya "şimdi X'i yapıyorum" deyip ilerlemeyi paylaşmak; konuşma başına tek odak tutmak (projeler karışmasın).
- **Araç seçimi:** Todoist (Claude'a bağlı, doğal dil giriş, P1–P4 öncelik, tarih bazlı otomatik "Bugün/Yarın/Bu Hafta" gruplama, alt görev). Jira'ya en yakın Microsoft ürünü Planner (kanban); backlog/sprint isteyene Azure DevOps ama tek kişiye fazla; basit checklist için Microsoft To Do. Sayaçlı işler için ilerleme çubuğu/adım kullanılır.

## Detaylar

Kurum bağlamında somut uygulama: yıllık prim için Ağustos'a kadar 5 SMAT + 5 TF5 + 10 saha stok kontrolü girişi gerekiyordu. Bunlar tek bir görevin altına 1–2–3 adımları olarak veya sayaçlı görev olarak takip edilir. Hiç başlanmamış iş (TF5), süre daralınca en çok sıkıntı yarattığı için önceliklendirilir; aciliyeti yüksek ama önemi düşük işler (laboratuvar denemesi) tarih yakınlığına göre listede yükselir ama önem rengiyle ayrışır. Liste "yaklaşan gün/tarih + önem" sırasına göre tutulur, saatlik plan yapılmaz.

Sınırlamalar: şahsi Microsoft hesabı (@outlook.com vb.) Claude'a bağlanamaz — bağlantı yalnızca iş/okul (Microsoft Entra) hesaplarını destekler ve bağlansa bile yalnızca arama sunar, To Do/Planner'da görev oluşturma/yönetme yoktur. Todoist'in ücretsiz planında `deadline` alanı kilitlidir; normal "due date" ile çalışılır. Kişiye özel bir "sabah başlangıç" skill'i (skill-creator ile) her sabah görevleri çekip önceliklendirip tek bir "şimdi buna başla" önerisi verecek şekilde kurulabilir.

## İlgili Kavramlar

- [[deneme-uretimi-alternatif-hammadde-recete-degisikligi]] — Laboratuvar denemesi, prim görevleri ve standart sunumu aynı anda yürüyen iş hatlarıdır; bu görev sistemi onları tek listede önceliklendirmek için kurulmuştur.
- [[multi-ai-agent-orkestrasyonu]] — Her ikisi de işi yapay zekaya devredilebilir küçük adımlara bölme fikrini paylaşır; orada ajanlar arası iş devri, burada kullanıcı–yapay zeka arası görev bölme söz konusudur.
- [[inbox-dump-hizli-gorev-yakalama]] — Buradaki "beyin boşaltma kutusu"nun dosya sistemi düzeyindeki uygulamasıdır; tarih önekli tek dosyayla anında yakalama yapılır.
- [[termin-tarihli-gorev-yakalama]] — Listenin "yaklaşan tarih + önem" sıralaması, tam da teslim tarihli görevlerin doğru zamanda yüzeye çıkması için kuruludur.

## Kaynaklar

- import-2026-07-part-002.md
