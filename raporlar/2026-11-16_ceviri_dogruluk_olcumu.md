# Çeviri motoru: premium metinlerde doğruluk ve bağlama göre anlam seçimi — 16 Kasım 2026

Ücretsiz rafın ilk metinleri elle düzeltildiği için ölçüm tabanı premium metinlerdir. İki soru:

1. Kalan hatalar motor düzeltmeleriyle giderilebilir mi?
2. Motor, sözlükteki anlamlar arasından cümleye uyanı seçebilir mi?

## Kısa cevap

- **Bugün:** premium metinlerde balonların %77,6'sı doğru, %13,5'i yakın, %7,2'si yanlış, %1,7'si boş.
- **Anlam seçimi asıl sorun.** Yanlış ve yakın balonların %80'i, sözlükte birden çok anlamı olan kelimelerde ve doğru anlam çoğu zaman listede var. Motor ise bağlama bakmıyor: kelimenin türüne uyan ilk anlamı seçiyor.
- **Kuralla düzeltilemiyor.** Sözlükteki anahtar kelimelerle seçim yaptırınca 42 balon değişti; 33'ü doğruydu ve bozuldu, 5 yanlış düzeldi.
- **Dil modeliyle seçim işe yarıyor.** Aynı 1.000 vakada, model yalnız sözlükteki anlamlardan seçince yanlış oranı %7,2'den %3,7'ye iniyor, doğru oranı %81,2'ye çıkıyor. Sözlükte uygun anlam yoksa modelin önerdiği karşılık da kullanılırsa yanlış %2,0'ye iner, doğru %83,6 olur.
- **Haiku ile Sonnet aynı sonucu veriyor** (yanlış %4,0 ve %3,7; vakaların %89'unda aynı anlamı seçtiler). Toplu iş için Haiku yeterli.
- **Bir kısmı motor kuralıyla düzeliyor:** "that", "like", "the way", "one of" ve saat ifadeleri. Kalıp anlamlarına da aynı seçim gerekiyor ("came up" her yerde "gündeme gelmek" çıkıyor).

## Nasıl ölçüldü

- **Taban.** 22 premium metindeki her içerik kelimesinden (5.489 vaka) sabit tohumla rastgele 1.000 vaka seçildi. Balonlar canlı kod ve canlı sözlükle üretildi; her balonu Sonnet cümle içinde değerlendirdi. Talimat: `ceviri-denetimi/dogruluk/TALIMAT.md`.
- **Anlam seçimi denemesi.** Sözlükte birden çok anlamı olan 768 vakada Haiku ve Sonnet'e cümle ile sözlükteki anlam listesi verildi. Görev: listeden seçmek; hiçbiri uymuyorsa "yok" deyip karşılık önermek.
- **Değerlendirme.** Motorun seçtiğinden farklı her seçim (249 farklı karşılık), kimin seçtiği bilinmeden ayrı bir Sonnet değerlendiricisine verildi. Motorla aynı seçimlerde tabandaki karar geçerli.
- **Denetim.** Seçimin bozduğu bütün vakaları ve kalan yanlışların hepsini elle okudum.
- **Dosyalar:** `ceviri-denetimi/premium/` (temel.json, sec_*.json, haiku_*/sonnet_*.tsv, yargi_*).

**Sınırlar.**
- Değerlendirici model, insan değil; "yakın" ile "doğru" arasındaki sınırda tutarsız. Oranları ±2 puan oynak okuyun.
- Yanlış oranındaki iniş bundan daha güvenilir: yanlış denen her vaka gerekçeli ve elle kontrol edildi.

## Sonuçlar

| | Doğru | Yakın | Yanlış | Boş |
|---|---|---|---|---|
| Bugünkü motor | %77,6 | %13,5 | %7,2 | %1,7 |
| Anahtar kelimeyle seçim | — | — | — | — |
| Haiku, yalnız sözlükten | %81,0 | %13,3 | %4,0 | %1,7 |
| Sonnet, yalnız sözlükten | %81,2 | %13,4 | %3,7 | %1,7 |
| Sonnet, sözlükte yoksa kendi önerisi | %83,6 | %12,7 | %2,0 | %1,7 |

Anahtar kelimeyle seçim satırı boş: denemede doğruyu bozdu (42 değişikliğin 33'ü kötüleşme), ölçüme alınmadı.

**Seçimin düzelttikleri:**

| Kelime | Motor | Model |
|---|---|---|
| hard ("hard with frost") | zor | sert |
| cabin | kulübe | kamara |
| lanes | şerit | dar sokak |
| drop ("metres from a drop") | düşürmek | uçurum |
| left ("left them") | ayrılmak | bırakmak |
| pegs | mandal | kazık |

**Seçimin bozdukları (4 yanlış, 14 yakın):**
- believe → "güvenmek" ("does not believe me")
- arm → "sandalye" (koltuğun kolu)
- account → "banka hesabı" ("on his own account")
- "since that night" → "ki o"

Seçim düzelttiğinin yaklaşık beşte birini bozuyor. Bu yüzden canlıya çıkmadan önce örneklem denetimi şart.

## Seçimden sonra kalanlar (1.000 vakada)

| Sınıf | Yanlış | Yakın | Ne yapılır |
|---|---|---|---|
| Sözlük karşılığı kaba ya da birleşik ("taşınmak, hareket etmek"; people → kişi) | 10 | 98 | Sözlükte anlamları ayrı ve yalın yazmak; ya da seçimde modelin önerisine izin vermek |
| Kural kelimeleri (that, like, the way, one of, saat ifadesi "half past") | 3 | 23 | Motor kuralı (aşağıda) |
| Kalıp ve özel isim | 7 | 6 | Kalıp anlamı için de seçim; başlıkta sahte özel isim; çevrilmeyen sayı ve halk adları |
| Sözlükte yok | — | — | 17 boş balon: tireli sayılar, bileşikler, nadir kelimeler |

## Öneri

**1. Bağlama göre anlam seçimi, önceden hesaplanmış.**
- Metinler sabit. Her premium metindeki çok anlamlı her kelime için model, sözlükteki anlamlardan birini bir kere seçer. Seçim cümle anahtarı ve kelime sırasıyla saklanır; ücretsiz rafın elle doğrulanmış karşılıkları da bugün bu yolla saklanıyor.
- Balon açılırken modele gidilmez; gecikme olmaz.
- Saklanan şey Türkçe metin değil, **sözlükteki anlamın kimliği** olmalı. Böylece kelime defterine de doğru anlam kaydedilir; bugün cümle-içi karşılıklar deftere sözlüğün genel anlamını yazıyor.
- Yeni metin eklenince aynı iş o metin için çalışır.
- **Ölçek:** premium katalog 263 metin, 431.631 kelime; tahminen 140 bin seçim. Haiku ile tek seferlik bir toplu iş.
- **Altyapı:** backend'de dil modeli istemcisi yok. Seçim çevrimdışı bir araçla yapılıp veri olarak yüklenir.
- **Önce pilot:** 5 premium metin seçilir, sonuç örneklem denetiminden geçer ve bu 1.000 vakalık ölçüm tekrarlanır. Yanlış oranı %4'ün altına inerse bütün kataloğa yayılır.
- **Modelin kendi önerisi:** sözlükte uygun anlam olmadığında model önerisinin kullanılıp kullanılmayacağı ayrı karar. Ek kazanç 1,7 puan, ama o karşılıklar sözlüğe girmemiş, editörden geçmemiş metin olur. Önerim: öneriler editör kuyruğuna gitsin; onaylanan sözlüğe eklensin.

**2. Motor kuralları.** Seçimden bağımsız, her metinde geçerli; yaklaşık bir günlük iş.
- "that": bağlaç ("said that" → "…dığını"), ilgi zamiri ("the strait that divides it" → "(…olan)"), işaret ("that night" → "o"). who/which kuralının devamı.
- "like" + isim → "gibi"; "the way" + özne → "…dığı gibi"; "one of" → "…lerden biri".
- Saat: "half past ten" → buçuk, "five to ten" → "ona beş var".
- Başlıklarda büyük harf tek başına özel isim saydırmasın; tireli sayılar çözülsün ("ninety-eight" → doksan sekiz).

**3. Kalıp anlamı seçimi.** Kalıp kayıtlarında da birden çok anlam var ve motor ilkini seçiyor ("came up to his waist" → "gündeme gelmek"). 1. maddedeki seçim kalıp kayıtlarını da kapsamalı.

**Sona bırakılanlar:**
- Sözlük karşılıklarının yalınlaştırılması: "yakın" vakaların çoğu bu, ama editör işi.
- Kaçırılan kalıpların sözlüğe eklenmesi: premium örneklemde 31 vaka.
- Tür etiketi hataları: balonu bozmuyor.

**Karar bekleyen:**
- 1'in 5 metinlik pilotu.
- 2'ye başlanması.
- Sözlükte uygun anlam yoksa modelin önerdiği karşılık doğrudan balona mı gitsin, editör kuyruğuna mı?
