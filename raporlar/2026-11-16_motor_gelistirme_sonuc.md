# Çeviri motoru geliştirmesi: sonuç — 16 Kasım 2026

Hedef: kural ekleyip başka yapıları bozmadan motorun ulaşabildiği en yüksek doğruluk. Kalan hatalar bundan sonra bağlama göre tek tek, elle düzeltilecek.

## Sonuç

| Küme | Önce doğru | Sonra doğru | Önce yanlış | Sonra yanlış |
|---|---|---|---|---|
| Gerçek dokunuşlar (482, dokunma sayısıyla ağırlıklı) | %87,1 | **%87,9** | %1,9 | **%1,2** |
| Premium (1.000) | %77,5 | **%79,9** | %7,2 | **%6,0** |
| Katalog (480) | %81,5 | **%84,2** | %5,8 | **%4,2** |
| Sınama (500; kurallar bu kümeden türetilmedi) | %77,4 | **%79,4** | %8,8 | **%7,4** |

- **Bozulma.** 9.511 vakalık havuzda 277 balon değişti: 215'i düzeldi, 1'i bozuldu, kalanı aynı düzeyde kaldı. Bozulan: "burned **that** temple" → "ki, (…dığını)".
- **Sınama kümesi.** Kazanç burada da görülüyor (doğru +2,0); kurallar örneklem kümesine ezberlenmedi.

## Katalog geneli bozulma taraması (canlıya almadan önce)

Ölçüm kümeleri küçük kelimeleri (in, the, a, for…) dışarıda bırakıyordu ve 46 metinle sınırlıydı. Bu yüzden 287 aktif metnin küçük kelimeler dahil her kelimesi (434.979 dokunuş) eski ve yeni motordan geçirildi. Değişen balonlardan her türden örnek alındı; eski ve yeni balon, hangisinin hangisi olduğu bilinmeden değerlendirildi.

**İlk taramada çıkan iki sorun ve yapılan düzeltme:**

- **Zaman ifadeleri.** Kalıplar kök üzerinden eşleştiği için 14 ifade çekimli biçimlere ya da başka anlamlara oturuyordu:
  - "the last **years**" → "geçen yıl"
  - "some **days** later" → "bir gün (ileride)"
  - "**the last week** of July" → "geçen hafta"
  - "in **one night**" → "bir gece"

  Bu 14 ifade listeden çıkarıldı:

  ```
  last week, last year, next year, some day, one day, one night,
  one morning, in a minute, in a moment, the day before,
  the day after, at one time, any more, for a minute
  ```

  Sözlüğe eklenecek ifade sayısı **41**.
- **"that" kuralı.** "**that** summer", "**that** school" gibi işaret sıfatları da bağlaç sayılıyordu; etiketleyici bunları ADP etiketliyor. Bağlaç dalı artık yalnız ardından zamir, belirleyici ya da özel isim geldiğinde çalışıyor ("that **he**…", "that **the** water…").

**Düzeltmeden sonra katalog geneli:**

| Ölçü | Sonuç |
|---|---|
| Değişen balon | 8.219 / 434.979 (%1,9) |
| Düzelen (tahmini) | ~5.800 |
| Bozulan (tahmini) | ~400 |

- Tahmin, değişikliğin türüne göre ayrı ayrı örneklenen 860 vakanın oranlarının katalogdaki gerçek değişiklik sayılarıyla çarpılmasıyla bulundu.
- Bozulanların büyük kısmı "that" kuralında. Örneklemde 52 vakada 38 düzelme, 6 bozulma; kalan kötü vakalar etiketleyicinin yanlış etiketinden geliyor ve elle düzeltme turunda listelenecek.
- Kalan diğer bozulmalar dağınık: "for good reasons" (2 vaka), "in the morning" (2).
- İlk taramada görülmeyen yeni bir balon çıkmadı. Bilmediğimiz bir bozulma türü kalmadı; kalanlar ölçüldü ve türleri biliniyor.

## Ne değişti

**Motor kuralları** (`feat/engine-accuracy`):
- "that": bağlaç ("said that he…" → "ki, (…dığını)") ve ilgi zamiri ("the strait that divides it" → "(…olan)"); işaret sıfatı sözlükte kalır.
- "like" edat → "gibi"; "the way" + yan cümle → "(…dığı) gibi"; "one of" → "(…lerden) biri".
- Saat: "half past ten" → "on buçuk", "ten to nine" → "dokuza on kala"; öbek tek balon.
- Tireli sayılar ("ninety-eight" → doksan sekiz); sayılı "time(s)" → "kez, sefer"; "at a time" → "bir seferde"; "two and a half" → "buçuk"; "half an hour" → "yarım"; "in order" → "sırayla, düzenli"; "in order to" → "(…mek) için".
- **İyelik ekli isimler.** Uygulama kelimeyi küçük harfle gönderdiği için bozuluyordu: "Tom's" → "tam tam (davulu)", "Maria's" → "hapishane arabası". Düzeltildi.
- **Başlıkta yanlış özel isim.** "The Man Who Walked into Camp" başlığında "Man" isim sanılıp çevrilmiyordu; artık çevriliyor.

**Sözlük:** 41 zaman/süre ifadesi sabit ifade olarak eklendi. Örnekler: "a long time" → uzun süre, "in the morning" → sabah, "for a moment" → bir an, "the next morning" → ertesi sabah, "years ago" → (…) yıl önce. Üç kelimeden hangisine dokunulursa dokunulsun tek balon çıkar.

**Uygulama** (`fix/phrase-type-label`): çok kelimeli her öbek "kalıp fiil" diye etiketleniyordu. Artık:
- yalnız phrasal verb türleri "kalıp fiil"
- birleşik isimler "birleşik isim"
- diğerleri "kalıp"

## Denenip geri alınanlar

Kapıdan geçemeyen ya da kazancı bozduğundan küçük kalan değişiklikler:

| Değişiklik | Neden çıkarıldı |
|---|---|
| Sözlükte birincil anlam sırası (5. adım) | 40 adayın kör karşılaştırmasında 2'si kazandı ("line → satır", "half → yarım"); 9.511'lik havuzda ikisi de kaybettirdi (çizilen çizgiler "satır", "half of humanity" "yarım" oldu). Bugünkü birincil anlamlar çoğunlukla doğru; yanlışlar bağlama bağlı. |
| Kökteki fiil anlamına inme ("pointed" → işaret etmek) | "was born" → "tahammül etmek" (kök bear), "excited" → "heyecanlandırmak". |
| Hareket fiili + yön edatı kalıp koruması ("came up from the office") | "Step back from the edge" kalıbını kesti. |
| "last night", "this time", "last time" ifadeleri | "the last night of the year" → "dün gece", "all this time" → "bu sefer". |

## Ölçüm nasıl yapıldı

- Her balon uygulamanın gerçek isteğiyle üretildi: küçük harf kelime, uygulamanın cümle bölmesiyle cümle ve kelime sırası.
- Sözlük değişiklikleri canlıya değil, canlının içerik kopyasına uygulandı. Kopyada kullanıcı verisi yok.
- Değişen her balon, hangi sürümün balonu olduğu bilinmeden değerlendirildi.
- Bozulanların hepsini elle okudum.
- Backend testleri: 1.661 geçti, 0 kaldı.

## Bekleyenler

1. **Canlıya alma (onay gerekli).**
   - Backend dalı birleştirilip yayınlanacak.
   - Sözlük SQL'i uygulanacak: `ceviri-denetimi/zaman/ZamanIfadeleri_2026_11_16.sql`; geri alma dosyası hazır.
   - Uygulama değişikliği yeni sürümle çıkar.
2. **Editör onayı.** Yeni Türkçe biçimler: "ki, (…dığını)", "(…olan)", "(…dığı) gibi", "(…lerden) biri", "kez, sefer", "(…mek) için" ve 41 zaman ifadesinin karşılıkları.
3. **Birleşik isimler (ekip kararı).**
   - Aday liste: `ceviri-denetimi/bilesik/eklenecek_aday.tsv`.
   - Liste, parçaların bugünkü balonu uygulama isteğiyle ölçülerek çıkarıldı: 239 çiftten 52'sinde parçalardan biri okuru yanıltıyor (car park → "park etmek", ice cream → "kaymak", river bank → "banka").
   - Liste onaylanınca eklenir. Yalnız son kelime isimken tanınır; deftere bütün olarak kaydedilir.
4. **Elle düzeltme turu.** Kalan yanlışların büyük kısmı bağlama bağlı ya da sözlük karşılığı kaba (premium yanlış %6,0). Sıradaki iş cümle-içi karşılıklarla tek tek düzeltme.
