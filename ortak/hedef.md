# Hedef ve takip

## Hedef
Uygulamayı yayına çıkarmak (iOS + Android), @gunluk_ingilizce kitlesinden sürdürülebilir bir test/kullanıcı/abone hunisi kurmak ve geliri büyütmek.

## Sayısal hedef (ekip önerisi, 6 Kas 2026)

Mehmet'in isteği üzerine ekip (Steve İşler + Nate Gümüş + Sean Büyüt) sayısal hedefi önerir. **Varsayımla değil, Play Console ve App Store Connect'ten çekilen gerçek taban veriyle:**

**Taban (6 Kas 2026 itibarıyla gerçek veri):**
| Platform | Toplam indirme (lansmandan beri) | Son dönem aktif/MAU | Ödeyen abone | Gelir |
|---|---|---|---|---|
| Android (Play Console, 30 Eki–6 Kas) | 60 | 23 (son 28 gün, +%130) | 0 | 0 TRY |
| iOS (App Store Connect, son 90 gün penceresi) | 77 (ilk kez indirme) | — (dönüşüm oranı %5,88 günlük ort.) | 1 (3 aktif plan, 1 ödemeli) | $3 |
| **Toplam** | **~137** | — | **1** | **~$3** |

**Sean Ellis mantığı (Sean Büyüt'ün dayanağı):** PMF henüz ölçülmedi, ödeyen kullanıcı sayısı tek haneli. Bu aşamada büyük/iddialı bir büyüme sayısı koymak yanlış sinyal verir — önce mütevazı bir checkpoint, sonra PMF anketi sonucuna göre revize.

**Önerilen checkpoint (4 hafta, 6 Kas – 4 Ara 2026):**
1. Toplam indirme: ~137 → **en az 275** (taban düşük olduğu için yüzdesel büyüme kolay; asıl anlamlı olan 2. ve 3. madde).
2. Android aylık aktif cihaz: 23 → **en az 60**.
3. Ödeyen abone: 1 → **en az 5**.
4. PMF anketi (Sean Ellis, "%40 çok hayal kırıklığına uğrardım" eşiği) bu 4 hafta içinde en az bir kez uygulanmış olsun.

Bu sayılar **hedef değil, ilk checkpoint** — tek haftalık veriden türetildi, gerçek trend görülünce (2-3 hafta sonra) revize edilecek. Nassim Talip'in itirazı aşağıda.

### İtiraz
- **Nassim Talip:** Bu sayılar bir haftalık veriden çıkarıldı, trend değil. "Hedef" diye sunmak yanıltıcı olabilir — "checkpoint, 2 hafta sonra revize edilecek" etiketiyle kaydedildi. **Kabul edildi.**

## Huni (takip edilecek)
1. Instagram'dan beta sayfasına tıklama (getdailyenglish.com/beta)
2. Beta sayfasından başvuru
3. Uygulamayı indirme / hesap açma
4. Aktivasyon (ilk ders/XP)
5. Abonelik (haftalık/aylık/yıllık)
6. Elde tutma (7 gün / 30 gün)

## Haftalık hedef kontrolü (her Pazartesi raporun ilk bölümü)
1. Bu haftaki huni sayıları (varsa) ve bir önceki haftayla karşılaştırma.
2. Mağaza durumunda değişiklik (yayın, inceleme sonucu, red vb.).
3. Durum: 🟢 yolda / 🟡 belirsiz (veri yok/az) / 🔴 sorun var.
4. 🔴 ise ya da veri yoksa: Steve İşler liderliğinde ekip, veri eksikliğinin ya da sorunun nedenini ve çözümünü önerir.

## Kayıt
| Hafta | Not |
|---|---|
| 29 Eki 2026 | Ekip kuruldu. iOS yayına hazır, Android üretim onayında. Sayısal hedef henüz belirlenmedi. |
| 6 Kas 2026 | Play Console + App Store Connect'ten gerçek taban veri çekildi (toplam ~137 indirme, 1 ödeyen abone, ~$3 gelir). Ekip 4 haftalık checkpoint önerisi sundu (bkz. yukarı). |
| 15 Kas 2026 | Ara kontrol (gerçek veri). iOS (App Store Connect, 13 Kas'a kadar): 160 ilk indirme, 3 ödemeli plan (5 aktif), 6 uygulama içi satın alma, 20 dolar gelir, 7. gün indirmeden ödemeye %2,33; elde tutma (yalnız izin verenler) 1. gün ~%10, 7. gün ~%5. Android (Play Console, son 28 gün): 80 edinme, 50 ilk açılış, 56 aylık aktif cihaz, gelir 0. Checkpoint'e göre: toplam indirme ~240/275, Android aktif 56/60, ödeyen 3/5, PMF anketi yapılmadı. |
| 15 Kas 2026 (düzeltme) | **Sayım kuralı (Mehmet):** Abonelik sayarken promosyon/testçi planları sayılmaz; yalnızca yayından sonraki gerçek satışlar baz alınır, önceki abonelikler test dönemine aittir. App Store Connect (13 Kas): 5 aktif plan = 3 Premium Yearly Launch + 2 Premium Monthly; bunların 1'i "Testers" promosyonu, 1'i 1 haftalık denemede. Mehmet'in güncel sayımı: 4 premium satış, 1'i deneme süresinin son günü iptal, 3 aktif. Aktif planların kaynağı: App Store arama 2, başka uygulamadan yönlendirme 2, App Store göz atma 1. |
| 15 Kas 2026 (ekip kararı) | **29 Kasım sınavının sayısı yeniden yazıldı.** Firebase'in 8/26 sayısı uygulamanın kendi kayıtlarıyla tutmadı: onboarding'i bitiren müşterilerin %81–85'i okumaya başlıyor (11–15 Kas 29/34; 29 Eki–10 Kas 92/114). Yeni hedef: bu oran en az %90; uygulamanın kendi kayıtlarından, sürüme göre ayrılarak okunur. Mehmet kararı ekibe bıraktı. Ayrıntı: `raporlar/2026-11-15_editor_bolum1_ek.md`. |
| 25 Kas 2026 | Haftalık kontrol (gerçek veri, Play Console). Android son 28 gün: 180 edinme, 105 ilk açılış, 123 aylık etkin cihaz, gelir 0, puan 4,75. iOS çekilemedi (App Store Connect oturumu kapalı). Checkpoint: toplam indirme en az ~340/275 ✔ (iOS'un 13 Kas sayısıyla), Android etkin 123/60 ✔, ödeyen abone bilinmiyor, PMF anketi yapılmadı (1.0.4 yayınından iki hafta sonraya; 4 Aralık'ta tutmayacak). Mağaza: Play üretimde 1.0.4 (47) 20 Kas'tan beri yayında; 1.0.4 (50) hazır ama incelemeye gönderilmemiş. Durum 🟡. Ayrıntı: `raporlar/2026-11-25_haftalik_rapor_ve_toplanti.md`. |
| 25 Kas 2026 (ek) | App Store Connect (son 30 gün, 23 Kas'a kadar): 323 ilk indirme, 927 sayfa görüntüleme, dönüşüm %6,97, 9 uygulama içi satın alma, 23 dolar gelir, 7 etkin plan, 4 ödemeli plan (promosyon ayrımı yapılmadı), 7. gün indirmeden ödemeye %1,53. iOS'ta 1.0.4 (50) yayında. Checkpoint: toplam indirme ~503/275 ✔, ödeyen en çok 4/5. |
