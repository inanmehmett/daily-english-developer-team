# Okuma yolu – sistem tanımı (taslak v1) ve açık uçlar analizi

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Çerçeve:** `ortak/okuma_yolu_sinirlari.md`. **Durum:** Mehmet'in onayını bekliyor; onaylanınca editör görevine dönüşür.
**Koddan doğrulananlar (Flutter `d5e4343`, backend):** onboarding'de plan ekranları (`obPlan*`), seviye, günlük dakika (`obMinutes*`), okuma saati, ilgi alanı, "neden öğreniyorsun" (`obGoal*`), söz ekranı ("İlk hedef küçük: 7 gün üst üste okumak", `obCommit*`); 11 bildirim türü (`NotificationType`); 8 paywall tetikleyicisi (`PaywallTriggerType`).

## 1. Dil: "senin yolculuğun"
- "Bugünün durağı" soğuk (Mehmet). Sahiplik dili: **"Senin yolculuğun"**.
- Onboarding'in plan ekranı ("Planın hazır") yolculuğu doğurur: "{ad}, yolculuğun hazır" + ilk dört durağın adları.
- Ana sayfa kartı: "Yolculuğun · 2/4 · Sıradaki: Kapıdaki Kedi". Bitiş ekranı: "Yolculuğunda bir durak daha".
- Dürüstlük: plan bugün "seviyene **ve ilgi alanlarına** göre seçiliyor" diyor (`obPlanStageStories`); yolculuk yalnız seviyeye göre. Ya ilgi alanı yolculuk seçiminde kullanılır ya da metin "seviyene göre" olur. (A3 bulgusunun tekrarı.)

## 2. Yolculuk yapısı
| Seviye | Başlangıç (ücretsiz, 4) | 1. yolculuk | Sonraki (öneri) |
|---|---|---|---|
| A1 | Ramadan → Two Cups → Thirty-One Mornings → The Bench | New in Town (10) | Coffee Shop (A2) |
| A2 | Ali's First Snow → Cat Knows the Time → Baba Yaga → Rabbits | Coffee Shop (12) | Dünya şehirleri B1 |
| B1 | Village → Penguins → Berlin Wall note → Girl Who Fell | Dünya şehirleri B1 (10) | Dünya şehirleri B2 (15) |
| B2 | **tanımsız** | Dünya şehirleri B2 (15) | Second Chances (12) |
| C1–C2 | **tanımsız** | Sherlock (4) / klasik öyküler | klasik romanlar |

## 3. Kurallar
- **Açılma:** ücretsiz kullanıcıda her yerel günde bir durak; durak gece yarısı açılır, bildirim kullanıcının seçtiği okuma saatinde gider. Premium'da bekleme yok.
- **Ücretsiz sınır:** başlangıç 4 + her yolculuğun ilk 2 durağı.
- **Satış anları:** (1) başlangıç bitince: ilerleme kartı + 7 gün deneme; (2) yolculukların 3. durağında. Günde en çok bir teklif.
- **Sıra:** diziler bölüm sırasıyla, atlanmaz. Sırasız yolculuklarda (şehirler) "bugün bunu değil" günde bir kez.
- **Yolculuk bitince:** sıradaki yolculuk otomatik atanır; seçim yok.

## 4. Gözden kaçabilecek noktalar (analiz)

**A. Vaatlerle çakışmalar**
1. **7 günlük söz kırılır.** Onboarding "7 gün üst üste okumak" sözü aldırıyor. Ücretsiz yol: 4 başlangıç + 2 yolculuk durağı = **6 gün**. Denemeyi almayan ücretsiz kullanıcı 7. gün okuyacak durak bulamaz ve serisi kırılır. Seçenekler: (a) yolculukların ilk **3** durağı ücretsiz, (b) 7. gün "pekiştirme günü" (baktığı kelimelerin tekrarı seriye sayılır), (c) söz 6 güne iner.
2. **Günlük dakika hedefi tutmaz.** Kullanıcı 10–15 dk seçebiliyor; ücretsiz bir durak 2–5 dk. Dakikadan türeyen günlük XP hedefi ücretsiz kullanıcı için ulaşılmaz olur. Öneri: günün hedefi "bugünün durağı"; dakika yalnız Premium'da anlam taşır.
3. **İlgi alanı sorusu kullanılmıyor** (madde 1).

**B. Mevcut sistemlerle çakışmalar**
4. **8 paywall tetikleyicisi** (onboarding, highEngagement, milestone, quizSuccess, streakAtRisk, winBack, limitReached, manual) ve kampanya/hediye/deneme şeritleri var. Çerçeve iki satış anı ve günde bir teklif diyor. Her tetikleyici ya bu iki ana bağlanmalı ya kapatılmalı; özellikle **streakAtRisk** (seri kaybı korkusuyla satış) madde 9'la çatışabilir.
5. **11 bildirim türü** (Streak, StreakStart, StreakRepair, Activation, TrialEnding, Promotion, VocabReview, DailyQuiz, DailyUnlock, NewContent, WinBack). Yolculuk kullanıcısına günde tek mesaj: "Durağın açıldı / yolculuğun seni bekliyor". Diğerleri ya bu mesaja katılır ya susar. Streak bildirimindeki "kayıp korkusu" çerçevesi gözden geçirilmeli.
6. **Bugünkü ücretsiz kurallar** (3 her zaman açık + 21 metinlik günlük havuz, herhangi bir metin) yolculuk kurallarıyla değişir. Keşfet'te ücretsiz kullanıcı günlük hakkını yolculuk dışına harcarsa yolculuk durur. Öneri: günlük hak yalnız yolculukta.
7. **Okuma Yolculuğu sayfası, rütbe ve XP.** Aynı adı taşıyan iki kavram olmaz: mevcut harita yolculuk haritasına dönüşür (Dieter). Rütbe adlarının kaderi hâlâ açık (17 Kas, CEFR tartışması).
8. **Günün quizi, kelime defteri, kelime tekrarı** döngüde "pekiştirme" adımına bağlanmalı; ayrı ayrı çağırmamalı.

**C. Kenar durumlar**
9. **B2 ve üstü için yolculuk tanımsız.** Ölçüm B2+ verirse ne olur? (Öneri: B2 → şehirler B2; C1+ → Sherlock ve klasik öyküler; ayrı karar.)
10. **A1'de ikinci yolculuk yok.** New in Town'dan sonra A1 okur Coffee Shop'a (A2) geçer; sıçrama büyük olabilir. A1 içerik açığı ayrı iş.
11. **Seviye yanlışsa.** Yolculuk zor ya da kolay gelirse kullanıcı karar vermeden nasıl düzelir? Öneri: 50 kelimede bakış eşiği aşılırsa uygulama kendisi yeniden ölçüm önerir.
12. **Mevcut kullanıcılar** (~240 müşteri, 3 abone). Yolculuğa nereden başlarlar? Öneri: seviyeleri ve bitirdikleri metinler korunur, ilk bitmemiş duraktan başlarlar; aboneler doğrudan seviye yolculuğuna.
13. **Deneme bitince.** 7 günde yolculuğun çoğunu okuyan kullanıcı ödemezse nerede kalır? Bitirdikleri kalır, kalan duraklar kilitlenir; açık anlatılmalı.
14. **Hızlı Premium okur** 10 durağı bir günde bitirir; sıradaki yolculuk hazır olmalı (kuyruk tanımı, madde 2).
15. **Yerel gün ve saat dilimi.** Bazı müşteriler UTC−8'de (iOS denemesi). "Gün" sunucuda değil cihaz yerel saatinde hesaplanmalı.

**D. Kalite ve ölçüm**
16. **Çeviri kalitesi önce yolculuk metinlerinde.** 44 metnin (4×3 başlangıç + 32) kelime anlamları bozmama kapısıyla öncelikli kontrol edilsin.
17. **Android satışı.** Satış anları kurulmadan önce Android satın alma akışı test hesabıyla denenmeli (açık madde).
18. **Ölçüm olayları baştan eklenmeli:** yolculuk atandı, durak açıldı, durak başladı/bitti, teklif gösterildi (an), teklif kabul/ret, "bugün bunu değil".
19. **Seslendirme hızı** A1'de dakikada 132–153 kelime; A1 yolculuğu için Mehmet dinleyip karar vermeli (içerik incelemesi P7).

## 5. Mehmet'ten beklenen kararlar
1. 7 gün sözü: yolculukların ilk 3 durağı mı ücretsiz, pekiştirme günü mü, söz mü değişir?
2. Günlük dakika hedefi: "bugünün durağı" ile mi değişir?
3. Paywall tetikleyicileri: iki satış anı dışındakiler (özellikle streakAtRisk) kapansın mı?
4. Bildirimler: yolculuk kullanıcısına günde tek mesaj mı?
5. B2 ve C1+ yolculukları.
6. Rütbe adları: kalkar mı, CEFR'in altında mı?
