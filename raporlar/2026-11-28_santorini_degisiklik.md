# Santorini (1036): metin değişikliği ve aynı sesle güncelleme

**Tarih:** 28 Kasım 2026 · **Hazırlayan:** editör · **Kuyruk:** 13 (12.1 ve 12.2 ile birlikte) · **Durum:** **canlıda** (Mehmet'in "yap"ı, 28 Kas; quiz ve balonlar dahil). Metin 13:38'de kapatılıp yazıldı, 13:40'ta 19/19 klip doğrulanarak açıldı. Mehmet uygulamada dinleyip onayladı: "metin olmuş, sesler tamam".

## Sonuç
- **19 cümleden 9'u yeni, 10'u aynen kalıyor.** Yalnız 9 klip üretilecek (478 karakter). Kalan 10 klip bugünkü ses dosyasını kullanmaya devam eder; bunların 6'sı yeni metinde başka sıraya düşüyor ve kaydı yeni sıraya taşınıyor, dosyaya dokunulmuyor.
- **Ses aynı:** Google Cloud TTS, `chirp3-hd-charon` (Chirp 3 HD "Charon"), hız 0,94, perde 0. Bugünkü 17 klibin 17'si bu sesle. ElevenLabs yok.
- **Maliyet:** ses ~0,8–1,4 sent (478 karakter; sistemin kayıt fiyatıyla 0,008 $, Google'ın Chirp 3 HD liste fiyatıyla 0,014 $). Yeni 9 cümlenin Türkçe çevirisi DeepL'den, ~1 sent. **Toplam 3 sentin altında.**
- **Dosya adı şeması aynı:** klip adı `sha256("<cümle>|<ses>|google")`'ın ilk 16 hanesi; yalnız cümle metnine ve sese bağlı. Canlıdaki iki klipte hesaplanıp doğrulandı (`8ae4b2defae16569`, `bc37d700c20a1fbf`). Değişmeyen cümleler bu yüzden yeniden üretilmez.
- **Quiz:** 4 sorudan 3'ü eski metinden alıntı yapıyor ("ring", "crater", "eruptions"); yeni metne uyarlandı (aşağıda). Doğru şıkların yeri değişmedi.
- **Kelime balonları:** değişen 9 cümlenin 96 kelimesi uygulamanın kullandığı hatla çözüldü. Yanlış anlam yok; 6 balon zayıf ("there is" → "orada", "in places" → "içinde / yer", "do not" → "yapmak", "middle" → "merkez"). Bunlar için bağlam karşılığı yazılacak (vitrin metinlerinde kullanılan yöntem).

## Bugünkü durum (12.1)
| | Değer |
|---|---|
| Erişim | **Premium.** Başlangıç paketinde değil, günlük havuzda değil |
| Seviye | A2 · 172 kelime (yeni hâl 182) |
| Ses | 17/17 cümle seslendirilmiş, 17/17 kelime zamanlamalı |
| Kelime anlamları | Elle bağlanmış anlam (bağlam karşılığı) **yok**; balonlar çözümleyiciden, cümleye göre geliyor |
| Quiz | Etkin quiz 4 soru; ayrıca eski, kapalı bir quiz var (okura gitmiyor, dokunulmadı) |
| Okur | Son 30 günde 1 okur, 3 oturum; quiz sonucu 1 |
| Kart metinleri | Türkçe ad "Uçurumun Kenarında: Santorini", açıklama ve özet yeni metinle çelişmiyor; değişmiyor |

## Cümle eşlemesi
Bölme, sunucunun kendi bölücüsüyle yapıldı (`SentenceUtils.SplitIntoSentences`); eski metinde 17 cümle çıktı, canlıdaki 17 klible birebir.

| Yeni sıra | Cümle | Ses |
|---|---|---|
| 0 | Every evening, thousands of people stand on a cliff… | korunur (yerinde) |
| 1 | Most of them do not know one thing: they are standing on a volcano. | **yeni** |
| 2 | Santorini was a round island long ago. | **yeni** |
| 3–5 | About 3,600 years ago… · It was one of the biggest explosions… · The middle of the island went under the sea. | korunur (yerinde) |
| 6 | Today you can see only a part of the old island: a long line of high cliffs, almost a circle. | **yeni** |
| 7 | In the middle, there is deep blue water. | **yeni** |
| 8 | That famous view from the white villages? | korunur (7 → 8) |
| 9 | You are looking inside the volcano. | **yeni** |
| 10 | The sea came in and filled it. | **yeni** |
| 11–13 | The volcano is not dead. · It is only sleeping. · In the middle of the water there is a small black island. | korunur (10–12 → 11–13) |
| 14 | It grew out of the sea after later explosions, and it is still warm in places. | **yeni** |
| 15 | The volcano can explode again. | **yeni** |
| 16–17 | So tomorrow evening… · The sunset is beautiful. | korunur (14–15 → 16–17) |
| 18 | But under their feet, there is a volcano, and it is still sleeping. | **yeni** |

Eski metindeki "The ground under their feet has a longer story.", "…the ring — a curve of high cliffs…", "…the mouth of the volcano.", "…the crater, filled by the sea." cümlelerinin dosyaları depoda kalır; hiçbir kayıt onları göstermez. Geri almada yeniden kullanılır.

## Quiz: önce / sonra
| Soru | Önce | Sonra |
|---|---|---|
| 1 | What are the famous cliffs of Santorini? · doğru: *The edge of an exploded volcano* · açıklama: "What is left today is the ring — a curve of high cliffs." | What are the high cliffs of Santorini? · doğru: *A part of the old island* · açıklama: "Today you can see only a part of the old island: a long line of high cliffs, almost a circle." |
| 2 | The volcano under Santorini is only sleeping, not dead. (Doğru) | **değişmiyor** (açıklamadaki iki cümle yeni metinde de var) |
| 3 | What is the blue water in the middle of the ring? · doğru: *The crater of the volcano, filled by the sea* | What is the blue water in the middle of the cliffs? · doğru: *The sea, inside the old volcano* · açıklama: "You are looking inside the volcano. The sea came in and filled it." |
| 4 | …small black island… · doğru: *New land grown from later volcanic eruptions* | soru aynı · doğru: *New land from later explosions* · açıklama: "It grew out of the sea after later explosions, and it is still warm in places." |

Yanlış şıklar değişmiyor. Yazımdan sonra etkin quizde "ring", "mouth", "crater", "eruptions" geçmiyor.

## Balonlar: yazılacak bağlam karşılıkları
| Cümle | Kelime | Bugün | Yazılacak |
|---|---|---|---|
| 1 | do (do not know) | yapmak | (yardımcı fiil) |
| 7 | middle | merkez | orta |
| 7 | there (there is) | orada | var |
| 14 | in (in places) | içinde | yer yer |
| 14 | places (in places) | yer | yer yer |
| 18 | there (there is) | orada | var |

Diğerleri doğru: "long ago" → çok önce, "came in" → içeri girmek, "out of" → -den dışarı, "inside" → içinde, "later" → daha sonra, "explode" → patlamak, "almost" → hemen hemen, "circle" → daire. Aynı "there is" ve "in places" zaafı değişmeyen 13. cümlede de var; ses değişmediği için bu işin dışında bıraktım, istenirse aynı yöntemle eklenir.

## Nasıl yazılacak (Mehmet "yap" deyince)
Okur, sesi eksik metni hiç görmesin diye metin kısa süre kapatılır:
1. `SantoriniRewrite_2026_11_28.sql`: yedek tabloları kurar, metni (ve kelime sayısını 182) yazar, **metni kapatır**, quizi ve balonları yazar. Metin ne eski ne onaylı yeni hâlindeyse hiçbir şey yazmaz.
2. Ses üretimi, geliştirici makinesinden (Google anahtarı yalnız orada): `generate-audio 1036 --voice chirp3-hd-charon --no-assign`. Değişmeyen 10 cümle kendi dosyasıyla yeni sıraya taşınır, 9 yeni cümle sentezlenir, çevirileri alınır.
3. Hizalama betiği: `align-word-timings.py --prod --apply --reading-text-id 1036` (yalnız zamanlaması olmayan 9 klibi işler).
4. `SantoriniRewrite_2026_11_28_OPEN.sql`: 19/19 klip doğru metinle, sesli ve zamanlamalı mı, değişmeyen 10 cümle eski dosyayı mı gösteriyor, yeni 9'un adı şemaya uyuyor mu; hepsi tutarsa metni açar, tutmazsa kapalı bırakır.
5. Uygulamada baştan sona dinleme, kısa kayıt ya da görüntü.

Kapalı kalma süresi birkaç dakika. Son 30 günde metnin 1 okuru var.

**Geri alma:** `SantoriniRewrite_2026_11_28_REVERT.sql` eski metni, 17 eski klip kaydını (zamanlamalarıyla), quizi geri yazar, balon kayıtlarını siler. Eski ses dosyaları silinmediği için ses de eski hâline döner.

**Yedek:** canlıdan salt okuma ile alındı (28 Kas 13:30): metin 1, klip kaydı 17, quiz sorusu 4, cevap 14. Geliştirici makinesinde, depo dışında. Yazma betiği aynı satırları ayrıca canlıda yedek tablolara alır.

**Sınandı:** üç betik, canlı yedeğinden kurulan yerel bir veritabanında sırayla denendi: ilk yazım ve ikinci kez çalıştırma (değişiklik yok), ses yokken açma (reddetti, 4/19), zamanlama yokken açma (reddetti, 10/19), tam hâlde açma (açtı), geri alma (metin md5'i ve 17 klibin hash, sıra, zamanlaması eskisiyle aynı).

## Bilinmesi gerekenler
- Betik dosyaları sunucu deposunda `chore/santorini-rewrite` dalında, henüz commit'lenmedi (editörün commit'i engellendi; Mehmet'in sözüyle yapılır). Üç dosyanın izin kuralı eklendi.
- Saklı cümle tokenları (`ReadingTextSentences`) bu metin için zaten yok; uygulama kullanmıyor. Etkilenmez.
- Başlangıç metni bu işte **değişmiyor** (ayrı adım; bkz. `veri_2026-11-27_metin_zorlugu/08_baslangic_ikinci_adim.md`).

## Yazımdan sonra (28 Kas, 13:38–13:45)
| Adım | Sonuç |
|---|---|
| 1. Metin, quiz, balonlar | Yazıldı; yedek tablolar canlıda (metin 1, klip 17, soru 4, cevap 14). Kelime sayısı 182 |
| 2. Ses | 6 cümle mevcut dosyayla yeni sıraya taşındı, 9 cümle aynı sesle (`chirp3-hd-charon`) üretildi; 19/19 |
| 3. Kelime zamanlaması | 9/9 klip hizalandı, doğrulamayı geçemeyen 0 |
| 4. Açma | Denetim geçti (19/19 doğru metin, ses, zamanlama; değişmeyen 10 cümle eski dosyada), metin açık |
| 5. Uygulama yolu | Sunucunun istemciye verdiği manifest ("default" ses, salt okuma) 19/19 tam |

**Dosya denetimi (19 klibin hepsi indirildi):** süreler kayıtla birebir; her klibin kelime zamanlaması cümlenin kelimeleriyle birebir; ses seviyesi yeni kliplerde −19,8 ile −23,5 dB, eskilerde −17,4 ile −23,4 dB arasında, yani aynı aralıkta. Geçişte ses farkı beklenmiyor.

**Uygulamada dinleme yapılamadı:** geliştirici makinesinde 2,1 GB boş yer var, simülatör derlemesi sığmıyor; telefon bağlı değil. Yerine 19 klip sırayla tek dosyada birleştirildi (73 sn, Mehmet'in masaüstünde `santorini_yeni_ses_2026_11_28.mp3`). Uygulamada baştan sona dinleme Mehmet'te: değişen cümlelerde (1, 2, 6, 7, 9, 10, 14, 15, 18) kelime vurgusu sesle gidiyor mu.

**Çeviri notu:** geliştirici makinesinde DeepL anahtarı olmadığı için cümle çevirileri üretim sırasında alınmadı. Etkisi yok: uygulama çeviriyi okur cümleye dokununca sunucudan istiyor, sunucuda anahtar var, boş önbellek kaydı yeniden çevriliyor. Eski metinde de 17 cümlenin yalnız 4'ünün hazır çevirisi vardı.

## Mehmet'ten beklenen
1. ~~Dinleme~~ yapıldı, onaylandı.
2. Başlangıç metni değişikliği (ayrı adım) için karar.
