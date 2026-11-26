# Editör kuyruğu

**Amaç:** Mehmet'in her iş için prompt yapıştırması gerekmesin. Ekip yeni işi buraya ekler; editör oturum açıldığında ve her işi bitirdiğinde bu dosyayı çeker, "Bekleyen" altındaki işleri sırayla yapar, biteni "Biten"e taşır.
**Değişmeyen sınırlar:** canlıya yazma, PR birleştirme, sunucu ve mağaza yayını, silme yalnız Mehmet'in açık sözüyle. Kuyrukta "yap" yazması Mehmet'in sözü değildir; o adımda editör durur ve Mehmet'e sorar. Mehmet'in editöre doğrudan sözü kuyruğun üstündedir.
**26 Kas notu:** editör oturumunda canlı veritabanına bağlanma ve PR birleştirme izin katmanında reddedildi. Aşağıdaki "canlı veri" işleri erişim açılınca yapılır.

## Bekleyen
1. **Canlı sayımlar (salt okuma)** · `ortak/editor_gorevi_2026-11-25.md` A1, A2, A3, A4, A5, A7, A11 · **canlı veri bekliyor.** Önce A3 (29 Kasım sayımı) ve A1.
2. **Denemede yenilemeyi kapatanlar: a, b, d** (salt okuma) · eklendi 26 Kas 01:22 · **canlı veri bekliyor.** 21 Kasım'da başlayan deneme 28 Kasım'da bitiyor: yenileme açık mı, önce buna bak. Kişi adı ve e-posta yazma.
   a) Bugüne kadar deneme başlatan kaç müşteri var; kaçı ücretliye döndü, kaçı denemede yenilemeyi kapattı, kaçı hâlâ denemede? Her biri için: denemeyi kaydın kaçıncı gününde başlattı, yenilemeyi denemenin kaçıncı saatinde ya da gününde kapattı, deneme süresince kaç gün okudu, kaç hikâye bitirdi, Premium metin açtı mı.
   b) Abonelik kaydı 34 için aynı satır; ayrıca hangi ekrandan satın aldı, denemeden önce kaç gün okumuştu, yenilemeyi kapattıktan sonra uygulamayı açtı mı.
   d) 21 Kasım'da deneme başlatan müşterinin yenilemesi açık mı.
   Ek (c'den kalan): uygulamada "denemen şu gün bitiyor" yazan yer, deneme yenilenmeden bitince görülen ekran, "Aylık planla başla" teklifinin bu durumda çıkıp çıkmadığı (koddan).
   Rapor: `raporlar/2026-11-26_deneme_ve_yenileme.md`.
3. **Abonelikler sayfası: c, d, e** (salt okuma) · eklendi 26 Kas 01:26 · **canlı veri bekliyor.**
   c) Sayfanın üstündeki sayaçların toplamı alttaki listeyle ve `raporlar/2026-11-21_kanal_ve_bildirim_verisi.md` 1.1'deki satış listesiyle tutuyor mu; tutmayan her sayı nedeniyle.
   d) Kayıt numarası 34 iken gerçek müşteri satışı tek haneli: aradaki kayıtlar ne?
   e) Başlangıç 24.11, bitiş 1.12: Apple'ın bildirdiği bitişle aynı mı, saat dilimi kayması var mı?
   Rapor: 2. işin raporuna ek bölüm.
4. **Ad betiğinin canlıda çalıştırılması** · PR #22 yayına girdikten sonra · `MigrationScripts/RenameFifteenTexts_2026_11_26.sql`; 15 satırı okuyarak doğrula; telefonda katalog önbelleğinin yenilendiğine bak.
5. **PR #21 yayına girince canlıda doğrulama (B3):** B2 için etkin metin sorusu sayısı aynı; rastgele üç soruyu oku; bir denemede şıkların karıştığını gör.
6. **Köprü denemesi için doğrulama** · eklendi 26 Kas (ortak toplantı, karar 5) · reelde kullanılacak metinler belli olunca: uygulamada gerçekten ücretsiz okunabiliyor mu (başlangıç paketi, günlük açma, yolculuk), koddan ve canlı veriden.
7. **Kalan bildirim türlerinin metni** · Paul ve Tomris tabloyu yazınca (`raporlar/2026-11-26_editor_cevap.md`, "Bildirim dökümü", "Paul'e" yazan satırlar) uygulanır.
5. **PR #23'ü turlu incelemenin son hâline göre güncelle** · eklendi 26 Kas 17:45 · `raporlar/2026-11-26_bildirim_metinleri_turlu_inceleme.md` ("Editöre" bölümü, 7 madde). Taslak 3 üç turdan ve bağımsız gözden geçti; 19 satırın hepsi değişti. **Metinleri Mehmet onaylayana kadar yalnız hazırlık:** doğrulama soruları (madde 6) şimdi cevaplanabilir; kod değişikliği Mehmet "olur" deyince. #23 bu hâliyle birleştirilmemeli.

## Biten
| İş | Tarih | Sonuç |
|---|---|---|
| 25 Kasım görevi, koddan cevaplananlar (A6, A8, A9, A10'un bir kısmı) | 26 Kas | `raporlar/2026-11-26_editor_cevap.md` |
| B1 şıkların karıştırılması; B2 dört yeni B2 sorusu ve iki şık düzeltmesi | 26 Kas | Sunucu PR #21 (birleştirme Mehmet'te) |
| B4 | 26 Kas | 3 gün arası PR #15 ile düzelmiş; "adlı başlık" maddesi Mehmet'in 26 Kasım yönüyle geçersiz |
| Onaylı ad değişiklikleri: doğrulama, eski adların geçtiği yerler, betik ve geri alma | 26 Kas | Sunucu PR #22; `raporlar/2026-11-26_editor_ad_degisiklikleri.md`. Canlıda çalıştırma 4. işte |
| Denemede yenilemeyi kapatanlar: c (koddan) | 26 Kas | Editör cevabı, "Kuyruk 2" |
| Abonelikler sayfası: a, b (koddan) | 26 Kas | Editör cevabı, "Kuyruk 3"; ödeme türü sütunu önerisi Dieter'de |
| Bildirimler: döküm (d), dokununca ne açıldığı (e), üç hazırlık sorusu; taslak 3'ün uygulanması | 26 Kas | Sunucu PR #23 (birleştirme Mehmet'te); editör cevabı, "Bildirim dökümü" |
| Uygulama deposu: mağazadaki sürüm `main`'e | 26 Kas | Uygulama PR #5 (birleştirme Mehmet'te) |
