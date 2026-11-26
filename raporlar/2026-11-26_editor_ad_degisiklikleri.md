# Editör raporu: onaylı ad değişiklikleri (15 metin)

**Tarih:** 26 Kasım 2026 · **Görev:** `ortak/editor_gorevi_2026-11-26_ad_degisiklikleri.md`
**Durum:** betik ve geri alma betiği hazır (sunucu [PR #22](https://github.com/inanmehmett/DailyEnglish/pull/22)); **canlıda çalıştırılmadı** (bu oturumda canlı veritabanına bağlanılamadı).

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
| İngilizce alt adlar (`SubtitleEN`) | Canlıdaki değerler okunamadı | Dokunulmadı; Tomris'e |

## Betik
- `MigrationScripts/RenameFifteenTexts_2026_11_26.sql`: yalnız `Title` ve `SubtitleTR`; adres (`Slug`) değişmez. Eşleşme adresle; 15 satırın tamamı bulunmazsa hiçbir şey yazmaz. Önceki adlar `_Backup_ReadingTextNames_2026_11_26` tablosuna alınır. İki kez çalıştırmak bir şey değiştirmez.
- `MigrationScripts/RenameFifteenTexts_2026_11_26_REVERT.sql`: adları yedekten geri yazar.
- Yerelde denendi: uygula (15 satır), yeniden uygula (değişiklik yok), geri al (15 satır eski hâline döndü).
- **Bilinmeyen:** canlıdaki adreslerin yereldekilerle aynı olduğu doğrulanamadı. Farklıysa betik hata verip durur, yarım yazmaz.

## Uygulama tarafı
Adlar sunucudan geliyor; uygulama güncellemesi gerekmez. Uygulamanın katalog önbelleğinin ne zaman yenilendiğine bu turda bakılmadı; yazımdan sonra telefonda bir kez doğrulanmalı.

## Kalan
1. PR #22'nin birleştirilmesi (web ana sayfası yayına girer).
2. Betiğin canlıda çalıştırılması ve 15 satırın okunarak doğrulanması.
3. İngilizce alt adlar ve Room 214 bulgusu: Tomris.
