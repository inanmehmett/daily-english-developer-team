# Editör raporu: onaylı ad değişiklikleri (15 metin)

**Tarih:** 26 Kasım 2026 · **Görev:** `ortak/editor_gorevi_2026-11-26_ad_degisiklikleri.md`
**Durum: canlıda uygulandı (26 Kas 17:52).** Sunucu [PR #22](https://github.com/inanmehmett/DailyEnglish/pull/22) birleşti ve yayına girdi (17:48); ardından betik canlıda çalıştırıldı. 15 satır güncellendi: 10 İngilizce ad, 13 Türkçe ad; adres (`Slug`) hiçbirinde değişmedi; başka hiçbir metne dokunulmadı. Önceki adlar `_Backup_ReadingTextNames_2026_11_26` tablosunda (15 satır). Web ana sayfası yeni adı gösteriyor.

## Doğrulama soruları
Cevaplar yerel veritabanındaki metinlerden; canlıdaki metinle aynı olduğu varsayıldı.
| # | Soru | Cevap |
|---|---|---|
| 1 | 1016: gece bölümü var mı? | Yok. Metin "On the morning of 30 June 1908" diye açılıyor; "night" ya da "evening" geçmiyor. Yeni ad metinle uyumlu |
| 2 | 1020: üç onay, biri vermedi; nükleer açık mı? | Evet. "On B-59 there were three", "He had done nothing except refuse to sign", "B-59 carried a nuclear torpedo" |
| 3 | 1059: Amazon geçiyor mu? | Evet. "a town on the edge of the Amazon rainforest" |
| 4 | 1061: terzi, buzla kaplı ada? | Evet. "hired for fifty dollars a month to sew fur clothing", "its seamstress", "a mountain of ice and stone in the Arctic Ocean" |
| 5 | 1055: süre kasırgadan sonra mı sayılıyor? | Evet. "Forty-one days after the wave"; fırtına için "one of the strongest hurricanes recorded". Not: metin olayı çoğunlukla "storm" diye anıyor, "hurricane" bir kez geçiyor |
| 6 | Eski adlar başka nerede? | Aşağıda |
| 7 | Room 214, 7. bölüm | "boathouse" ilk beş bölümde geçmiyor, ilk kez 6. bölümde geçiyor. 7. bölümün Türkçe adı ("Kayıkhanedeki Kardeş") katalogda görünüyorsa kardeşin yerini erken söyler. Bölümler baştan sona okunmadı; kelime sayımıyla bakıldı |

## Eski adların geçtiği yerler
| Yer | Bulgu | Yapılan |
|---|---|---|
| Web ana sayfası (`Views/WebHome/Index.cshtml`) | "The Island Where Rabbits Won / Haritadan Silinen Ada" elle yazılı | PR #22'de yeni adla değişti |
| Başka metinlerin merak cümlesi, bitiş cümlesi, açıklaması | Eski adların hiçbiri geçmiyor (yerel veri) | – |
| Bildirim metinleri | Ad veritabanından okunuyor; elle yazılı ad yok | – |
| Uygulama kodu ve gömülü dosyalar | Geçmiyor | – |
| Eski içerik betikleri ve belgeler (`MigrationScripts`, `Docs`) | Geçiyor; tarihsel kayıt | Dokunulmadı |
| Mağaza görselleri ve açıklaması | Bakılmadı (konsol gerekir) | – |
| İngilizce alt adlar (`SubtitleEN`) | Canlıdaki değerler "Kalan" bölümünde | Dokunulmadı; Tomris'e |

## Betik
- `MigrationScripts/RenameFifteenTexts_2026_11_26.sql`: yalnız `Title` ve `SubtitleTR`; adres (`Slug`) değişmez. Eşleşme adresle; 15 satırın tamamı bulunmazsa hiçbir şey yazmaz. Önceki adlar `_Backup_ReadingTextNames_2026_11_26` tablosuna alınır. İki kez çalıştırmak bir şey değiştirmez.
- `MigrationScripts/RenameFifteenTexts_2026_11_26_REVERT.sql`: adları yedekten geri yazar.
- Yerelde denendi: uygula (15 satır), yeniden uygula (değişiklik yok), geri al (15 satır eski hâline döndü).
- Çalıştırmadan önce canlıda 15 adresin ve mevcut adların onay listesindeki "önce" sütunuyla birebir aynı olduğu okundu.

## Uygulama tarafı
Adlar sunucudan geliyor; uygulama güncellemesi gerekmez. Uygulamanın katalog önbelleğinin ne zaman yenilendiğine bu turda bakılmadı; yazımdan sonra telefonda bir kez doğrulanmalı.

## Kalan
1. Telefonda bir kez bakmak: katalogda ve yolculuk sayfasında yeni adlar görünüyor mu (uygulamanın ağ önbelleği 5–10 dakika; cihazdaki katalog kopyasının ne zaman yenilendiğine bakılmadı).
2. İngilizce alt adlar ve Room 214 bulgusu: Tomris. Canlıdaki İngilizce alt adlar: 1016 "A Giant Blast, No Crater", 1017 "The Loudest Sound Ever Recorded", 1020 "One Refusal, No Launch", 1023 "A Poison Island Full of Rabbits", 1045 "The Hut on Chicken Legs", 1053 "The Box He Must Never Open", 1055 "Alone on a Broken Boat", 1059 "She Fell Three Kilometres", 1060 "497 Days on the Ice", 1061 "Two Years on Wrangel Island"; 148, 1063, 1064, 1066, 1082'de boş. Yeni adla aynı şeyi söyleyenler (1045, 1053, 1061) Tomris'in kararında.
3. Geri alma gerekirse: `MigrationScripts/RenameFifteenTexts_2026_11_26_REVERT.sql`.
