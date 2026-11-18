# Sürüm 1 – ilk oturum: uygulama raporu

**Tarih:** 18 Kasım 2026. **Görev:** `ortak/editor_gorevi_2026-11-18_surum1_ilk_oturum.md` (dayanak `ortak/butun_plan.md`). **Plan:** `raporlar/2026-11-17_yolculuk_uygulama_plani.md`.

**Durum:**
- 12 maddenin hepsi kodlandı ve her madde ayrı commit'lendi.
- Akış iPhone SE 3 simülatöründe yerel sunucuyla uçtan uca sürüldü. Sürüşte 6 hata bulundu ve düzeltildi.
- Dallar gönderilmedi, canlı veritabanına yazılmadı. Yayın, birleştirme ve `NextHook` yazımı Mehmet'te.

| Depo | Dal | Taban |
|---|---|---|
| Sunucu | `feat/journey-core` | `feat/free-limits` ← `master` |
| Flutter | `feat/journey-core` | `feat/free-limits` ← `fix/paywall-trigger-attribution` |

## Maddeler

| # | Madde | Durum | Commit | Cihazda |
|---|---|---|---|---|
| 1 | Yolculuk tanımı ve atama | Önceden hazır | sunucu `2947cbf`, `235a739`, `cacd039`, `1df4e31` | Atama görüldü (A2 → `starter-a2`) |
| 2 | Onboarding sonu: "{ad}, yolculuğun hazır" + 4 durak; teklif (`onboarding`) + kaydırmadan görünen "Ücretsiz başla: günde bir durak"; kapanınca durak 1 | Bitti | sunucu `bbf6ca5`; Flutter `3bba9b2d` | Görüldü |
| 3 | Ana sayfa kartı: "Senin yolculuğun · 1/4 · Sıradaki: {ad}", tek düğme | Önceden hazır | Flutter `c1d35796` | Görüldü |
| 4 | Bitiş ekranı: n/4, sıradaki ad + `NextHook` (boşsa açıklama); açıksa "Sıradaki durak"; kapalıysa "Sıradaki durak yarın açılır" + "Yarın hatırlat" + "Premium'la şimdi oku" | Önceden hazır | sunucu `df73f77`; Flutter `42fc9b26` | Görüldü |
| 5 | Deneme/Premium başlayınca "Premium açıldı: yolculuğun bekliyor" → sıradaki durak | Bitti | Flutter `901bb5be` | Satın alma sürülemedi; widget testi var |
| 6 | Paywall: "7 gün ücretsiz dene"; "7 gün ücretsiz, sonra {fiyat}/{dönem}; istediğin an iptal" | Bitti | Flutter `30946f2d` | Görüldü (mağaza planlarıyla) |
| 7 | Vazgeçince paywall açık kalır; yıllık seçiliyse "Yıllık fazla mı geldi? Aylık planla başla"; indirim yok | Bitti | Flutter `cf9aa592` | Mağaza iptali sürülemedi |
| 8 | Başlangıç duraklarında dokunuş haktan düşmez; sınır ekranı tetikleyicisi `limitReached` | Bitti | sunucu `bd743be`; Flutter `d3172932` | Sınır sayfası görüldü |
| 9 | Kilitli içerik: metnin adı, "Premium'la şimdi oku", hak varsa "Bugünkü ücretsiz hakkımla aç" | Bitti | Flutter `416b726c` | Görüldü |
| 10 | Ekranı kesen teklif: ilk oturumda 2 (onboarding sonu, durak 2 bitişi), sonra günde 1 | Bitti | Flutter `2322c5fb` | İlk oturumda başka teklif çıkmadı |
| 11 | Olaylar + cihazda kayıtla doğrulama | Bitti | Flutter `5726a49f` (+ önceki `19909e5d`) | Kayıt aşağıda |
| 12 | 12 başlangıç durağı için `NextHook` taslağı | Bitti | ekip `b5ed085` | — |

## Madde notları

**2. Onboarding sonu.**
- Plan ekranının başlığı "{ad}, yolculuğun hazır". Altında yolculuğun dört durağı adlarıyla sıralanıyor; ilkinde "Bugün" yazıyor.
- Duraklar, hesap açılmadan önce `GET /api/Journey/starter?level=&interests=` ucundan geliyor. Uç, atamayla aynı kuralı kullanıyor; kullanıcıya sonra atanan yolculuk ekranda gördüğüyle aynı.
- Uç cevap vermezse eski plan ekranı (hafta hedefi ve yol haritası) gösteriliyor.
- "Bu planla devam et" sırasıyla şunları yapıyor: hesabı açıyor, ana sayfaya geçiyor ve `onboarding` tetikleyicisiyle paywall'ı açıyor.
- Paywall'da satın alma düğmesinin hemen altında "Ücretsiz başla: günde bir durak" duruyor. Bu satır sabit alt çubukta olduğu için kaydırmadan görünüyor.
- Paywall ister bu satırla ister çarpıyla kapansın, 1. durak doğrudan açılıyor.
- Satın alma olursa başarı ekranı kullanıcıyı sıradaki durağa götürüyor (madde 5).
- "Deneme rehberi" ekranı kaldırıldı; onboarding'e yeni ekran eklenmedi.
- Paywall'ı ilk okumaya erteleyen işaret artık konmuyor.

**5. Premium açıldı.**
- Satın almadan sonra yolculuk sunucudan yeniden yükleniyor.
- Okunabilir bir sıradaki durak varsa başarı ekranı "Premium açıldı: yolculuğun bekliyor" diyor. Tek düğme o durağı açıyor.
- Yolculuk yoksa eski ekran ("Premium'a hoş geldin") gösteriliyor.
- Onboarding teklifinden satın alındığında 1. durak ikinci kez açılmıyor.

**6. Paywall.**
- Seçili planın kendi deneme günü ve mağaza fiyatı kullanılıyor: düğmede "7 gün ücretsiz dene", altında "7 gün ücretsiz, sonra $19,99/yıl; istediğin an iptal".
- Yıllık kartta aylık karşılık zaten vardı ("$1,67/ay").

**7. İkinci yol.**
- Mağaza sayfası iptal edilirse ya da ödeme düşerse paywall açık kalıyor.
- Seçili plan yıllıksa düğmenin üstünde "Yıllık fazla mı geldi? Aylık planla başla" çıkıyor. Dokunmak aylık planı seçip satın almayı başlatıyor.
- İndirim yok.
- Olaylar: `purchase_downsell_shown`, `purchase_downsell_accepted`.

**8. Başlangıç istisnası.**
- Kelime ve cümle çevirisi istekleri artık okunan metnin kimliğini (`readingTextId`) taşıyor.
- Metin, kullanıcıya atanmış bir başlangıç yolculuğunun durağıysa sunucu günlük hakkı düşmüyor.
- Okuyucu da bu duraklarda kendi yerel hak kontrolünü atlıyor.
- Çeviri ve defter sınır sayfaları paywall'ı tek tetikleyiciyle (`limitReached`) açıyor. Hangi sınır olduğu `limit_reached` olayının `type` alanında.

**9. Kilitli içerik.**
- Genel uyarı yerine alttan bir sayfa açılıyor: metnin adı, "Premium'la şimdi oku" ve ikinci düğme.
- İkinci düğme "Bugünkü ücretsiz hakkımla aç" oluyor, yalnız metin ücretsiz havuzdaysa ve bugünün hakkı varsa. O zaman metni açıp okuyucuya götürüyor.
- Bu koşul yoksa ikinci düğme "Şimdi değil" diyor.
- Dizi bölümleri ve kilitli bölümler de aynı sayfayı kullanıyor.

**10. Teklif sayısı.**
- İlk oturumda ekranı kesen iki an var:
  - onboarding sonu teklifi: tavana yazılıyor;
  - durak 2 bitişindeki iki kapı: bitiş ekranının parçası, tavana yazılmıyor.
- Oturum bayrağı ilk oturumda başka bir teklifin araya girmesini engelliyor.
- Eski 24 saatlik bekleme kaldırıldı; artık yerel takvim gününde 1 teklif. Bekleme yüzünden, akşam onboarding'i biten kullanıcı ertesi gün başlangıcı bitirdiğinde ana teklifi göremiyordu.

## Cihazda doğrulama

**Nasıl yapıldı:**
- Sunucu yerelde çalıştırıldı ve `de_surum1` veritabanına bağlandı. Bu veritabanı, yalnız içerik taşıyan yerel kopyadan türetildi; içinde kullanıcı yok, FCM anahtarı yok.
- Sunucu ayrı bir dizinden, yalnız yerel bağlantı dizesiyle başlatıldı. Böylece projedeki `.env` (canlı veritabanı) yüklenmedi.
- Paywall fiyatları için canlıdaki `SubscriptionPlanPrices` tablosunun 3 satırı salt okunur bağlantıyla okundu ve yerel kopyaya yazıldı. Kişisel veri yok.
- **Canlıya hiçbir şey yazılmadı.**
- Akış `integration_test/critique_shots_test.dart` dosyasının `SURUM1` kipiyle sürüldü. Sırası:
  1. onboarding;
  2. teklif → "Ücretsiz başla";
  3. durak 1 → bitiş → "Sıradaki durak";
  4. durak 2 → bitiş (yarın açılır, iki kapı);
  5. ana sayfa, kilitli sayfa, sınır sayfası, paywall;
  6. "Yarın hatırlat".

### Sürüşte bulunan ve düzeltilen hatalar

1. **Yanlış yolculuk atanıyordu** (`0a910c88`).
   - Belirti: plan ekranı A2 duraklarını gösterirken ana sayfa A1 yolculuğunu açtı.
   - Sebep: yolculuk, onboarding cevapları (seviye dahil) sunucuya yazılmadan yükleniyordu; sunucu da varsayılan seviyeyle atadı.
   - Düzeltme: yükleme artık kayıttan sonra. Doğrulama: A2 → `starter-a2`.
2. **Durak 1 kilitli açıldı** (`0a910c88`).
   - Belirti: durak açıldıktan sonra uygulama metni kilitli sandı.
   - Sebep: ortak hak düştükten sonraki `/api/FreeUnlocks` okuması önbellekten döndü.
   - Düzeltme: `/api/Journey`'ye yazmak artık bu okumayı ve okuma ilgili okumaları önbellekten düşürüyor.
3. **Durak 1 bitişini seri hatırlatma sayfası kesiyordu** (`57809ad6`).
   - Belirti: "Yarın da hatırlatalım mı?" sayfası "Sıradaki durak"ın üstüne açılıyordu.
   - Planda durak 1 bitişinde kesme yok. Yolculukta hatırlatma, durak 2'deki "Yarın hatırlat" kapısının işi.
   - Düzeltme: sayfa yolculuk dışı metinlerde kalıyor.
4. **Paywall, planlar yüklenmeden bir plan satıyordu** (`ed76ade2`).
   - Belirti: onboarding teklifi açıldığında liste yükleniyordu, ama alt çubuk "Premium'a Geç · ₺79,99/hafta" diyordu. Dokunuş ise aylık yedek planı satın alacaktı.
   - Bu hata yolculuktan önce de vardı.
   - Düzeltme: yükleme bitene kadar çubuk plan ve fiyat göstermiyor, düğme bekliyor.
5. **Ana sayfa eski ilerlemeyi gösteriyordu** (`028e9e34`).
   - Belirti: iki durak okununca kart hâlâ 1/4 dedi.
   - Sebep (ağ katmanı): önbellek isabeti isteği `resolve` ile kapatıyor. Önünde duran tekrar önleyicinin (dedup) uçuş kaydı bu yüzden hiç kapanmıyordu. Aynı GET 45 sn bu kayda bağlanıp iptal ediliyordu; sürüşte `/api/Journey` 182 kez böyle düştü.
   - Düzeltme: dedup önbelleğin arkasına alındı. Test eski sırada takılıyor, yeni sırada geçiyor.
   - Bu hata yalnız yolculuğu değil, kısa aralıkla tekrarlanan bütün GET isteklerini etkiliyordu. Çökme panelindeki "Deduplication safety cleanup" kayıtları büyük ihtimalle bu.
6. **En büyük yazıda seçili plan yine düğmenin altında kalıyordu** (`f8ebcf8d`, `be2f9372`).
   - Belirti: SE 3'te paywall açılınca yalnız haftalık kart görünüyordu. Seçili olan yıllık kart düğmenin altındaydı (Dieter'in engelleyici bulgusu).
   - Sebep: seçili kart bir kez görünür yapılıyordu. Sonra üstteki satırlar (deneme süresi, "şimdi N hikâye açık") geç gelip içeriği uzatıyor ve kartı yeniden aşağı itiyordu.
   - Düzeltme: kullanıcı kendisi kaydırana kadar, içerik her uzadığında kart yeniden gösteriliyor.
   - İkinci sebep: bitiş ekranından açılan paywall'da planlar önbellekten sayfadan önce hazır oluyor ve kaydırma hiç tetiklenmiyordu. Kontrol artık ilk çizimde de yapılıyor.

### Cihazdan düşen olaylar (yerel `UserEvents`, son temiz sürüş)

| Saat | Olay | Alanlar |
|---|---|---|
| 02:00:42 | `journey_assigned` | `starter-a2`, A2, `initial` |
| 02:00:43 | `offer_shown` | `moment=onboarding_end` |
| 02:00:50 | `offer_dismissed` | `moment=onboarding_end`, `via=free_path` |
| 02:00:50 | `journey_stop_unlocked` | durak 1 |
| 02:00:50 | `journey_stop_started` | durak 1, `source=onboarding` |
| 02:01:21 | `journey_stop_completed` | durak 1 |
| 02:01:31 | `journey_stop_unlocked`, `journey_stop_started` | durak 2, `source=finish` |
| 02:02:05 | `journey_stop_completed` | durak 2 |
| 02:02:05 | `offer_shown`, `journey_wait_shown` | `moment=journey_next` |
| 02:02:20 | `remind_tomorrow_tapped` | durak 3 |
| 02:02:27 | `offer_dismissed` | `moment=journey_next` |
| 02:02:35 | `remind_tomorrow_result` | `granted=false` (simülatörde sistem penceresi cevaplanmadı) |
| 02:02:46 | `limit_reached` | `type=translation` |

- Bitiş ekranındaki "Sıradaki durak" dokunuşu bu sürüşte yalnız `finish_cta_tapped` olarak yazıldı. Artık `journey_next_tapped` (`source=finish`) da yazılıyor (`5726a49f`).
- Ana sayfa ve satın alma sonrası kaynaklar önceden vardı.
- `purchase_downsell_shown/accepted` ve `offer_accepted` cihazda görülmedi, çünkü mağaza sayfası testle sürülemiyor.

### Ekran görüntüleri

Görüntüler `raporlar/ekran_2026-11-18/` klasöründe; "normal" ve "büyük yazı" (iOS en büyük erişilebilirlik boyutu, uygulamada 1,3 tavan) olarak ayrı.

| Ekran | Madde | Normal | Büyük yazı |
|---|---|---|---|
| Plan: "{ad}, yolculuğun hazır" + 4 durak | 2 | [görüntü](ekran_2026-11-18/normal/116_plan_yolculuk.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/116_plan_yolculuk.png) (liste kayıyor, düğme sabit) |
| Onboarding sonu teklifi: seçili yıllık + "7 gün ücretsiz dene" + "Ücretsiz başla: günde bir durak" | 2, 6 | [görüntü](ekran_2026-11-18/normal/116b_onboarding_teklif.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/116b_onboarding_teklif.png) |
| Durak 1 bitişi: 2/4, sıradaki durak, açıklama, "Sıradaki durak" | 4 | [görüntü](ekran_2026-11-18/normal/31_durak1_bitis.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/31_durak1_bitis.png) |
| Durak 2 bitişi: "Sıradaki durak yarın açılır" + iki kapı | 4, 10 | [görüntü](ekran_2026-11-18/normal/33b_durak2_bitis_kapilar.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/33b_durak2_bitis_kapilar.png) |
| "Yarın hatırlat" → sistem izni | 4 | [görüntü](ekran_2026-11-18/normal/39_yarin_hatirlat.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/39_yarin_hatirlat.png) |
| Ana sayfa kartı: 2/4, "Sıradaki: Baba Yaga", yarın açılır, tek düğme | 3 | [görüntü](ekran_2026-11-18/normal/35_ana_sayfa_kart.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/35_ana_sayfa_kart.png) (bu sürüşte simülatör "çevrimdışı" dedi, kart eski veriyle 1/4; bkz. açık nokta 10) |
| Kilitli içerik sayfası | 9 | [görüntü](ekran_2026-11-18/normal/36_kilitli_icerik.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/36_kilitli_icerik.png) |
| Çeviri sınırı sayfası | 8 | [görüntü](ekran_2026-11-18/normal/37_ceviri_siniri.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/37_ceviri_siniri.png) |
| Bitiş ekranından açılan paywall (`journeyNext`) | 6 | [görüntü](ekran_2026-11-18/normal/38_paywall.png) | [görüntü](ekran_2026-11-18/buyuk_yazi/38_paywall.png) (planlar yüklenirken çekildi: düğme bekliyor, fiyat yok) |

Notlar:
- Fiyatlar simülatörün StoreKit dosyasından geliyor (dolar). Türkiye fiyatı ve deneme süresi gerçek cihazda, TestFlight'ta bir kez görülmeli.
- Kilitli içerik ve sınır sayfaları sürüşte doğrudan açıldı. Kilitli sayfa, "Bugünkü ücretsiz hakkımla aç" görünür hâliyle çekildi.

## Açık noktalar ve kararlar (Mehmet ve ekip)

1. **Yayın sırası:**
   1. Sunucu dalları `master`'a birleşir. Yolculuk tabloları migration ile gelir.
   2. `NextHook` betikleri onayla çalışır: seviye yolculuklarının 32 cümlesi hazır; 12 başlangıç cümlesi taslak (`raporlar/2026-11-18_baslangic_duraklari_nexthook_taslak.md`).
   3. Flutter dalları birleşir, sonra 1.0.4 derlenir.
2. **Durak 2 bitişinde ana düğme "Quiz'e Başla".** İki kapının altında büyük turuncu bir quiz düğmesi duruyor. "Bir ekranda tek ana eylem" kuralıyla çakışıyor. Quiz düğmesinin bu ekranda ikincil olup olmayacağı karar.
3. **Onboarding teklifinin başlığı** "Sınırsız oku, daha hızlı öğren". Plan, teklifin yolculuğu satmasını istiyor ("7 gün ücretsiz: bütün yolculuk bekleme olmadan"). Bu turda yalnız düğme ve fiyat satırı değişti; başlık metni ayrı karar.
4. **Simülatörde deneme süresi.** Mağaza planları yüklenince düğme "7 gün ücretsiz dene" diyor. Yüklenene kadar artık bekliyor. Gerçek cihazda Türkiye fiyatı ve deneme bir kez TestFlight'ta görülmeli; simülatör StoreKit dosyasının dolar fiyatlarını gösteriyor.
5. **24 saatlik bekleme kalktı** (madde 10). Ekranı kesen teklif artık takvim gününde bir. Eski kural ("Map §3") bilinçli bir karardı; değişiklik bu görevin "sonra günde bir" kuralına dayanıyor.
6. **Ağ katmanı düzeltmesi** (`028e9e34`) bütün istekleri etkiliyor. Yayından sonra çökme panelinde "Deduplication safety cleanup" kayıtlarının düşmesi beklenir; bakılmalı.
7. **4. durağın `NextHook` cümlesini** yalnız Premium kullanıcı görür. Ücretsiz kullanıcı başlangıcı bitirince ilerleme kartı ve teklif görüyor.
8. **Sürüm 2–3 işleri dalda duruyor:** başlangıç bitince ilerleme kartı, 3. durak kilidi, harita, bildirim düzeni. Sürüm 1 ile çıkıp çıkmayacakları Mehmet'in kararı.
9. **Testler:**
   - Sunucu: 1553 test geçti.
   - Flutter: `flutter analyze` temiz, tam takım geçti (sürüşle aynı anda çalışınca 8 dosya derleme zaman aşımına düştü; tek başına çalıştırınca geçtiler).
   - Satın alma, mağaza iptali ve aylığa geçiş cihazda sürülemedi; widget ve birim testleriyle korunuyor.
10. **Büyük yazı sürüşünde simülatör "çevrimdışı" oldu.**
    - Yerel sunucu bu sırada cevap veriyordu; uygulamanın bağlantı denetimi simülatörde birkaç kez "offline" dedi.
    - Sonuç: ana sayfa kartı eski veriyle 1/4 gösterdi. Normal yazı sürüşünde aynı kart doğru (2/4).
    - Aynı karede, çevrimdışı şeridi en büyük yazıda taşıyor (sarı-siyah taşma çizgisi). Bu sorun Sürüm 1'den önce de vardı, bu turda dokunulmadı.
