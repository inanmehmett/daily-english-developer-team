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

## Ek (26 Kas, gece): kartta görünmeyen beş Türkçe adın kısaltılması
**Görev:** `ortak/editor_gorevi_2026-11-26_bes_ad_kisaltma.md` · **Durum: canlıda uygulandı (27 Kas 15:01).** Mehmet: "yap". Sunucu [PR #25](https://github.com/inanmehmett/DailyEnglish/pull/25) GitHub testi geçtikten sonra birleştirildi ve yayına girdi (14:57); ardından betik canlıda çalıştırıldı. Beş satırın Türkçe adı değişti (21–27 karakter); İngilizce adlar ve adresler aynı; başka metne dokunulmadı; önceki adlar `_Backup_ReadingTextTrNames_2026_11_26b` tablosunda. Web ana sayfası "Haritadan Silinen Ada" gösteriyor. 28 karakteri aşan etkin Türkçe ad sayısı 28'den 23'e indi.

| Adım | Sonuç |
|---|---|
| 1. Canlıdaki şimdiki değerler | Beş satırın `SubtitleTR` değeri tablodaki "şimdi" sütunuyla birebir aynı (29–31 karakter) |
| 2. Betik ve geri alma | `MigrationScripts/ShortenFiveTurkishNames_2026_11_26.sql` ve `..._REVERT.sql`. Yalnız `SubtitleTR`; eşleşme adresle; beş satırın beşi beklenen adla bulunmazsa ya da yeni adlardan biri 28 karakteri aşarsa hiçbir şey yazmaz; önceki adlar `_Backup_ReadingTextTrNames_2026_11_26b` tablosuna. Yerelde uygulandı, yeniden uygulandı (değişiklik yok), geri alındı |
| 3. Canlıya yazma | Yapıldı (27 Kas 15:01), beş satır canlıdan okunarak doğrulandı |
| 4. Görüntüyle doğrulama | **Yapıldı (27 Kas), sonuç olumsuz:** beş addan dördü telefonda kesiliyor. Aşağıdaki "Görüntü ve ölçüm" bölümüne bakın |
| 5. Eski adın sabit yazıldığı yerler | Web ana sayfasında "Haritadan Silinen Tavşan Adası" yazıyordu; PR #25'te "Haritadan Silinen Ada" oldu. Başka sabit yer yok |
| 6. 28 karakter denetimi | Test takımına **eklenemiyor:** metinler yalnız veritabanında, testler canlı içeriği görmüyor. Yerine iki şey: bu betik yeni adlar 28'i aşarsa yazmayı reddediyor; depoya salt okunur denetim sorgusu eklendi (`MigrationScripts/CheckTurkishNameLength.sql`), ad yazan her betikten sonra çalıştırılır |

**Görevde olmayan bulgu:** canlıda 28 karakteri aşan Türkçe adı olan etkin metin **28 tane**, yalnız bu beşi değil. Öbür 23'ünün Türkçe adı da kartlarda görünmüyor (çoğu 26 Kasım'dan önce de böyleydi):
| Karakter | Metinler (kimlik: ad) |
|---|---|
| 34 | 1033: Shakespeare: Kelime İcat Eden Adam · 1009: Yıldızları Sayan Hükümdar Uluğ Bey |
| 33 | 175: Stephen Hawking'e Biçilen İki Yıl · 994: İskenderiye'nin Kayıp Kütüphanesi · 1065: İstanbul'un Yer Değiştiren Pazarı |
| 32 | 1035: Londra'nın Durmayan Dönme Dolabı |
| 31 | 153: Harry Potter Setlerinde Büyümek · 873: Bazı Kapılar Neden Dışa Açılır? · 1001: Floransa: Yirmi Dakika, Üç Dahi · 1007: Küllerinden Doğan Şehir: Londra |
| 30 | 872: Kendini Neden Gıdıklayamazsın? · 999: İnkaların Yıkılmayan Duvarları · 998: Beyaz Piramidin İzinde: Kahire · 1087: Dünyanın En Ünlü Vergi Belgesi · 1010: Azteklerin Göldeki Beyaz Şehri · 1014: Viyana: Müziğin Silikon Vadisi · 1040: Huckleberry Finn'in Maceraları |
| 29 | 1074: Bob Dylan'ın Yuhalandığı Gece · 1004: Kudüs'ün Taşınamayan Hazinesi · 1037: Yıkılmak İstenen Eyfel Kulesi · 1036: Uçurumun Kenarında: Santorini · 1000: Şam'ın İki Bin Yıllık Caddesi · 1029: Cep Herkülü Naim Süleymanoğlu |

Karar ekipte (Tomris, Dieter): 23 adı da kısaltmak mı, kartı iki satıra geçirmek mi (uygulama derlemesi).

### Görüntü ve ölçüm (27 Kas)
**Nasıl alındı:** ana sayfa rafının gerçek kartı (`UnifiedBookCard`), uygulamanın kendi yazı tipiyle (Inter) test ortamında çizdirildi; adlar canlıdan okunan değerler. Simülatörde uygulamanın tamamını derlemek bu bilgisayarın diskine sığmadı (4 GB'tan fazla istiyor), o yüzden görüntü telefonun kendisinden değil. Kapaklar ağdan gelmediği için boş; bakılan şey başlığın altındaki Türkçe satır.
- Telefon genişliği (kart 130 pt): `raporlar/ekran_2026-11-27/kisa_adlar_telefon.png`
- Tablet genişliği (kart 155 pt): `raporlar/ekran_2026-11-27/kisa_adlar_tablet.png`

**Beş kart, telefonda:**
| Metin | Yeni ad | Kartta görünen |
|---|---|---|
| 1023 | Haritadan Silinen Ada | **tamamı** |
| 1055 | Kasırgadan Sonra 41 Gün | "Kasırgadan Sonra 41" |
| 1045 | Baba Yaga ve Yürüyen Kulübe | "Baba Yaga Ve Yürüyen" |
| 1063 | İki Kez Kahvaltı Eden Ülke | "İki Kez Kahvaltı Eden" |
| 148 | İtalyanlar Neden Konuşkan? | "İtalyanlar Neden" |

Önceki hâlde bu beş kartta Türkçe satır hiç yoktu; şimdi satır var ama dördünde son kelime sessizce düşüyor (üç nokta yok). "İtalyanlar Neden" ve "Kasırgadan Sonra 41" yarım cümle gibi okunuyor. Ayrıca kart "ve" bağlacını büyük harfle yazıyor ("Baba Yaga Ve…"); bu uygulamadaki baş harf büyütme kuralından geliyor.

**Asıl bulgu: 28 karakter kuralı kartın gerçek genişliğini tutmuyor.** Türkçe satır tek satır ve sabit genişlikte; sığıp sığmadığını karakter sayısı değil harflerin eni belirliyor. Canlıdaki 287 etkin metnin tamamı ölçüldü:
| Kart genişliği | Tam görünen | Kesilen | Hiç çizilmeyen (28'i aşan) | Kesilen en kısa ad |
|---|---|---|---|---|
| 130 pt (genişliği 400 pt'in altındaki telefonlar) | 227 | **37** | 23 | 21 karakter |
| 140 pt (büyük telefonlar) | 241 | 23 | 23 | 21 karakter |
| 155 pt (tablet) | 255 | 9 | 23 | 24 karakter |

Telefonda (130 pt) kesilen 37 adın içinde 26 Kasım'da yazılan 15'ten dördü de var: 1016 "Gökyüzünün Düştüğü Sabah", 1020 "Üçüncü İmzayı Vermeyen Adam", 1053 "Urashima Tarō ve Yasak Kutu", 1059 "Gökten Amazon'a Düşen Kız". Tam liste (kimlik: ad, karakter):
120: Penguen Neden Uçamaz? (21) · 148: İtalyanlar Neden Konuşkan? (26) · 874: Aynalar Neden Yeşilimsi? (24) · 875: Fotoğraflar Neden Sararır? (26) · 877: Uçaklar Neden İz Bırakır? (25) · 878: Yoldaki Çizgiler Neden Var? (27) · 879: Çelik Gemiler Neden Batmaz? (27) · 905: Gruptaki Yedinci Numara (23) · 949: Fırının Bozulduğu Perşembe (26) · 987: Sabahın Dördünde Kahve (22) · 990: Dünyanın Kurduğu Şehir: Roma (28) · 1002: Avrupa'nın İnanmadığı Şehir (27) · 1011: Dünyanın Öbür Ucu: Timbuktu (27) · 1012: Ganj Kıyısında Üç Bin Yıl (25) · 1013: Venedik'in Altındaki Orman (26) · 1016: Gökyüzünün Düştüğü Sabah (24) · 1018: Telgrafın Tutuştuğu Gece (24) · 1020: Üçüncü İmzayı Vermeyen Adam (27) · 1021: Gutenberg'in Kaybettiği İcat (28) · 1030: Tom Sawyer'ın Maceraları (24) · 1032: Mısır'da Çay Nazlanması (23) · 1034: Her Sabah İki Kıta: İstanbul (28) · 1039: Alice Harikalar Diyarında (25) · 1045: Baba Yaga ve Yürüyen Kulübe (27) · 1046: Makineyle Yarışan Adam (22) · 1053: Urashima Tarō ve Yasak Kutu (27) · 1055: Kasırgadan Sonra 41 Gün (23) · 1057: Karanlıkta Altmış Dokuz Gün (27) · 1059: Gökten Amazon'a Düşen Kız (25) · 1062: İki Kez Ölü Sayılan Dağcı (25) · 1063: İki Kez Kahvaltı Eden Ülke (26) · 1068: Çöp Kamyonu Gelmeyen Köy (24) · 1075: Yerinde Durmayan Deniz (22) · 1076: Eski Buzdolabının Son Gecesi (28) · 1084: Gökyüzü Neden Turuncu Olur? (27) · 1091: Seksen Günde Devriâlem (22) · 1111: Küçük Prens'i Yazan Pilot (25)

**Sınır:** ölçüm test ortamında, kartın genişliği metin kutusu sayılarak yapıldı; gerçek telefonda bir iki piksel oynayabilir, sınırdaki birkaç ad yer değiştirebilir. Tablonun yönü değişmez.

**Karar (ekip ve Mehmet):**
1. Kartta Türkçe satır iki satıra geçsin ya da sığmayınca küçülsün (uygulama değişikliği, derleme 51): 60 metnin hepsini çözer, adları kısaltmaya gerek kalmaz.
2. Ya da içerik kuralı "28 karakter" yerine ölçüyle yazılsın (telefonda güvenli sınır yaklaşık 20 karakter) ve 60 ad yeniden kısaltılsın.
3. Bu beş ad için geri alma betiği hazır (`ShortenFiveTurkishNames_2026_11_26_REVERT.sql`); geri alınırsa satır yine hiç çizilmez.
Editör bir şey değiştirmedi.
