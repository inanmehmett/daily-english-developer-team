# Ücretsiz sınırlar kime değiyor

**Rol:** Nate Gümüş (veri). **Tarih:** 17 Kasım 2026.
**Görev:** `ortak/editor_gorevi_2026-11-17_ucretsiz_sinirlar.md`. Yalnız okuma yapıldı. Bağlantı `default_transaction_read_only = on` ile açıldı; canlıda hiçbir satır değişmedi. Kod ya da veritabanı değişikliği yok.

## En üstte beş satır

1. **Günlük okuma sınırı canlıda hiç uygulanmıyor.** Ne Flutter'daki "günde 3", ne sunucudaki "günde 1" çalışıyor. Okuma sayacını artıran iki fonksiyonu (istemcide `useReadingQuota`, sunucuda `UseReadingQuotaOnCompletionAsync`) çağıran hiçbir yer yok. 268 müşterinin hepsinde `TodayReadingCount` = 0 ve `LastReadingDate` boş. Okumayı fiilen sınırlayan tek şey içerik kilidi: 3 açık metin ve günde 1 açma.
2. **Çeviri sınırına (25) neredeyse kimse çarpmıyor, çünkü sunucu her dokunuşu saymıyor.** Hak, kelime sözlükte yoksa (DeepL'e gidecekse) ve önbellekte olmayan cümle çevirisinde düşüyor. Müşterilerin 89 gününde 25'ten fazla kelime dokunuşu var. Ama son çeviri günündeki gerçek sayaç ortanca 3. Sınıra çarptığı görülen tek kişi var.
3. **Defter sınırı (15 kelime, ilk 7 gün sınırsız) kimseyi durdurmuş görünmüyor.** 7 günden eski 144 müşteriden 17'si ilk haftada 15 kelimeyi geçti. Bunlardan yalnız 2'si 7. günden sonra uygulamaya döndü.
4. **Kilit herkese değiyor.** 268 müşterinin 69'u kilitli bir metne ya da bölüme dokundu. 46 kişi günlük açma hakkını en az bir kez kullandı.
5. **Alıcılar ve tamamlamayanlar satın almadan önce sınıra çarpmamıştı.** 14 kişiden hiçbiri, basmadan önce çeviri ya da defter sınırına çarpmamıştı. Okuma sınırı ise hiç yok. Ortak tek temas kilitli içerik: 14 kişinin 8'i basmadan önce kilitli bir metne ya da bölüme dokunmuştu.

## Yöntem

- **Kimler:** `Users.AccountKind = 'customer'`, 268 hesap. Kayıt anı `UserProfiles.CreatedAt`. Gün UTC+3; sunucunun çeviri sayacı da UTC+3 gününe göre sıfırlanıyor (`UserUsageQuota.ResetDailyIfNeeded`).
- **Dokunma:** `word_lookup` olayı, yani kullanıcının kelime balonu açması. Bu, sunucunun düştüğü hak değil (bkz. S1).
- **Gerçek düşen hak:** `UserUsageQuotas.TodayTranslationCount`. Tablo geçmiş tutmuyor; yalnız kişinin son çeviri günündeki sayıyı saklıyor.
- **Sınıra çarpma kaydı:** `AuditLogs`'ta `TranslationLimitReached` müşteride 0 satır. Bu kayıt yalnız kullanılmayan `/use-translation` ucunda yazılıyor; balonun kullandığı `TranslateWord` ucu 402 dönerken kayıt yazmıyor. İstemci de çeviri, defter ve okuma sınırı sayfalarında olay göndermiyor. Bu yüzden "sınıra çarptı" ancak dolaylı ölçülebiliyor.
- Müşteri satırları yerel bir çalışma veritabanına kopyalandı (e-posta ve ad yok), sorgular orada koştu. Kopya iş bitince silindi.

## S1. Kelime dokunuşu ve çeviri sınırı

Kişi-gün başına `word_lookup` sayısı (en az bir dokunuşun olduğu günler):

| | Değer |
|---|---|
| Dokunuşlu gün / kişi | 242 gün / 174 kişi |
| Ortanca | 17 |
| %75 | 35 |
| %90 | 65 |
| En çok | 170 |
| 25 ve üzeri dokunuşlu gün | 89 gün, 74 kişi |
| Cümle çevirisiyle birlikte 25 ve üzeri | 103 gün, 80 kişi |

25 ve üzeri dokunuşlu gün sayısı kişi başına: 1 gün 64 kişi, 2 gün 7 kişi, 3 gün 1 kişi, 4 gün 2 kişi.

Sunucuda gerçekten düşen hak (her kişinin son çeviri günü; 92 kişide sıfırdan büyük):

| | Değer |
|---|---|
| Ortanca | 3 |
| %90 | 8 |
| 18 ve üzeri | 2 kişi |
| 25'e ulaşan | 1 kişi |

O 92 kişi-günde 3.262 dokunuş ve 496 cümle çevirisi var; düşen hak toplamı 344. Sınıra ulaşan tek kişi (Android) o gün 20 kelimeye ve 28 cümleye bakmış. Yani hakkı asıl cümle çevirisi tüketiyor; kelime dokunuşlarının çoğu sözlükten geliyor ve hak düşürmüyor.

Dokunuş düzeyine göre o günden sonrası:

| Günlük dokunuş | Kişi-gün | O gün paywall gördü | Ertesi gün döndü |
|---|---|---|---|
| 1–9 | 83 | 21 | 12/71 (%17) |
| 10–24 | 70 | 27 | 21/53 (%40) |
| 25+ | 89 | 34 | 25/74 (%34) |

Okuma: "25 dokunuşa çarpan" günlerde kullanıcı sınırı görmedi; sunucu o dokunuşların çoğunu saymadı. Bu yüzden son tablo sınırın etkisini değil, çok okuyan günü gösteriyor. Ertesi gün dönüş oranı 10–24 ve 25+ dokunuşlu günlerde benzer. Bu bir **bağıntıdır**.

## S2. İlk metinde dokunma

İlk biten metin (`reading_completed`), metnin ilk açılışından bitişine kadarki dokunuşlar. 97 kişi:

| Metin seviyesi | Kişi | Ortanca | %75 | %90 | En çok |
|---|---|---|---|---|---|
| A1 | 49 | 12 | 19 | 34 | 167 |
| A2 | 22 | 19,5 | 48,5 | 56 | 66 |
| B1+ | 26 | 19,5 | 30 | 48,5 | 87 |
| Hepsi | 97 | 16 | | | |

Sınır her dokunuşu saysaydı, ilk metnini dokunuş sınırına çarpmadan bitirebilecek olanlar:

| Sınır | A1 | A2 | B1+ | Hepsi |
|---|---|---|---|---|
| 10 | 24/49 (%49) | 3/22 (%14) | 9/26 (%35) | 36/97 (%37) |
| 15 | 32/49 (%65) | 6/22 (%27) | 10/26 (%38) | 48/97 (%49) |
| 20 | 37/49 (%76) | 12/22 (%55) | 14/26 (%54) | 63/97 (%65) |
| 25 (bugünkü sayı) | 41/49 (%84) | 12/22 (%55) | 18/26 (%69) | 71/97 (%73) |

İlk metinlerin çoğu üç metinden geliyor: Two Cups (A1, 42 kişi, ortanca 12,5), Why Penguins Can't Fly (B1, 23 kişi, ortanca 22) ve The Island Where Rabbits Won (A2, 21 kişi, ortanca 19).

Okuma: tablo, sınırın her dokunuşu saydığı varsayımına dayanıyor. Bugünkü sunucu kuralında sözlükteki kelimeler sayılmadığı için ilk metinde sınıra çarpan neredeyse yok. A2 grubunun 22 kişiden ibaret olması ve bunların neredeyse hepsinin aynı metni okuması (Rabbits) sonucu o metne bağlıyor.

## S3. Kelime defteri

| | Değer |
|---|---|
| En az bir kelime kaydeden | 92/268 |
| Kaydedenlerde ortanca | 8 |
| %75 | 18 |
| %90 | 31 |
| En çok | 88 |
| 15'i geçen | 28 kişi |
| İlk gün kelime kaydeden | 76 kişi, ortanca 7 kelime |
| İlk gün 15'i geçen | 18 kişi |

| Toplam kayıtlı kelime | Kişi |
|---|---|
| 0 | 176 |
| 1–5 | 38 |
| 6–15 | 26 |
| 16–30 | 18 |
| 31+ | 10 |

7. günden sonra sınır:
- Kaydı 7 günden eski olan müşteri 144.
- Bunlardan ilk haftada 15 kelimeyi geçen (yani 8. günde sınırda olan) 17 kişi. Bu 17 kişiden 7. günden sonra uygulamaya dönen 2 kişi; ikisi de o günlerde kelimeye baktı.
- 7. günden sonra kelime kaydeden 4 kişi var: biri abone; biri tam 15'e ulaştı; ikisi sınırın altında.

Defter sınırına çarpma kaydı olmadığı için "kaydetmeye çalışıp duvara çarpan" sayılamıyor. Sınırda olup geri dönenlerin sayısı (2) üst sınırdır.

Okuma: 15 kelimelik sınır, ilk haftayı geçen az sayıdaki kullanıcıya değiyor. Sınıra gelen kullanıcıların çoğu 7. günden önce gitmiş oluyor.

## S4. Okuma kilidi ve günlük açma

| | Kişi | Olay |
|---|---|---|
| Kilitli bir metne ya da bölüme dokunan (herhangi biri) | 69 | |
| Kilitli kitap önizlemesi açtı (`locked_book`, `preview_opened`) | 61 | 156 |
| Kilitli dizi bölümüne dokundu (`locked_series_episode`) | 44 | 241 |
| Kilitli kitapta "Premium" düğmesine bastı (`preview_cta`) | 5 | 7 |
| Günlük açma hakkını kullandı (`FreeTextUnlocks`) | 46 | 64 açma, 18 farklı metin |

Günlük açmayı kaç kez kullandı: 1 kez 40 kişi, 2 kez 1, 3 kez 1, 4 kez 2, 5 kez 1, 6 kez 1.

Okuma: kilit, ücretsiz kullanıcının en sık değdiği sınır. Günlük açmayı kullananların çoğu bir kez kullanmış.

## S5. Okuma sınırında tutarsızlık: canlıda hangisi uygulanıyor

**Hiçbiri.** Canlıda okumayı yalnız erişim kuralı sınırlıyor.

| Yer | Ne diyor | Canlıda ne oluyor |
|---|---|---|
| Flutter `freemium_limits.dart` | 7. günden sonra günde 3 okuma | Bu sabit yalnız onboarding paywall'unun metninde geçiyor ("Günlük 3 okuma limiti kalkar"); hiçbir şeyi engellemiyor. |
| Sunucu `GET /api/ApiUserProfile/freemium-status` | Günde 1 (`limit = 1`, `canRead = TodayReadingCount < 1`) | `TodayReadingCount` hiç artmıyor; `canRead` herkes için her zaman `true`. |
| Sunucu `POST use-reading-quota` ve `UseReadingQuotaOnCompletionAsync` | Okuma hakkını düşer (7. günden sonra) | İkisini de çağıran yer yok. Müşterilerin hepsinde `TodayReadingCount = 0`, `LastReadingDate = boş`. |
| Sunucu `ReadingTextsController.CanAccessReadingTextAsync` | `IsStarterPack` açık; `IsDailyUnlock` metni günde 1 açılabilir; gerisi premium | **Uygulanan tek kural budur.** |

Okuyucu her açılışta `freemium-status` soruyor ve `canRead` her zaman doğru döndüğü için "günlük okuma hakkın bitti" sayfası canlıda hiç açılmıyor. Okuma sonrası çıkan teklif penceresi ise kalan hakkı aynı uçtan okuyor (1 − 0). Bu yüzden ilk 7 günden sonra her okumanın ardından "1 okuma hakkın kaldı" yazabilir. Bu satır koddan çıkarıldı; ekranda görülmedi.

## S6. Alıcılar ve tamamlamayanlar satın almadan önce sınıra çarpmış mıydı

| | Platform | Basmadan önce bir günde en çok dokunuş | Basmadan önce defterdeki kelime | 7. günden sonra mı | Kilitli içeriğe dokunuş | Günlük açma | Son çeviri günündeki gerçek sayaç |
|---|---|---|---|---|---|---|---|
| A (alıcı) | iOS | 0 | 0 | hayır | 0 | 0 | 0 |
| B (alıcı) | iOS | 15 | 30 (ilk hafta, sınırsız) | hayır | 1 | 0 | 7 |
| C (alıcı) | iOS | 0 | 0 | hayır | 0 | 0 | 0 |
| D (alıcı) | iOS | 0 | 0 | hayır | 1 | 0 | 0 |
| E | iOS | 31 | 0 | hayır | 6 | 1 | 8 |
| F | Android | 7 | 5 | hayır | 0 | 0 | 0 |
| G | iOS | 14 | 0 | hayır | 12 | 1 | 0 |
| H | Android | 0 | 0 | hayır | 2 | 0 | 25 (basıştan 46 saat sonra) |
| I | iOS | 12 | 0 | hayır | 2 | 0 | 0 |
| J | iOS | 9 | 0 | hayır | 0 | 0 | 0 |
| K | iOS | 15 | 0 | evet | 39 | 0 | 0 |
| L | iOS | 23 | 1 | hayır | 4 | 1 | 18 (basıştan 14 dk önce, aynı gün) |
| M | iOS | 10 | 1 | hayır | 0 | 0 | 0 |
| N | Android | 0 | 0 | hayır | 0 | 0 | 0 |

Satırlar bu rapor için yeniden sıralandı; harfler önceki raporun harfleriyle eşleşmiyor.

Okuma:
- Hiçbiri basmadan önce çeviri sınırına çarpmamıştı. 25'e ulaşan tek kişi (H) bu sınıra basıştan 46 saat sonra ulaştı.
- Defter sınırına çarpan yok: 14 kişinin 13'ü ilk haftasındaydı; 7. günden sonra basan tek kişinin (K) defteri boştu.
- Okuma sınırı canlıda yok.
- Ortak temas kilitli içerik: 4 alıcının 2'si, 10 tamamlamayanın 6'sı basmadan önce kilitli bir metne ya da bölüme dokunmuştu.

Sayılar küçük (4 ve 10); **hipotez.**

## İtirazlar

- **Sınıra çarpma olayı kaydedilmiyor.** Çeviri, defter ve okuma sınırları için ne sunucu ne istemci kayıt bırakıyor. "Çarptı" sayıları dolaylı: dokunuş sayısı, son günün sayacı, defter büyüklüğü. Gerçek çarpma sayısı bilinmiyor.
- **Çeviri sayacı yalnız son günü tutuyor.** Kişinin önceki günlerde 25'e ulaşıp ulaşmadığı görülemez; 25'e ulaşan "tek kişi" bir alt sınırdır.
- **`word_lookup` balonun açılmasıdır, düşen hak değildir.** S2'deki "sınır X olsaydı" tablosu her dokunuşun sayıldığını varsayıyor; bugünkü kural böyle değil.
- **Olay kaydı eksik.** Önceki raporlarda görüldüğü gibi dönenlerin yaklaşık beşte biri olaysız; ilk biten metni olan 98 kişi `reading_completed` olayına dayanıyor.
- **Küçük sayılar.** A2 ilk metin grubu 22 kişi; alıcı ve tamamlamayan grubu 14 kişi.

Öneri yok.
