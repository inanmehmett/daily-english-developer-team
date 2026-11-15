# İçerik incelemesi – ilk kanıtlı cevap (Bölüm 2)

**Tarih:** 15 Kasım 2026 · **Rol:** Paul Ulus (içerik ve pedagoji). Tek geçiş, alt ajan yok; üye kurgusaldır. Yalnız okuma: kod ve içerik değiştirilmedi.

**İçerikte kullanıcıyı kaçıracak düzeyde sorun var mı?** Evet, iki yerde: dokunulan kelimenin anlamı örneklemin beşte birinde cümledeki anlam değil ve bu hatalar en çok bakılan kelimelere denk geliyor; ayrıca ilk önerilen üç metinden ikisi etiketinden bir seviye zor. Metinlerin kendisi, başlıklar, açıklamalar ve quizler iyi durumda.

**Dayandığı örnek:** 5 metin (her zaman ücretsiz üç metin ve en çok okunan iki metin), 50 kelime anlamı, 25 cümle çevirisi, 20 quiz sorusu, 5 metnin ses kaydı verisi; canlı kullanım kayıtları (29 Eki–15 Kas, müşteri hesapları).

## Özet

1. **Kelime anlamı:** 50 kelimenin 11'i cümledeki anlamı vermiyor. İlk hikâyenin anahtar kelimesi "glasses" için "gözlük" geliyor (metin çay bardağını anlatıyor). En çok okunan metinde en çok bakılan kelime "beating" için "yenmek" geliyor.
2. **Seviye:** "Thirty-One Mornings" A1 etiketli ama A2; "The Island Where Rabbits Won" A2 etiketli ama B1. İkincisi A2 ve üstünü seçen herkesin ilk hikâyesi.
3. **Okurlar her seviyede eşikten çok kelimeye bakıyor:** 9–23 kelimede bir bakış; ölçü 50 kelimede bir.
4. **Cümle çevirisi:** 25 cümlenin 19'u doğal ve doğru, 3'ü yanlış, 3'ü kusurlu. Yanlışlar edebî ve eksiltili cümlelerde.
5. **Ses ve quiz:** ses dosyaları yerinde ve eşzamanlama verisi tam (dinlenemedi); 20 quiz sorusunun hepsi metinden cevaplanabiliyor. Kullanıcıdan gelen soru bildirimi yok.

## Örneklem neden bu beş metin

Görev "her seviyede ilk önerilen metin ve her zaman ücretsiz üç metin" diyordu. Uygulama ilk metni kilitsiz metinler arasından seçiyor ve kilitsiz yalnız üç metin var: A1 seçene "Two Cups", A2 ve üstünü seçen herkese "The Island Where Rabbits Won" öneriliyor. Yani iki küme aynı üç metin. Bunlara en çok okunan iki metni ekledim. Okumaların tamamına yakını A1–B1'de (A1 161, A2 37, B1 167, B2 1 açılış), bu yüzden B2 ve üstünden örnek almadım.

## Bulgular

| # | Bulgu | Kanıt | Önem | Öneri |
|---|---|---|---|---|
| P1 | Dokunulan kelimenin anlamı 50 örnekten 11'inde cümledeki anlam değil (%22). Hepsinde sunucu "bağlamdan çözüldü" diyor. | Aşağıdaki "Kelime anlamları" tablosu; canlı uygulamanın `TranslateWord` yanıtları, 15 Kas | yüksek | Üç ücretsiz metin ve en çok okunan iki metin için bu 11 kelimeye elle doğru anlam yazılsın (bağlam notu düzeneği var). Sonra aynı kontrol sıradaki en çok okunan metinlere. |
| P2 | Hatalar en çok bakılan kelimelere denk geliyor: "beating" (70 okurun 38'i baktı), "hollow" (29), "drops" (26), "bursts" (21), "folds" (20); "pot" (65 okurun 21'i), "glasses" (11). | `UserEvents.word_lookup`, okumaya atanmış | yüksek | P1 ile aynı iş; sıra bu listeye göre. |
| P3 | "The Island Where Rabbits Won" A2 etiketli; cümle ortalaması 13,6 kelime, en uzun cümle 32 kelime, en az altı edilgen yapı ve bir "though" yan cümlesi. Okurlar 14 kelimede bir kelimeye bakıyor (açılış başına ortanca 14 bakış). 16 okurun 9'u bitirmiş. | Metin; kullanım kaydı | yüksek | Ya etiket B1 yapılsın ya da metin A2'ye indirilsin. Etiket değişirse A2 seçenin ilk hikâyesi "Two Cups" olur (karar ekipte, aşağıda). |
| P4 | "Thirty-One Mornings" A1 etiketli; cümleler kısa ama eksiltili ("Day three: it runs, but late.", "Birds up high. Water somewhere."). 9 kelimede bir bakış: örneklemin en yükseği. Okur sayısı az (7). | Metin; kullanım kaydı | orta | Etiket A2 yapılsın. Az okur olduğu için bakış oranı hipotez. |
| P5 | En çok okunan metin "Why Penguins Can't Fly" (70 okur) en az bitirilen metin: 28 kişi (%40). Metin mecazla ilerliyor ("moved its sky into the water", "The price was the sky"). | Kullanım kaydı; metin | orta | B1 için yerinde ama ilk karşılaşılan metin olmamalı. Hangi yoldan bu kadar okura ulaştığı bilinmiyor (aşağıda). |
| P6 | Cümle çevirisi 25 örnekten 3'ünde yanlış, 3'ünde kusurlu. "Day three: it runs, but late." → "Çalışıyor, ama gecikmeli." "The price was the sky." → "Fiyat tavan yapmıştı." | Aşağıdaki "Cümle çevirileri" | orta | Üç ücretsiz metnin cümle çevirileri elle yazılıp saklansın; canlıda cümle tablosu boş, çeviri her seferinde makineden geliyor. |
| P7 | Seslendirme hızı A1 metinlerinde dakikada 132–153 kelime. Seviye gözetilmemiş: B1 metinleri 140–165. | `SentenceAudioClips.DurationMs` toplamı ÷ kelime sayısı | orta | Dinlenmeden kalite söylenemez. A1 için daha yavaş bir okuma denenmeli mi, Mehmet dinleyip karar versin. |
| P8 | Quiz: metin başına 4 soru var (görev 5 diyordu). 20 sorunun hepsi metinden cevaplanıyor, tek doğru cevap var. İki soru dikkat istiyor (aşağıda). | Quiz tabloları | düşük | İki soru yeniden yazılabilir. |
| P9 | Başlık, Türkçe alt başlık ve açıklamalar Mehmet'in standartlarına uyuyor: beşi de metindeki bir sahneye dayanıyor, Türkçesi doğal. Tek pürüz: "Two Cups" başlığı, metin ise hep "glasses" diyor. | Katalog alanları | düşük | Başlık "Two Glasses" olabilir; karar Mehmet'in zevkine kalır. |
| P10 | Beş metnin hepsinde bitiş cümlesi ve "sıradaki" kancası alanları boş. | `FinishLine`, `NextHook` | düşük | Metni bitirenin sonraki okumaya geçişi zayıf (22 kişiden 6); bu alanlar o an için yazılabilir. |

## Metin metin

| Metin | Etiket | Kelime | Cümle ort. / en uzun | Okur / bitiren | Kaç kelimede bir bakış | Benim okumam |
|---|---|---|---|---|---|---|
| Two Cups | A1 | 217 | 6,2 / 12 | 65 / 37 | 22 | A1'e uygun. Sessiz, kendi içinde biten bir hikâye. |
| Thirty-One Mornings | A1 | 252 | 6,5 / 22 | 7 / 5 | 9 | A2. Eksiltili anlatım A1 okuru için zor. |
| The Island Where Rabbits Won | A2 | 285 | 13,6 / 32 | 16 / 9 | 14 | B1. Edilgen yapı ve uzun cümle yoğun. |
| Why Penguins Can't Fly | B1 | 324 | 12,5 / 27 | 70 / 28 | 23 | B1–B2. Mecaz yükü ağır. |
| The Village That Whistles | B1 | 282 | 14,8 / 30 | 31 / 17 | 22 | B1'e uygun. |

"Kaç kelimede bir bakış" yaklaşık bir ölçüdür: kelime bakışları, kullanıcının o sırada açık olan metnine atandı (açılıştan sonraki 45 dakika). Meraktan yapılan dokunuşlar da içinde ("Two Cups"ta "the" ve "them" kelimelerine bile bakılmış).

**İlk paragraflar:** beşi de ilk cümlede bir soru açıyor (merdivenleri silen adam, her sabah aynı tilki, haritadan silinen ada, taş gibi denize düşen penguen, ıslıkla konuşan köylüler). Bu bir okuma yargısıdır, ölçüm değil.

**Okurların en çok baktığı kelimeler** (seviyenin üstünde kalanların kanıtı):
- Two Cups: bucket, cleans, stairs, flat, stood, above, pot, wet, still.
- Thirty-One Mornings: fox, rock, somewhere, count (az okur).
- The Island: ferries, purpose, chase, concrete, removed, erased, multiplied, chemicals, released, enemies, weapon.
- Penguins: beating, ancestors, trade, hollow, useless, movement, drops, solid, tubes, bursts, flippers, folds.
- Village: whistle, syllables, valleys, shepherds, speech, carries, invitations, steep, treats, heritage.

## Kelime anlamları (yanlış çıkan 11)

| Metin | Kelime | Cümle | Uygulamanın verdiği | Olması gereken |
|---|---|---|---|---|
| Two Cups | glasses | Two glasses this time. | gözlük | bardak |
| Two Cups | pot | I put water in the pot. | çömlek | demlik / tencere |
| Thirty-One Mornings | still | Stand still, look at the trees… | hâlâ | kıpırdamadan |
| The Island | left | …the buildings were left standing. | ayrılmak | bırakılmak |
| Penguins | beating | …wings beating like any bird… | yenmek | (kanat) çırpmak |
| Penguins | drops | …and drops into the sea like a stone. | düşürmek | düşmek |
| Penguins | hollow | …light bodies and hollow bones… | kovuk | içi boş |
| Penguins | folds | A big wing folds in water… | kat izi/yeri | katlanmak, bükülmek |
| Penguins | bursts | …with short bursts much faster. | patlama | kısa süreli hamle |
| Village | handled | …language is handled mostly on the left side… | başa çıkmak | işlenmek |
| Village | holds | The village now holds a festival… | tutmak | düzenlemek |

Doğru çıkan 39'un arasında iyi örnekler de var: "on purpose" → "kasten, bilerek", "next (to)" → "yanında", "pick (up)" → "(eliyle) almak, yerden kaldırmak", "light bodies" → "hafif".

Tutarsızlık: aynı metinde cümle çevirisi "Bu sefer iki bardak." diyor, kelimeye dokununca "gözlük" çıkıyor.

## Cümle çevirileri (yanlış ve kusurlu 6)

| Metin | Cümle | Uygulamanın verdiği | Sorun |
|---|---|---|---|
| Thirty-One Mornings | Day three: it runs, but late. | Üçüncü gün: Çalışıyor, ama gecikmeli. | Yanlış: tilki kaçıyor. |
| Thirty-One Mornings | Then it stands, walks along the rock, and is gone between the trees. | Sonra orada durur, kayanın üzerinde yürür… | Yanlış: ayağa kalkar, kaya boyunca yürür. |
| Penguins | The price was the sky. | Fiyat tavan yapmıştı. | Yanlış: bedeli gökyüzüydü. |
| Thirty-One Mornings | Forty steps is fine. | Kırk adım yeterli. | Kusurlu: kırk adım mesafe sorun değil. |
| Thirty-One Mornings | The fox is under the rock… | Tilkisi kayanın altında… | Kusurlu: "tilkisi" değil "tilki". |
| Village | The sound carries the melody of the syllables instead of the voice. | Ses, ses yerine hecelerin melodisini taşır. | Kusurlu: "sound" ve "voice" ikisi de "ses". |

"Two Cups" ve "The Island" için beşer cümlenin hepsi doğru ve doğal ("Dışarıda deniz gri ve dalgasızdı.", "Japon haritalarından kasten çıkarılmıştı.").

## Ses

- Beş metnin her cümlesi için ses kaydı var; sıra numaraları kesintisiz, hepsinde kelime zamanlama verisi dolu, tek ses kullanılmış. Örnek altı dosya açılıyor (200, `audio/mpeg`).
- Hız (toplam süre ÷ kelime): Two Cups 153, Thirty-One Mornings 132, The Island 158, Penguins 140, Village 165 kelime/dakika.
- **Dinleyemedim.** Telaffuz, ton ve eşzamanlamanın kulağa nasıl geldiği hakkında bir şey söyleyemem.

## Quiz

- Sunucu soruları ve şıkları her seferinde karıştırıyor; "doğru cevap hep ilk şık" sorunu yok.
- Dikkat isteyen iki soru:
  - The Island, doğru/yanlış: "The text gives two different stories about how the rabbits arrived, and does not say which is true." Tek cümlede iki iddia var ve metin hakkında soru soruyor; A2 okur için ağır.
  - Thirty-One Mornings: "What does the fox do on day thirty-one?" Doğru cevap "gözlerini bir saniye kapatır"; çeldiricilerden "ağaçların arasına kaçar" da metnin sonunda kısmen oluyor.
- Açıklamaların çoğu metinden alıntı; üçü Türkçe editör notu gibi ("Metin sebebi söylemez, sırayı gösterir.").
- `quiz_question_reported` kaydı: hiç yok.

## Bilinmeyenler

- Ses kalitesi (dinlenmedi).
- "Why Penguins Can't Fly" neden en çok okunan metin: günlük açılan metinlerden biri, ama 70 okura hangi ekrandan ulaştığına bakmadım.
- Bölümlü 36 kitabın ve B2 üstü metinlerin durumu: örneklemde yok.
- Kelime anlamı hatalarının katalog genelindeki oranı: 50 kelime, bilerek zor ve çok anlamlı kelimelerden seçildi; rastgele örnekte oran daha düşük çıkabilir.
- Kelimeye bakma sıklığının ne kadarı zorluk, ne kadarı merak: yeni sürümdeki ölçümle (bakışın yapıldığı metin kaydı) netleşecek.

## İtirazlar

- **Nassim Talip:** "Seviye zor" yargısı üç metinde 7–16 okura dayanıyor; Thirty-One Mornings'te 7. Etiket değişikliği ucuz ve geri alınabilir olduğu için yapılabilir ama "ders" yazılmaz.
- **Don Normal:** Okurlar yanlış anlamı fark etmeyebilir; "glasses → gözlük" cümleyi anlamsız kılar ama kullanıcı hatayı kendinde arar. Bu yüzden şikâyet gelmemesi sorun olmadığını göstermez.
- **Paul Ulus'un kendi şerhi:** Metinlerin edebî kalitesi yüksek; "Thirty-One Mornings"teki eksiltili üslup bilinçli bir tercih. Sorun metinde değil etikette ve makine çevirisinin bu üslupla baş edememesinde.

## Ekibe bırakılan kararlar

Mehmet bu turdaki kararları ekibe bıraktı. Tek geçiş:

| Konu | Karar | Gerekçe |
|---|---|---|
| 11 yanlış kelime anlamı | Elle düzeltilsin; ilk iş. | En çok okunan metinlerin en çok bakılan kelimeleri; ürünün ana vaadi "dokun, anlamı gör". |
| Thirty-One Mornings etiketi | A2 yapılsın. | Metin değişmez, yalnız raf değişir. |
| The Island etiketi | Şimdilik A2 kalsın; önce P1 düzeltilsin, yeni sürümdeki bakış ölçümüyle iki hafta sonra karar verilsin. | Etiket B1 olursa A2 ve üstünü seçen herkesin ilk hikâyesi "Two Cups" olur; bu, yeni son ekranın ölçümünü bozar (29 Kasım). Nassim Talip'in şartı. |
| Üç ücretsiz metnin cümle çevirileri | Elle yazılıp saklansın. | Yeni kullanıcının ilk gördüğü metinler; makine burada yanılıyor. |
| A1 ses hızı | Mehmet dinlesin; karar onun kulağında. | Dinlenmeden karar verilemez. |

Bu kararların hiçbiri bu turda uygulanmadı; içerik ve sözlük düzeltmeleri ayrı bir iş.
