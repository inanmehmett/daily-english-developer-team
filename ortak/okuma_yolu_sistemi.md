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

---

## Tur 2 (17 Kas 16:51) – Mehmet'in cevapları ve ekip tartışması

**Kararlar (Mehmet):**
- İlgi alanına göre seçim mümkün olduğunca yapılır; o seviyede ilgi alanına uygun içerik yoksa slotu ekip doldurur. Plan ekranındaki "ilgi alanına göre" ifadesi böylece doğru olur.
- 7 günlük söz tutulur.
- Günlük ücretsiz hak kullanıcının; istediği metne harcar.
- Seviye zorunlu: herkes seviye ölçümünden geçer; ama istediği içerikten de okuyabilir.
- Gün cihazın yerel saatine göre. Mevcut harita yolculuk haritasına dönüşür.
- Yeni içerik her seviyeye (B2 dahil) gelecek.

**1. 7 günlük söz nasıl tutulur:** Günlük hak her gün var; söz bununla tutulur. Ücretsiz yolculuk durakları bitince ana sayfa kararı kullanıcıya bırakmaz: "Bugünün ücretsiz okuması" olarak seviyesine ve ilgi alanına uygun bir havuz metnini önerir, yanında "Yolculuğuna Premium'la devam et". Keşfet'ten başka metin seçmek serbest.

**2. Ücretsiz kullanıcı ve özellikler (koddan doğrulandı, `EntitlementConstants.cs`):** Ücretsizde kelime çevirisi günde 25, kelime defteri ilk 7 gün sınırsız, sonra toplam 15 kelime. Yani özellikler kapalı değil, sayılı.
- Bir metne yetiyor mu: 300 kelimelik metinde 50 kelimede 1,2–3,3 bakış = 7–20 bakış (katalog verisi). 25 hak tek metne yetiyor.
- **Steve/Sean:** Bütün özellikleri sınırsız vermek gerekmiyor; vermek satışı artırmaz. Doğru olan, çekirdek değeri (kelimeye dokunup anlamak) ilk günlerde tattırmak, derinliği (sınırsız defter, aralıklı tekrar, beklemeden devam) satmak. Bugünkü kurgu buna uygun.
- **Nate:** Kanıt: en çok kelimeye bakan dilim en çok bitiren ve en çok dönen dilim (`2026-11-16_neden_kalmiyorlar.md` S4); cümle çevirisi kullananlar daha çok dönüyor. Çekirdek özelliği kısmak tutmayı düşürebilir; 25 sınırı yerinde.
- **Dakika hedefi:** sorun özellik değil süre. Ücretsiz bir durak 2–5 dk; kullanıcı 10–15 dk seçebiliyor. Öneri: günlük hedef dakika değil görev listesi (madde 4); dakika Premium'da serbest okumayla dolar. Paul: metni sesle yeniden dinlemek/okumak gerçek öğrenme, hedefe sayılabilir.

**3. Satış anları – çerçeve revize:** Mehmet haklı: herkes sonu beklemez; doğrudan almak isteyene kapı her zaman açık olmalı.
- **Revize kural:** (a) Premium'a giden yol her zaman görünür (ana sayfa, profil, kilitli durak); bunlar teklif sayılmaz. (b) Araya giren teklifler (ekranı kesen) günde en çok bir; değer anı ve hikâye anında. (c) Onboarding sonundaki teklif: önce veriye bakılacak.
- **Dikkat (Nate):** Son günlerde iki değişiklik yapıldı: onboarding sonu paywall ilk okumaya ertelendi; Premium şeridi hiç metin bitirmemiş kullanıcıya gösterilmiyor (V8, `8069597`). Eğer şimdiye kadarki alıcılar bu yüzeylerden aldıysa satışı farkında olmadan kısmış olabiliriz. Önce dört satın almanın hangi yüzeyden, kayıttan kaç dakika sonra ve kaç metin okunmuşken yapıldığı canlıdan okunmalı. (V7'deki deneme kayıttan 35 sn sonra başlamış ve iptal edilmişti; tek örnek.)

**4. Bildirimler – tek mesaj yerine iki mesaj + uygulama içi görev listesi:**
- **Uygulama içi "Bugünün görevleri"** (ana sayfanın ilk kartı, sıralı): (1) yolculuk durağı, (2) zamanı gelen kelime tekrarı (X kelime), (3) günün quizi. Tek düğme: "Sıradaki görev". Her görev bitince sıradakine geçer; bitince "Bugünü tamamladın". Kullanıcı karar vermez, uygulama sıralar.
- **Bildirim en çok iki:** (1) gün içinde, kullanıcının okuma saatinde: "Bugün 3 görevin var: durak, 6 kelime, quiz" (tek mesajda topluca); (2) akşam, yalnız gün tamamlanmadıysa ve seri varsa: seri hatırlatması. Yeni içerik bildirimi isteğe bağlı, haftada en çok bir.
- **Don:** Kullanıcı uygulamaya bildirim olmadan da girdiğinde aynı listeyi görür; görevleri bildirime değil ana sayfaya bağlamak asıl çözüm.
- **Nassim:** Akşam seri mesajı "kaybedeceksin" diliyle değil "bugün 1 durak kaldı" diliyle yazılmalı (madde 9).
- **Bugünkü 11 bildirim türü** bu iki mesaja eşlenir; eşlenemeyen susar (Activation, WinBack gibi geri kazanım mesajları ayrı kural: haftada bir).

**Diğer:**
- **Seviye zorunlu:** onboarding'deki seviye ölçümü atlanamaz olur (yeni ekran eklenmez; var olan tur zorunlu hale gelir). Nassim: zorunlu test onboarding'i bırakanları artırabilir; ölçülsün.
- **Günlük hak serbest:** Keşfet'te başka metin açan kullanıcının yolculuğu o gün ilerlemez; ana sayfa ertesi gün yine yolculuğu önerir.

**Mehmet'ten beklenen:**
1. Görev listesi (durak, tekrar, quiz) ana sayfanın ilk kartı olsun mu?
2. Bildirim: günde en çok iki (görev çağrısı + koşullu akşam) uygun mu?
3. Satış yüzeylerinin kararı canlı veriden sonra; editöre dört satın almanın dökümü sorulsun mu?
