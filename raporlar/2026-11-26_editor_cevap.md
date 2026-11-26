# Editör cevabı: 25 Kasım görevi ve kuyruk (26 Kasım 2026)

**Kimden:** editör · **Mehmet (26 Kas):** "Yayına gönderdim. Editördeyiz zaten. Hepsi onaylı, yap; tüm yetkiler sende."
**Kapsam:** `ortak/editor_gorevi_2026-11-25.md` (A1–A11, B1–B4) ve `ortak/editor_kuyrugu.md` (1–4).

## Özet
- **Üç sunucu PR'ı (#21, #22, #23) ve bir uygulama PR'ı (#5) açık; hiçbiri birleştirilmedi.** Birleştirme isteği bu oturumun izin katmanında reddedildi; birleştirmeyi Mehmet yapar.
- **Canlı veritabanına bağlanılamadı** (aynı izin katmanı). Canlı sayım isteyen bütün maddeler bu yüzden yapılmadı; aşağıda tek tek işaretli.
- Koddan cevaplanabilen her soru cevaplandı.

| PR | İçerik | Test | Birleşince |
|---|---|---|---|
| Sunucu [#21](https://github.com/inanmehmett/DailyEnglish/pull/21) | Şıkların karıştırılması (belge testi ve "Seviyeni yeniden ölç"); dört yeni B2 sorusu, iki şık düzeltmesi | 1841 geçti, 0 kaldı | Yayına girer; betik gerekmez |
| Sunucu [#22](https://github.com/inanmehmett/DailyEnglish/pull/22) | 15 ad değişikliği betiği, geri alma betiği, web ana sayfasındaki ad | Yerelde uygulandı ve geri alındı | Betik canlıda ayrıca çalıştırılmalı |
| Sunucu [#23](https://github.com/inanmehmett/DailyEnglish/pull/23) | Bildirim metinleri (taslak 3), Türkçe ad, dokununca hikâyenin kapağı | 1831 geçti, 0 kaldı | Yayına girer; betik gerekmez |
| Uygulama [#5](https://github.com/inanmehmett/Flutter/pull/5) | Mağazadaki 1.0.4 (50) ve bekleyen iki okuyucu düzeltmesi `main`'e | Kod değişikliği yok | Yayın etkisi yok |

## A. Bilgi istekleri
| # | Durum | Cevap |
|---|---|---|
| A1 Sürüm dağılımı | **Yapılmadı** (canlı veri) | – |
| A2 Geri bildirimler | **Yapılmadı** (canlı veri) | – |
| A3 Tutunma, 29 Kasım sayımı | **Yapılmadı** (canlı veri) | 29 Kasım sınavı bu sayıya bağlı |
| A4 Çekirdek grup | **Yapılmadı** (canlı veri) | – |
| A5 Satın alanlar | **Yapılmadı** (canlı veri) | – |
| A6 Yorum isteme | Koddan | Uygulama içi değerlendirme penceresi **2 Ekim'den beri var** (`lib/core/services/store_review_service.dart`). Hikâye bitişinde ve geçilen quizde (en az %80) denenir. Koşullar: kurulumdan en az 3 gün, 3 etkin gün, 3 bitmiş okuma; iki istek arası 120 gün; yılda en çok 3; aynı sürümde bir kez. Profildeki "değerlendir" mağaza sayfasını açar |
| A7 Haftalık tablo | **Yapılmadı** (canlı veri) | – |
| A8 Belge testi | Koddan | Şıklar **karıştırılmıyordu** (sunucu kayıttaki sırayla yolluyor, uygulama geleni gösteriyor). Soru bazında cevap kaydı **var** (`AssessmentResponses`: soru, seçilen şık, doğru mu, süre). Düzeltme PR #21'de. Eşikler ve mağaza/site iddiaları bu turda dökülmedi |
| A9 Derleme 50 görüntü soruları | Koddan | Kariyer alt şeridi gün tahminini yalnız sunucu bir tahmin verebildiğinde yazar (okurun son günlerdeki okuma hızı gerekir); yoksa "…'ya doğru ilerliyorsun"a düşer. Görüntüdeki hesapta hız verisi yoktu; hata değil. Belge testinde altta kalan şıklar için **kaydırma ipucu yok** (düz liste; çubuk ya da solma yok) |
| A10 Yorum isteme altyapısı | Kısmen | Bildirim mağaza sayfasını açabiliyor (yönetim panelindeki "yeni sürüm hazır" bildirimi). Sunucudan açılıp kapanan genel bir duyuru kartı dar bir aramayla bulunamadı; kesin cevap için ana sayfa kartları ayrıca taranmalı. Mağaza yorumlarının dökümü yapılmadı (konsol gerekir) |
| A11 Bildirim sayıları | **Yapılmadı** (canlı veri) | Kelime tekrarındaki 3 gün arası PR #15 ile düzeldi: ara artık gönderim kaydından okunuyor (`SentSinceAsync`) |

## B. Düzeltmeler
**B1 Şıkların karıştırılması: PR #21.** Sunucuda yapıldı; uygulama derlemesi gerekmiyor. Her denemenin bir tohumu var; şık sırası tohumdan ve soru kimliğinden türetiliyor. Uygulama gördüğü konumu yolluyor, sunucu kayıttaki sıraya çevirip puanlıyor ve öyle kaydediyor. 1.0.2, 1.0.4 (47) ve 1.0.4 (50) etkilenmiyor. Yayından önce başlamış yarım denemeler eski sırayla sürer. "Seviyeni yeniden ölç" parçaları da aynı şekilde.

**B2 Sorular: PR #21.** Havuz açılışta tohum dosyalarından yazıldığı için canlıya ayrıca betik gerekmiyor; eski dört soru silinmez, kapatılır.
| Değişiklik | Not |
|---|---|
| 130, 146, 136, 144 yerine dört yeni B2 sorusu | Yeni anahtarlar `rv1-b2-t03-q5`, `-t07-q5`, `-t04-q5`, `-t06-q5` |
| 133: "cheap" → "simple" | Uygulandı |
| 161: doğru şık "believed it would be" | Uygulandı |
| 39: "it costs no money" | Zaten yapılmıştı |
| 56: tür etiketi çıkarım olsun | **Uygulanmadı.** Havuzun mekanik denetimi A1'de çıkarım sorusunu reddediyor; etiket "metin bağı" kaldı. Karar Charles'ta |
| "Türü boş" beş soru | Veri sorunu değil: türler kayıtta dolu (ana fikir, amaç); 21 Kasım dökümü bu iki türü "-" yazmış |

Paul'un metninden sapmalar (mekanik denetim "doğru şık tek başına en uzun olamaz" dediği için): 130'un yerine gelen soruda bir çeldiriciye "that" eklendi; 146'nınkinde "By charging for concerts" → "By charging visitors for concerts"; 144'ünkinde doğru şık "There is too little time to follow one animal", çeldiriciler buna göre uzatıldı. 136 ve 144'ün yerine gelen sorular "metin bağı" etiketli (bir metinde aynı türden iki soru olamıyor). **Charles ve Paul bakmalı.**

**B3 Canlıda doğrulama:** yapılmadı (PR birleşmedi, canlı veri erişimi yok).

**B4 Bildirim:** 3 gün arası zaten düzelmiş (A11). "İlk okumaya çağrı başlığı hikâye adıyla gitsin" maddesi Mehmet'in 26 Kasım yönüyle ("kitap adı başlık olmaz") geçersiz kaldı; tersine, başlıktaki hikâye adı kaldırıldı.

## Kuyruk
**1. Ad değişiklikleri:** ayrıntı `raporlar/2026-11-26_editor_ad_degisiklikleri.md`. Betik hazır (PR #22), canlıda çalıştırılmadı.

**2. Denemede yenilemeyi kapatanlar:** a, b, d **yapılmadı** (canlı veri). c, koddan:
- Deneme bitiş bildirimi bitişten **2 gün önce**, yalnız **yenilemesi açık** olana gider. Yenilemeyi kapatana gitmez (gövde "plan olarak devam eder" dediği için bilerek).
- Yenilemeyi kapatan deneme kullanıcısına özel bir bildirim ya da teklif yok.
- Uygulamada kalan deneme günü yalnız **profil sayfasında** yazıyor ("{n} gün deneme kaldı"); abonelik yönetimi kartında durum "Deneme". Ana sayfada denemeyle ilgili bir satır yok. Deneme yenilenmeden bitince görülen ekran ve "Aylık planla başla" teklifinin bu durumda çıkıp çıkmadığı taranmadı (kuyrukta).

**3. Abonelikler sayfası:** c, d, e **yapılmadı** (canlı veri). a ve b, koddan:
- a) "Platform" hücresindeki ikinci, etiketsiz rozet **ödeme türü** (Ücretli, Deneme, Promosyon, İade edildi, Test, Elle). Açıklaması yalnız fareyle üstüne gelince çıkıyor; telefonda görünmüyor. Öneri: ödeme türü kendi sütununa ("Ödeme") alınsın. Uygulanmadı; panel görünümü taslak onayıyla değişir.
- b) Üç alan aynı iki kayıttan (durum, yenileme) türetiliyor. Çelişkili görünebilecek iki durum: durumu hâlâ "Deneme" olup bitiş tarihi geçmiş kayıt ("Deneme" + "Deneme ödemeye dönmeden bitti" + erişim yok), ve geçmişinde ödeme izi olup durumu "Deneme" olan kayıt (yeniden abone olan).
- Sayaçlar abonelik **kaydını** sayar; yalnız "Premium kullanıcı" kişi sayar.

**4. Bildirimler:** d ve e'nin kod kısmı ile üç soru:
- **e)** Mehmet'e gelen "seri başlat" bildirimi dokununca **ana sayfayı** açıyordu, metni değil (hikâye kimliğini yalnız "geri dön" taşıyordu). PR #23 ile yarım hikâyesi olan okurda seri, günlük hatırlatma ve ilk okuma bildirimleri de kimliği taşıyor; 1.0.4 dokununca o hikâyenin kapak sayfasını açar. Mehmet'in hesabında metnin gerçekten yarım olup olmadığına bakılamadı (canlı veri).
- **Soru 1:** bir tür için birden çok şablon tutulup sırayla seçilmiyor; her türün tek metni var. Gönderim kaydına metin sürümü yazılıyor (bu PR'dan sonra `copy_v3`), şablon kimliği yazılmıyor.
- **Soru 2:** gönderim işi saatte bir çalışıyor (her saat :05). Saat sırası: seçilen saat, yoksa son 14 günün en yoğun etkinlik saati, yoksa 20:00. "Dün okuduğu saatin yarım saat öncesi" için etkinlik zamanları kayıtta var; yarım saatlik hassasiyet işin yarım saatte bir çalışmasını gerektirir.
- **Soru 3:** kişi başına günde 1 bildirim.

### Bildirim dökümü (d): bugün gidenler ve PR #23 sonrası
| Tür | Bugün (başlık / gövde) | PR'dan sonra | Kaynak |
|---|---|---|---|
| Seri başlat (1–2 gün) | "{ad}, dün okudun, bugün de olsun mu?" (36+ karakter, kesiliyor) / "{İngilizce ad} bıraktığın yerde duruyor." | "İyi akşamlar, {ad}" / "Bugünkü hikâyen hazır. 3 dakika yeter." | Taslak 3 |
| Seri (3+ gün) | "{ad}, 5 gündür her gün okuyorsun" / "Bu akşam bir bölüm daha okursan 6. gün olur." | "5 gün oldu" / "Harika gidiyorsun. Bugün de okursan 6 olacak." | Taslak 3 |
| Günün quizi | "Dünkü kelimeler yerine oturdu mu?" / "Bugün 10 yeni kelime, iki dakika. Herkesle aynı sorular." | "Günün quizi hazır" / "10 soru, 2 dakika." (5 soruya kadar "1 dakika") | Taslak 3 |
| Kelime tekrarı | "ready ne demekti?" / "Bugün 7 kelimenin tekrar günü. …" | "Küçük bir tekrar" / "Defterindeki kelimelere birlikte bakalım mı?" | Taslak 3 |
| Geri dön, 3. gün | "{İngilizce ad} seni bekliyor" / "Kaldığın yerden, 4 dakikalık bir hikâye." | "Seni özledik" / "Yeni hikâyen hazır. Kısa bir tanesiyle başlayalım mı?" | Taslak 3 |
| Deneme bitiyor | "Ücretsiz denemen cuma günü bitiyor" / "Sonrasında yıllık plan olarak devam eder. İstemezsen iptal edebilirsin; sürpriz yok." | "Küçük bir hatırlatma" / "Denemen cuma günü bitiyor. Sonrasında yıllık plan olarak devam eder; istemezsen iptal edebilirsin." | Taslak 3, **sapmayla** |
| Yeni hikâye | "Yeni hikâye: {İngilizce ad}" / "B1 seviyesinde, yeni eklendi. İlgi alanına göre seçtik." | "Yeni hikâye" / "Rafına yeni bir hikâye eklendi. Göz at." | Taslak 3 |
| İlk okuma, 1. gün | "İlk hikâyen: {İngilizce ad}" / "Senin seviyende bir hikâye. Takıldığın kelimeye dokunman yeter." | "İlk hikâyen hazır" (adlıysa "{ad}, ilk hikâyen hazır") / aynı gövde | Kural 2 |
| İlk okuma, 1. gün, yarım hikâye | "Hikâyen yarım kaldı" / "{İngilizce ad} bıraktığın yerde duruyor." | aynı başlık / "{Türkçe ad} yarım kaldı. Kaldığın yerden devam et." | Kural 4 |
| İlk okuma, 3. gün | "Beş dakikan var mı?" / "Seviyene göre kısa hikâyeler var. Bilmediğin kelimeye dokun, sözlüğe gerek yok." | **değişmedi** | Paul'e |
| İlk okuma, 7. gün | "Hangi hikâyeyle başlasak?" / "Seviyene göre hikâyeler var. Birini seç, ilk bölümü oku." | **değişmedi** | Paul'e |
| Günlük hatırlatma | "{ad}, okuma vakti" / "Bugünkü hedefin 10 dakika; bir bölüm yeter." ya da yarım hikâye satırı | başlık aynı; yarım hikâye satırı Türkçe adla | Paul'e |
| Seri telafisi | "{ad}, dün ara verdin, sorun yok" / "5 günlük serin duruyor. Bugün bir hikâye ya da bölüm bitirirsen geri gelir." | **değişmedi** | Paul'e |
| Geri dön, 7. gün | "{ad}, bir haftadır görüşmedik" / "Sıradaki hikâyen hazır: {ad}. Defterindeki kelimeler de yerinde." | başlık aynı; hikâye Türkçe adla | Paul'e |
| Geri dön, 14. gün | "Yolculuğun yerinde duruyor" / "{ad}, 4 dakika. Ne zaman istersen oradan devam." | hikâye Türkçe adla | Paul'e |
| Geri dön, 30. gün | "Kapı hep açık" / "Kaldığın yerdeyiz. {ad} seni bekliyor." | hikâye Türkçe adla | Paul'e |
| Günün ücretsiz metni | 12 Kasım'dan beri **gönderilmiyor** | **gönderilmiyor** | Karar ekipte |
| Yeni rütbe | 12 Kasım'dan beri **gönderilmiyor** | **gönderilmiyor** | Karar ekipte |

**Taslaktan sapma (deneme bitiyor):** taslağın gövdesi "O güne kadar bütün hikâyeler açık" diyordu ve ücretlendirmeyi söylemiyordu. Bu bildirim yalnız yenilemesi açık olana gidiyor; ücretin alınacağını söylemeyen metin ücreti sürpriz yapar. Başlık taslaktan alındı, gövdede "sonrasında … olarak devam eder; istemezsen iptal edebilirsin" kaldı. Ekip taslaktaki cümleyi isterse tek satır.

**Uygulanmayan taslak satırları:** "Az kaldı / Hikâyenin bitmesine 2 dakika var" (kalan süre hesaplanamıyor; yanlış sayı söylenmesin diye yazılmadı) · "Günün ücretsiz metni açıldı" ve "Yeni rütbe" (bu iki tür 12 Kasım'dan beri kapalı; açmak gönderim düzenini değiştirir, ayrı karar).

**Uygulama dili İngilizce olan okur:** ayrım yapılmadı; hepsine Türkçe ad gider (Türkçe adı olmayan metinde İngilizce ad).

## Ek bulgular
- **Room 214, 7. bölüm ("Kayıkhanedeki Kardeş"):** "boathouse" sözü ilk beş bölümde hiç geçmiyor; ilk kez 6. bölümde geçiyor. Katalogda 7. bölümün Türkçe adını gören okur, kardeşin yerini 6. bölüme gelmeden öğrenir. (Yerel veritabanındaki metinlerden; bölümler baştan sona okunmadı.)
- Uygulama deposunda mağazadaki sürüm `feat/journey-core` dalındaydı, `main` 16 Kasım'da kalmıştı: PR #5.
- Sunucu PR #17 (seviye etiketi betiğinin canlıda çalışan hâli) 21 Kasım'dan beri açık.

## Mehmet'ten beklenen
1. **PR'ları birleştirmek:** sunucu #21 ve #23 (birleşince yayına girer), uygulama #5 (yayın etkisi yok).
2. **Canlı veri erişimi:** bu oturumda veritabanı bağlantısı izin katmanında reddedildi. Erişim açılırsa A1–A5, A7, A11 ve kuyruk 2–3'ün sayımları tek turda çekilir.
3. **Ad değişiklikleri:** #22 birleşip yayına girdikten sonra betiğin canlıda çalıştırılması.
