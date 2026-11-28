# Editör kuyruğu

**Amaç:** Mehmet'in her iş için prompt yapıştırması gerekmesin. Ekip yeni işi buraya ekler; editör oturum açıldığında ve her işi bitirdiğinde bu dosyayı çeker, "Bekleyen" altındaki işleri sırayla yapar, biteni "Biten"e taşır.
**Değişmeyen sınırlar:** canlıya yazma, PR birleştirme, sunucu ve mağaza yayını, silme yalnız Mehmet'in açık sözüyle. Kuyrukta "yap" yazması Mehmet'in sözü değildir; o adımda editör durur ve Mehmet'e sorar. Mehmet'in editöre doğrudan sözü kuyruğun üstündedir.
**26 Kas notu:** canlı veriye erişim Mehmet'in sözüyle eklenen izin kuralıyla açıldı (salt okunur sorgu; yazma yalnız adı kurala yazılmış betik için). Yeni bir canlı betik için yeni kural ve Mehmet'in sözü gerekir.

## Bekleyen
> **Sıra kuralı (28 Kas, ekip):** "kuyruğu çalıştır" denince editör numara sırasına değil bu gruplara bakar. "Önce" bitmeden "Sonra"ya geçmez; "Bekliyor" altındakileri koşulu yazılmadan yapmaz. Her işin numarası değişmez (raporlar numarayla gönderme yapıyor). Oturum sınırına yaklaşınca yarım işi bırakmaz; bitirdiğini Biten'e yazar, kalanı not eder.
> Bekleme nedenleri: 5 köprü reelinin metinleri belli değil · 6 ekip hikâyesiz metinleri vermedi · 7 panel oturumu Mehmet'te.

### Önce (bu sırayla; 1. hafta yol haritası)
10. **ÜÇ CEPHE, aşama 0: envanter ve mevcut durum (salt okuma; öncelikli, kuyruğun başına)** · eklendi 26 Kas 23:59 · Mehmet (23:25): teslim paketi, kapaklar ve ElevenLabs önümüzdeki hafta. Ön analiz: `raporlar/2026-11-26_uc_cephe_on_analiz.md`. **Bölüm 8'deki dört başlığın tamamını cevapla** (8.1 paket envanteri, 8.2 canlı durum, 8.3 kod, 8.4 bekleyen maddeler). Paket: `~/Downloads/ARSIV/TESLIM - TAM PAKET (5 Eki 2026)/`. Belgede yanlış ya da eksik gördüğün her şeyi düzelt; kodu sen yazdın, biz dışarıdan okuduk. **Ek sorular (ikinci tur, belgenin sonundaki A–E):** mutabık kayıt birimi sayısı her şeyden önce (159 mu, 364 mü; neyi sayıyor) · ElevenLabs hız sınırı, plan kotası, ticari lisans koşulu ve aynı girdiyle aynı ses çıkıyor mu · canlıda ElevenLabs sesli metinde anlık üretim bugün gerçekten kapalı mı · kelime takibi sapma düzeltmesi istemcide mi, eski sürümlerde ne olur; cihazda klip önbelleği · üç sütunlu kelime tablosunda eksik sütunun ve quizi olmayan metnin sonucu · Peter Pan'a (1095) bağlı ilerleme, favori, kelime kayıtları · cümle bölücü ve normalleştirme nerede, sürümü sabitlenebilir mi · yeni içerik bildirimi ve "yeni" rafı 160 metinle nasıl davranır · R2'de klip depolama boyutu. **Bu aşamada kod yazma, yükleme yapma, ses ya da kapak üretme, para harcatan çağrı yapma.** Çıktı: `raporlar/2026-11-27_uc_cephe_envanter.md` ve tablo dosyaları `raporlar/veri_2026-11-27/` altında.
11. **Başlangıç metinlerinde balon ne gösteriyor (yalnız okuma)** · eklendi 27 Kas 22:15 · gerekçe: `raporlar/2026-11-27_metin_kalitesi_pilot.md`, Ek 2 · çıktı: `raporlar/veri_2026-11-27_metin_zorlugu/07_balon_anlamlari.md`


   1. Üç başlangıç metninin (916, 1083, 1023) ve 120'nin (Why Penguins Can't Fly) en çok dokunulan 20 kelimesi için: balonda okura gösterilen Türkçe anlam, kelimenin geçtiği cümleyle yan yana. Özellikle 916'da "flat" ("the sea was grey and flat"), "still", "stood", "above", "gone"; 1083'te "rock", "count", "hands", "steps".
   2. Anlam cümleye göre mi seçiliyor, kelimeye göre tek anlam mı geliyor? Nereden geldiğini bir cümleyle yaz.
   3. Bir kullanıcının ilk metni hangi kurala göre seçiliyor (seviyeye göre hangi metin)? B1 seçen kullanıcının ilk metni bugün hangisi?
12. **Başlangıç metinleri, 2. adım: Santorini ve B1 (yalnız okuma)** · eklendi 27 Kas 23:30 · gerekçe: `raporlar/2026-11-28_a2_baslangic_adaylari.md` · çıktı: `raporlar/veri_2026-11-27_metin_zorlugu/08_baslangic_ikinci_adim.md`
   1–2. *Bitti (28 Kas), Biten'de.*
   3. B1 seçen müşterilerde: ilk metni Rabbit Island olanlar ile Why Penguins olanlar; bitirme, ikinci metne başlama, ertesi gün dönüş (aynı yöntemle, `02_ilk_metinden_sonra.md`).
   4. B1 metinlerinin dökümü (`veri_2026-11-21/A2_metinleri.md` biçiminde), en azından 120, 1024, 1089, 161, 1019 ve ücretsiz B1'ler.
   5. 1089 The Train with No Driver: 21 Kasım'da A2, 27 Kasım'da B1 görünüyor; etiket ne zaman, kimce değişti.
   6. 127 Ali's First Snow ve 140 A Bus Ride with a Stranger: konuşmalarda tırnak işaretleri yok; aynı sorunlu başka metin var mı (liste).

13. **Santorini (1036): metin değişikliği ve aynı sesle güncelleme** · eklendi 28 Kas 12:55 · Mehmet (12:50): "değişiklikleri yaptıktan sonra ses dosyaları da güncellenmeli. Aynı ses dosyaları ile güncellenebilir. Şu an Santorini sesi fena değil." · metin: `raporlar/2026-11-28_a2_baslangic_adaylari.md`, "Son hâl" · çıktı: `raporlar/2026-11-28_santorini_degisiklik.md`
   **Durum (28 Kas 13:45):** 1, 4 ve 5'in yedek kısmı bitti; betikler hazır ve yerelde sınandı. Canlıya yazma **Mehmet'in "yap"ını bekliyor** (9 cümle, 9 klip, 3 sentin altında). 6 ve 7 sonra.
   1. Hazırlık (12.1 ve 12.2 ile birlikte, yalnız okuma): metnin bugünkü sesi hangi sağlayıcı ve hangi ses (ses kimliği, hız); kaç cümle değişiyor, kaç klip yeniden üretilecek, kaç klip olduğu gibi kalacak; karakter sayısı ve tahmini maliyet. Dosya adı (özet) şemasının aynı kaldığını bir cümlede doğrula, yoksa değişmeyen cümleler de boşuna yeniden üretilir.
   2. **Ses kuralı:** yeni cümleler bugünkü sesle (aynı sağlayıcı, aynı ses, aynı hız) üretilir. Başka ses ya da ElevenLabs yok. Değişmeyen cümlelerin klipleri korunur.
   3. Ses kullanıcı metni açınca anlık değil, **önceden** üretilir; ardından hizalama betiğiyle kelime zamanlaması çıkarılır. Metin, bütün cümlelerin sesi ve zamanlaması hazır olmadan okura bu hâliyle açılmaz.
   4. Kelime anlamları ve quiz: değişen cümlelerde balon anlamı ve quiz soruları yeni metne uyuyor mu; uymayanlar listelenir ve düzeltilir (eski "ring", "mouth", "crater", "eruptions" geçen soru ya da anlam kalmasın).
   5. Önce yedek (eski metin, eski klip kayıtları), sonra canlıya yazma. **Canlıya yazmadan ve klipleri canlıya taşımadan önce dur, Mehmet'e "yap" diye sor.**
   6. Doğrulama: uygulamada metin baştan sona dinlenir; değişen cümlelerde ses ile vurgu uyumlu mu, cümle geçişlerinde ses farkı duyuluyor mu. Görüntü ya da kısa kayıt.
   7. Başlangıç metni değişikliği (A2 okurun ilk metni Santorini) **ayrı adım**: 12.2'nin cevabıyla, yine Mehmet'in "yap"ıyla. Ses ve metin hazır olmadan başlangıç değişmez.

### Sonra (sıra serbest, yer kalırsa)
1. **27 Kasım akşamı: `copy_v4` ikinci bakış** · sabah kontrolü yapıldı (Biten'de). Asıl hacim 20:00–21:00'de: seri bildirimleri (E1, E2) ve "son hatırlatmamız"tan sonra susma kuralının kayıtta görülmesi.
   **10 Aralık: ölçüm** · `raporlar/2026-11-26_editor_canli_sayimlar.md` bölüm 6'daki tablo `copy_v4` için metin anahtarına göre; `copy_v2` tabanıyla yan yana. `copy_v3` yalnız 26 Kasım akşamı gitti (59 gönderim); karşılaştırmaya girmez.
2. **Tutunmanın sürüme göre ayrımı** · Android 7. gün dönüşündeki sıçrama (16 Kasım haftası, 8/53) 1.0.4 (47) ile mi geldi.
3. **"Hiç olay göndermemiş" 35 müşteri** (11–25 Kasım) · onboarding'i bitirmiş görünüp olay göndermeyen hesaplar: platform, sürüm, hesap açılış yolu; ölçüm kaybı mı, gerçek terk mi.
4. **Denemeden kalanlar (koddan)** · deneme yenilenmeden bitince kullanıcının gördüğü ekran; "Aylık planla başla" teklifinin bu durumda çıkıp çıkmadığı; kayıt 34'ün hangi ekrandan satın aldığı.
9. **Kartta görünmeyen beş Türkçe ad: kalan tek adım görüntü** · adlar canlıda (27 Kas 15:01, Biten'de). Kalan: uygulamada beş kartın Türkçe adının göründüğünün görüntüyle doğrulanması.
8. **Kartta görünmeyen adlar ve adsız dizi kartı (önce doğrula ve taslak; kod sonraki derleme)** · eklendi 26 Kas 21:30 · `raporlar/2026-11-26_kartta_gorunmeyen_adlar.md`.
   a) Doğrula: mağazadaki 1.0.4 (50)'de `BookTitleLines.maxTrChars = 28` kuralı ana sayfa raflarında, keşifte ve kütüphanede aynı mı; başka hangi ekran Türkçe adı uzunluğa göre gizliyor ya da kesiyor (yolculuk sayfası, bitiş kartı, kapak, bildirim)? Her yer için sınır ve davranış tablosu.
   b) Game Day dizi kartı: kapak resminde ad var mı, resim yükleniyor mu? Kapağında ad olmayan başka dizi var mı (hepsinin listesi)?
   c) Taslak görüntü (kod değil, ayrı dal): Türkçe ad iki satıra kadar sarılır ve hiç gizlenmez; dizi kartında kapağın altında dizi adı. SE 3 ve büyük yazıda, en uzun gerçek adlarla (34 karakter). Dieter ve Don bakacak.
   d) Canlıda Türkçe adı 28 karakteri aşan metinlerin güncel listesi (kimlik, ad, uzunluk, erişim).

### Bekliyor (koşulu gelmeden yapma, atla)
5. **Köprü denemesi için doğrulama** · reelde kullanılacak metinler belli olunca: uygulamada gerçekten ücretsiz okunabiliyor mu.
6. **Bildirim metinleri, hikâyesiz hâller** · ekip E7, E9–E14 ve E11 için hikâyesiz metin verirse (ya da "gitmesin" derse) uygulanır; D1–D4'te dokununca Profil için derleme 51 ihtiyaç tanımı.
7. **Panel sayaçlarının karşılaştırması** · abonelikler sayfasının üstündeki sayaçlar ile sayım raporunun 4. bölümü (panel oturumu gerekir).

## Biten
| İş | Tarih | Sonuç |
|---|---|---|
| 25 Kasım görevi, koddan cevaplananlar (A6, A8, A9, A10'un bir kısmı) | 26 Kas | `raporlar/2026-11-26_editor_cevap.md` |
| B1 şıkların karıştırılması; B2 dört yeni B2 sorusu ve iki şık düzeltmesi | 26 Kas | Sunucu PR #21, **canlıda** (26 Kas 17:22) |
| B4 | 26 Kas | 3 gün arası PR #15 ile düzelmiş; "adlı başlık" maddesi Mehmet'in 26 Kasım yönüyle geçersiz |
| Onaylı ad değişiklikleri: doğrulama, eski adların geçtiği yerler, betik ve geri alma | 26 Kas | Sunucu PR #22; `raporlar/2026-11-26_editor_ad_degisiklikleri.md`. Canlıda çalıştırma 4. işte |
| Denemede yenilemeyi kapatanlar: c (koddan) | 26 Kas | Editör cevabı, "Kuyruk 2" |
| Abonelikler sayfası: a, b (koddan) | 26 Kas | Editör cevabı, "Kuyruk 3"; ödeme türü sütunu önerisi Dieter'de |
| Bildirimler: döküm (d), dokununca ne açıldığı (e), üç hazırlık sorusu; taslak 3'ün uygulanması | 26 Kas | Sunucu PR #23, **canlıda** (26 Kas 17:30); editör cevabı, "Bildirim dökümü" |
| Uygulama deposu: mağazadaki sürüm `main`'e | 26 Kas | Uygulama PR #5, birleşti (26 Kas) |
| Canlı sayımlar: A1, A2, A3, A4, A5, A7, A11; deneme ve yenileme dökümü (2a, 2b, 2d); abonelik kayıtları (3d, 3e) | 26 Kas | `raporlar/2026-11-26_editor_canli_sayimlar.md` |
| PR #21 canlıda doğrulama (B3) | 26 Kas | Havuz istenen hâlde; karışık şık sırası ilk gerçek denemede görülecek |
| Ad betiğinin canlıda çalıştırılması | 26 Kas | 15 satır, yedekli; `raporlar/2026-11-26_editor_ad_degisiklikleri.md` |
| Bildirim metinleri, onaylı son hâl (`copy_v4`): doğrulama tablosu, kod, testler | 26 Kas | Sunucu PR #24, **canlıda** (26 Kas 23:20); `raporlar/2026-11-26_editor_bildirim_metinleri.md` |
| `copy_v4` ilk gönderimlerin doğrulanması (27 Kas, 14:56) | 27 Kas | 26 gönderim, hepsi anahtarlı; 1 dokunma; 2 "Unregistered" hata; günlük temiz. `raporlar/2026-11-26_editor_bildirim_metinleri.md` son bölüm |
| Kartta görünmeyen beş Türkçe adın kısaltılması: betik, yayın, canlıya yazma | 27 Kas | Sunucu PR #25 canlıda (14:57), betik çalıştırıldı (15:01), beş satır doğrulandı. `raporlar/2026-11-26_editor_ad_degisiklikleri.md` (ek) |
| 11. Metin zorluğu verisi (altı madde, yalnız okuma) | 27 Kas | `raporlar/veri_2026-11-27_metin_zorlugu/` (README'de özet). Mağaza yorumları okunamadı; beş şey tutulmuyor |
| 12.1 Santorini: erişim, ses, anlamlar, son hâlin etkisi · 12.2 başlangıç metni kod mu veri mi | 28 Kas | Premium, 17/17 sesli ve zamanlamalı, bağlı anlam yok. Başlangıç: kural kodda (seviyedeki en kısa açık metin), değiştirmek veri (`IsStarterPack`). `raporlar/veri_2026-11-27_metin_zorlugu/08_baslangic_ikinci_adim.md` |
| 13.1 Santorini hazırlığı ve yedek | 28 Kas | 9 cümle yeni, 10 klip korunur, ses aynı (`chirp3-hd-charon`, 0,94), 3 sentin altında; quizde 3 soru, 6 balon düzeltmesi. Yazma "yap" bekliyor. `raporlar/2026-11-28_santorini_degisiklik.md` |
