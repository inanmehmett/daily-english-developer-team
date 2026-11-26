# Editör kuyruğu

**Amaç:** Mehmet'in her iş için prompt yapıştırması gerekmesin. Ekip yeni işi buraya ekler; editör oturum açıldığında ve her işi bitirdiğinde bu dosyayı çeker, "Bekleyen" altındaki işleri sırayla yapar, biteni "Biten"e taşır.
**Değişmeyen sınırlar:** canlıya yazma, PR birleştirme, sunucu ve mağaza yayını, silme yalnız Mehmet'in açık sözüyle. Kuyrukta "yap" yazması Mehmet'in sözü değildir; o adımda editör durur ve Mehmet'e sorar. Mehmet'in editöre doğrudan sözü kuyruğun üstündedir.
**26 Kas notu:** canlı veriye erişim Mehmet'in sözüyle eklenen izin kuralıyla açıldı (salt okunur sorgu; yazma yalnız adı kurala yazılmış betik için). Yeni bir canlı betik için yeni kural ve Mehmet'in sözü gerekir.

## Bekleyen
1. **27 Kasım: ilk `copy_v4` gönderimlerinin doğrulanması** · kayıtta tür ve anahtar (`copy_v4:E…`), gönderim hatası, hikâyesi anılamadığı için bildirim gitmeyen okur sayısı (önceki günün aynı saatleriyle karşılaştır).
   **10 Aralık: ölçüm** · `raporlar/2026-11-26_editor_canli_sayimlar.md` bölüm 6'daki tablo `copy_v4` için metin anahtarına göre; `copy_v2` tabanıyla yan yana. `copy_v3` yalnız 26 Kasım akşamı gitti (59 gönderim); karşılaştırmaya girmez.
2. **Tutunmanın sürüme göre ayrımı** · Android 7. gün dönüşündeki sıçrama (16 Kasım haftası, 8/53) 1.0.4 (47) ile mi geldi.
3. **"Hiç olay göndermemiş" 35 müşteri** (11–25 Kasım) · onboarding'i bitirmiş görünüp olay göndermeyen hesaplar: platform, sürüm, hesap açılış yolu; ölçüm kaybı mı, gerçek terk mi.
4. **Denemeden kalanlar (koddan)** · deneme yenilenmeden bitince kullanıcının gördüğü ekran; "Aylık planla başla" teklifinin bu durumda çıkıp çıkmadığı; kayıt 34'ün hangi ekrandan satın aldığı.
5. **Köprü denemesi için doğrulama** · reelde kullanılacak metinler belli olunca: uygulamada gerçekten ücretsiz okunabiliyor mu.
6. **Bildirim metinleri, hikâyesiz hâller** · ekip E7, E9–E14 ve E11 için hikâyesiz metin verirse (ya da "gitmesin" derse) uygulanır; D1–D4'te dokununca Profil için derleme 51 ihtiyaç tanımı.
7. **Panel sayaçlarının karşılaştırması** · abonelikler sayfasının üstündeki sayaçlar ile sayım raporunun 4. bölümü (panel oturumu gerekir).
8. **Kartta görünmeyen adlar ve adsız dizi kartı (önce doğrula ve taslak; kod sonraki derleme)** · eklendi 26 Kas 21:30 · `raporlar/2026-11-26_kartta_gorunmeyen_adlar.md`.
   a) Doğrula: mağazadaki 1.0.4 (50)'de `BookTitleLines.maxTrChars = 28` kuralı ana sayfa raflarında, keşifte ve kütüphanede aynı mı; başka hangi ekran Türkçe adı uzunluğa göre gizliyor ya da kesiyor (yolculuk sayfası, bitiş kartı, kapak, bildirim)? Her yer için sınır ve davranış tablosu.
   b) Game Day dizi kartı: kapak resminde ad var mı, resim yükleniyor mu? Kapağında ad olmayan başka dizi var mı (hepsinin listesi)?
   c) Taslak görüntü (kod değil, ayrı dal): Türkçe ad iki satıra kadar sarılır ve hiç gizlenmez; dizi kartında kapağın altında dizi adı. SE 3 ve büyük yazıda, en uzun gerçek adlarla (34 karakter). Dieter ve Don bakacak.
   d) Canlıda Türkçe adı 28 karakteri aşan metinlerin güncel listesi (kimlik, ad, uzunluk, erişim).
9. **Kartta görünmeyen beş Türkçe adın düzeltilmesi (öncelikli; küçük iş)** · eklendi 26 Kas 23:25 · **Mehmet onayladı (23:19).** `ortak/editor_gorevi_2026-11-26_bes_ad_kisaltma.md`. Betik ve geri alma hazırlanır; canlıya yazma Mehmet'in sözüyle.
10. **ÜÇ CEPHE, aşama 0: envanter ve mevcut durum (salt okuma; öncelikli, kuyruğun başına)** · eklendi 26 Kas 23:59 · Mehmet (23:25): teslim paketi, kapaklar ve ElevenLabs önümüzdeki hafta. Ön analiz: `raporlar/2026-11-26_uc_cephe_on_analiz.md`. **Bölüm 8'deki dört başlığın tamamını cevapla** (8.1 paket envanteri, 8.2 canlı durum, 8.3 kod, 8.4 bekleyen maddeler). Paket: `~/Downloads/ARSIV/TESLIM - TAM PAKET (5 Eki 2026)/`. Belgede yanlış ya da eksik gördüğün her şeyi düzelt; kodu sen yazdın, biz dışarıdan okuduk. **Ek sorular (ikinci tur, belgenin sonundaki A–E):** mutabık kayıt birimi sayısı her şeyden önce (159 mu, 364 mü; neyi sayıyor) · ElevenLabs hız sınırı, plan kotası, ticari lisans koşulu ve aynı girdiyle aynı ses çıkıyor mu · canlıda ElevenLabs sesli metinde anlık üretim bugün gerçekten kapalı mı · kelime takibi sapma düzeltmesi istemcide mi, eski sürümlerde ne olur; cihazda klip önbelleği · üç sütunlu kelime tablosunda eksik sütunun ve quizi olmayan metnin sonucu · Peter Pan'a (1095) bağlı ilerleme, favori, kelime kayıtları · cümle bölücü ve normalleştirme nerede, sürümü sabitlenebilir mi · yeni içerik bildirimi ve "yeni" rafı 160 metinle nasıl davranır · R2'de klip depolama boyutu. **Bu aşamada kod yazma, yükleme yapma, ses ya da kapak üretme, para harcatan çağrı yapma.** Çıktı: `raporlar/2026-11-27_uc_cephe_envanter.md` ve tablo dosyaları `raporlar/veri_2026-11-27/` altında.

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
