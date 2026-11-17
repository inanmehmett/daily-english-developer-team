# Satın almalar hangi anda oldu

**Rol:** Nate Gümüş. **Tarih:** 17 Kasım 2026.
**Görev:** `ortak/editor_gorevi_2026-11-17_satin_alma_anlari.md`. Yalnız okuma yapıldı. Bağlantı `default_transaction_read_only = on` ile açıldı ve canlıda hiçbir satır değişmedi.

## En üstte beş satır

1. **Yayından bu yana gerçek satın alma 4 tane, dördü de iOS'ta.** 2'si yıllık plan denemesi, 2'si doğrudan aylık. Android'de gerçek satın alma yok.
2. **Dört satın almanın üçü hesap açıldıktan sonraki ilk 3 dakikada oldu** (35 sn, 1 dk 45 sn, 2 dk 57 sn). Dördüncüsü 2 gün 18 saat sonra.
3. **Dördünde de paywall'dan önceki son 4 dakikada Premium şeridi (`highEngagement`) gösterilmiş.** Paywall'u neyin açtığı kaydedilmiyor: her paywall gösterimi `trigger = manual` olarak yazılıyor. Kod bunu açıklıyor: paywall sayfası tetikleyiciyi rota argümanından okuyor, ama onu açan hiçbir çağrı bu argümanı vermiyor. Yüzey ancak paywall'dan hemen önceki olaydan çıkarılabildi.
4. **Satın almaya basıp tamamlamayan 10 kişi var (7 iOS, 3 Android).** Onuncunun da seçtiği plan yıllık. Bu grup basmadan önce daha çok okumuş: ortanca 1 metin bitirmiş, 11 kelimeye bakmış.
5. **Paywall'un ilk okumadan sonraya ertelenmesi ve V8 için önce/sonra karşılaştırması yapılamaz.** Ertelemenin canlıya çıktığı sürüm (1.0.0+23, 24 Eylül) ilk müşteriden önce; bütün müşteriler ertelenmiş hâli gördü. V8 (`8069597`, 15 Kasım) ise 1.0.4+47'nin kodunda. Hiçbir müşteri bu sürümden olay göndermedi. Müşterilerin en yeni sürümü 1.0.2+45.

## Yöntem

- **Kimler:** `Users.AccountKind = 'customer'`, 261 hesap (168 iOS, 93 Android). Kayıt tarihleri 29 Ekim – 17 Kasım. `IsFreeGrant` olan abonelikler sayılmadı. Test, geliştirici, testçi ve promosyon hesapları da sayılmadı.
- **Kayıt anı:** `UserProfiles.CreatedAt`. Bu an onboarding'in sonunda, hesap açıldığında düşüyor.
- **Satın alma:** `Subscriptions` (Production) ve `SubscriptionHistories` (`TrialStarted`, `Purchased`, `Renewed`, `AutoRenewDisabled`).
- **Satın almaya basma:** `PaywallAnalyticsEvents.purchase_started`.
- **Tamamlanmayan:** `purchase_started` kaydı olan, ama `purchase_completed`, `subscription_completed` ya da `trial_started` kaydı olmayan müşteri. Her kişi için ilk basış sayıldı.
- **Satın almadan önce:**
  - Biten metin: `reading_completed` olayları ve `ReadingProgresses.IsCompleted`; ikisi ayrı verildi.
  - Kelime bakışı: `word_lookup`.
  - Oturum: farklı `SessionId` sayısı.
- **Yüzey:** Paywall gösterimi (`paywall_shown`) tetikleyiciyi taşımıyor. Bu yüzden gösterimden hemen önceki olay yazıldı: kilitli kitap gösterimi, şerit tıklaması, okuma bitişi ve benzeri. Bu bir çıkarımdır.
- Müşteri satırları yerel bir çalışma veritabanına kopyalandı; e-posta, ad ve makbuz verisi alınmadı. Sorgular orada koştu ve kopya iş bitince silindi. Kişiler A–D (alıcı) ve E–N (tamamlamayan) diye anılıyor.

## S1–S5. Gerçek satın almalar

| | A | B | C | D |
|---|---|---|---|---|
| Tarih | 2 Kas | 3 Kas | 7 Kas | 13 Kas |
| Platform | iOS | iOS | iOS | iOS |
| Plan | Yıllık (lansman fiyatı) | Aylık | Yıllık (lansman fiyatı) | Aylık |
| Deneme mi | Deneme | Doğrudan | Deneme | Doğrudan |
| Kayıttan satın almaya | 2 dk 57 sn | 2 gün 18 sa | 35 sn | 1 dk 45 sn |
| Uygulama sürümü | 1.0.1+43 | 1.0.0+37 | olay yok | 1.0.2+45 |
| Paywall'dan hemen önceki olay | ilk metni bitirdi (33 sn önce) | Premium şeridine dokundu | şerit gösterildi (5 sn önce) | kilitli dizi bölümüne dokundu (`locked_series_episode`, 4 sn önce) |
| Son 4 dk'da Premium şeridi gösterildi mi | evet | evet (tıkladı) | evet | evet |
| Paywall'da geçen süre (açılıştan satın almaya) | 37 sn | 40 sn | 26 sn | 1 dk 32 sn |
| Satın almaya kadar biten metin (olay / ilerleme kaydı) | 1 / 1 | 0 / 2 | 0 / 0 | 0 / 0 |
| Satın almaya kadar kelime bakışı | 0 | 30 | 0 | 0 |
| Satın almaya kadar oturum | 1 | 7 | 0 | 1 |
| Sonra: durum | Deneme ücretliye döndü (9 Kas `Renewed`), etkin | Etkin, sonraki dönem 3 Ara | 14 Kas'ta yenilemeyi kapattı, süresi doldu | Etkin, sonraki dönem 13 Ara |
| Sonra: başlattığı / bitirdiği metin | 8 / 5 | 4 / 0 (ilerleme kaydında 2) | 0 / 0 | 3 / 3 |
| Sonra: etkin gün | 5 | 4 | 0 | 3 |
| Son olay | 6 Kas | 14 Kas | hiç olay yok | 17 Kas |

Okuma:
- **A** ilk metni (Why Penguins Can't Fly, 48 saniyelik okuma kaydı) bitirdikten 33 saniye sonra paywall'u görmüş. Bu, ilk okumadan sonra açılan ertelenmiş paywall'un davranışıyla uyumlu; kayıt ise bunu ayırmıyor.
- **B**'nin satın almadan önceki ilk 13,5 saatinde olay kaydı yok; eski sürüm (1.0.0+37) bunları göndermemiş olabilir.
- **C**'nin hiç `UserEvents` kaydı yok. Paywall şerit gösteriminden 5 saniye sonra açılmış. 15 Kasım raporundaki V7 bu kişidir.
- **D** onboarding'i 1 dakika 25 saniyede bitirmiş. Önerilen raftaki ilk diziyi (New in Town) açmış, kilitli bölüme dokunmuş ve aylık planı almış.

**Hipotez:** satın alanların üçü ürünü neredeyse hiç kullanmadan ödeme yaptı.

`SubscriptionHistories`'te aynı saniyede yinelenen `TrialStarted` ve `Purchased` satırları var (B'de 4, D'de 2). Bunlar yenileme değil, aynı satın almanın tekrar kaydı. Gerçek yenileme yalnız A'da (`Renewed`, 9 Kas).

## S6. Satın almaya basıp tamamlamayanlar (10 kişi)

| | Platform | Plan | Kayıttan basışa | Paywall'dan hemen önceki olay | Biten metin (olay / ilerleme) | Kelime bakışı | Oturum | Sürüm |
|---|---|---|---|---|---|---|---|---|
| E | Android | Yıllık | 7 dk | uygulama açılışı (3 sn önce); son 10 dk'da şerit ve kilitli dizi bölümü | 1 / 0 | 0 | 2 | 1.0.2+45 |
| F | Android | Yıllık | 9 dk | metin bitişi (5 sn önce); şerit | 1 / 1 | 0 | 2 | 1.0.2+45 |
| G | Android | Yıllık | 15 dk | şerit gösterimi (aynı saniye) | 1 / 1 | 7 | 2 | 1.0.0+41 |
| H | iOS | Yıllık | 5 sa 25 dk | metin bitişi (18 sn önce); şerit | 2 / 1 | 10 | 4 | 1.0.2+45 |
| I | iOS | Yıllık | 10 sa 57 dk | metin bitişi (4 sn önce); şerit ve kilitli dizi bölümü | 2 / 2 | 12 | 8 | 1.0.2+45 |
| J | iOS | Yıllık | 18 sa 57 dk | kilitli kitap önizlemesi (8 sn önce) | 1 / 0 | 48 | 4 | 1.0.1+43 |
| K | iOS | Yıllık | 19 sa 55 dk | kilitli kitap önizlemesi (4,5 dk önce) | 1 / 1 | 14 | 3 | 1.0.1+43 |
| L | iOS | Yıllık | 2 gün 2 sa | kayıt yok (öncesinde 2 gün olay yok) | 0 / 1 | 9 | 2 | 1.0.2+45 |
| M | iOS | Yıllık | 5 gün 22 sa | metin bitişi (5 dk önce); kilitli kitap | 3 / 3 | 36 | 6 | 1.0.2+45 |
| N | iOS | Yıllık | 9 gün 2 sa | kayıt yok (öncesinde 5 gün olay yok) | 1 / 1 | 28 | 6 | 1.0.1+43 |

| | Satın alan (4) | Basıp tamamlamayan (10) |
|---|---|---|
| Kayıttan ortanca süre | 2 dk 21 sn | 15 sa (aralık 7 dk – 9 gün) |
| Basmadan önce ortanca biten metin (olay) | 0 | 1 |
| Basmadan önce ortanca kelime bakışı | 0 | 11 |
| Seçilen plan | 2 yıllık, 2 aylık | 10 yıllık |
| Platform | 4 iOS | 7 iOS, 3 Android |

Okuma: tamamlamayanların hepsi yıllık planda basmış, satın alanların ikisi aylık almış. Android'de basan 3 kişinin üçü de ilk 15 dakikada basmış. Tamamlamamanın nedeni (iptal, ödeme hatası, mağaza bağlantısı) kayıtlarda yok. `purchase_cancelled` ve `purchase_failed` olayları 15 Kasım'da koda eklendi (`9d169eb`), ama canlıdaki hiçbir müşteri sürümünde değil. Sayılar küçük (4 ve 10); fark **hipotezdir**.

## S7. Paywall ertelemesi ve V8 ne zaman canlıya çıktı

| Değişiklik | Kod | Sürüm | Müşteride |
|---|---|---|---|
| Onboarding sonu paywall'u ilk okuma bitene kadar ertelendi | `2f920a8`, 23 Eyl | 1.0.0+23 (24 Eyl) | İlk müşteri 29 Eki'de geldi; bütün müşteriler ertelenmiş hâli gördü |
| Onboarding son ekranı ilk hikâyeyi açıyor (ertelenmiş paywall'a dokunmuyor) | `b325e20`, 15 Kas | 1.0.4+47 kodunda | Canlıda değil |
| V8: Premium şeridi ilk metin bitene kadar gizli | `8069597`, 15 Kas | 1.0.4+47 kodunda | Canlıda değil |

1.0.4+47 sürüm numarası `967390c` ile 15 Kas 01:44'te verildi; V8 ondan sonra, 15:11'de yazıldı. O saatten önce derlenmiş bir 1.0.4+47 V8'i içermez. Müşterilerden gelen olaylarda görülen en yeni sürüm 1.0.2+45 (iOS ve Android).

Bu yüzden önce/sonra karşılaştırması yapılamıyor. Aşağıdaki tablo, V8 ve yeni son ekran canlıya çıktığında karşılaştırılacak **önceki** durumdur:

| Kayıt haftası | Müşteri | İlk 2 dk'da Premium şeridi gösterilen | Paywall gören | Satın almaya basan | Satın alan |
|---|---|---|---|---|---|
| 26 Eki (29 Eki'den) | 27 | 20 | 10 | 1 | 1 |
| 2 Kas | 99 | 76 | 37 | 8 | 2 |
| 9 Kas | 65 | 47 | 28 | 3 | 1 |
| 16 Kas (2 gün) | 70 | 52 | 18 | 2 | 0 |
| **Toplam** | **261** | **195 (%75)** | **93** | **14** | **4** |

| Platform | Müşteri | Paywall gören | Basan | Satın alan |
|---|---|---|---|---|
| iOS | 168 | 64 | 11 | 4 |
| Android | 93 | 29 | 3 | 0 |

Ek sayılar:
- **Erteleme yürürlükteyken bile paywall ilk okumadan önce açılıyor.** 139 paywall gösteriminin 68'i, o kişi henüz hiç metin bitirmemişken oldu. Ertelenen yalnız onboarding sonundaki otomatik paywall. Kilitli kitap, kilitli bölüm ve şerit paywall'u ilk okumadan önce de açabiliyor.
- **Şerit neredeyse herkese ilk metinden önce gösteriliyor.** 261 müşterinin 251'ine, hiç metin bitirmeden önce en az bir şerit gösterimi düşmüş.

## İtirazlar

- **Dört satın alma ve on yarım kalan deneme hüküm vermek için çok az.** Tablodaki her fark tek kişiyle değişebilir.
- **Yüzey bir çıkarımdır.** Paywall'un hangi düğmeden açıldığı kaydedilmiyor. "Hemen önceki olay" bir şeridin gösterildiğini söyleyebilir, ama kullanıcının ona dokunduğunu söylemez. Şerit tıklaması yalnız B'de kayıtlı.
- **Olay kaydı eksik.** C'nin hiç olayı yok; B'nin ve L–N'nin satın alma öncesindeki saatlerinde de kayıt boşluğu var. "0 metin, 0 bakış" bu kişilerde alt sınırdır.
- **"Yayından bu yana" müşteri etiketinin başladığı tarihtir (29 Eki).** Daha önceki gerçek kullanıcı varsa (ör. mağaza incelemesi dönemi), `AccountKind` onları müşteri saymıyor olabilir; bu kontrol edilmedi.
- **Seçilen plan son basışın planıdır.** Kişi paywall'da planlar arasında gidip gelmiş olabilir; A ve C üç planın hepsine dokunmuş.

Öneri yok.
