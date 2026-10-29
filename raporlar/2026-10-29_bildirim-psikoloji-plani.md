# Bildirim / elde tutma psikoloji planı — ekip değerlendirmesi

**Tarih:** 29 Eki 2026 · **Kadro:** Kent Bekçi, Don Normal, Nate Gümüş, Sean Büyüt, Nassim Talip, Steve İşler (tek geçiş)
**Kaynak:** Mehmet'in ayrı bir oturumda aldığı 7 maddelik bildirim/elde tutma planı + aynı oturumdaki şeytanın avukatı itirazı (iki ek dosya olarak paylaşıldı).

## Özet
Plan iyi kurulmuş ama kanıtlanmamış varsayımlar üzerine fazla yük bindiriyordu (kontrol grubu, A/B varyant sistemi, profil yeniden tasarımı, paylaşım kartı — hepsi gerçek kullanıcı yokken). Devil's advocate'in itirazlarının çoğu ekip tarafından **haklı bulundu**. Ekip, devil's advocate'in önerdiği küçültülmüş kapsamı onaylıyor.

## Üye görüşleri
- **Kent Bekçi (geliştirme):** Faz sıralaması (önce sunucu/ölçüm, sonra uygulama, en son tasarım) doğru; kod tabanında zaten `CelebrationCoordinator` var, kesinti bütçesini onun üzerine genişletmek doğru yaklaşım, sıfırdan yazmaya gerek yok.
- **Nassim Talip (şüpheci):** İtirazlar isabetli — özellikle (a) birkaç yüz test hesabıyla %10 kontrol grubu + varyant sisteminin istatistiksel olarak anlamsız olması, (b) "bu gece duraklar" ifadesinin dürüst ama tehditsiz olması (kendi affedici mekanizmamız kayıp dilini zayıflatıyor), (c) günlük seri vs haftalık hedef sorusunun asıl kimlik kararı olduğu ve veriden önce Mehmet'in sezgisini gerektirdiği.
- **Don Normal (UX):** İzin penceresinin bölüm bitişine taşınması ve kullanıcının kendi saatini seçmesi iyi karar (uygulama niyeti etkisi + özerklik). Profil yeniden sıralaması, Kaydedilenler ve paylaşım kartı gibi büyük tasarım işleri gerçek kullanıcı verisi gelmeden ertelenmeli — devil's advocate'le aynı fikirdeyiz.
- **Nate Gümüş (veri):** `push_opened` olayı tek başına yeterli başlangıç; kontrol grubu ve varyant sistemi şimdi aşırı mühendislik. Gerçek kullanıcı geldikten sonra (lansmandan 2–4 hafta sonra) tekrar değerlendirilir.
- **Sean Büyüt (büyüme):** Paylaşım kartı (görsel) yerine önce Wordle tarzı kopyalanabilir metin ızgarası denenmeli — maliyeti çok daha düşük, viral potansiyeli muhtemelen daha yüksek (Instagram hikâyesinden indirme zaten zor, görsel kart bu sorunu çözmüyor).
- **Steve İşler (karar):** İtirazların çoğu kabul edildi. Devil's advocate'in "şimdi yapılacaklar" listesi (4 madde) onaylanıyor, gerisi lansman sonrası gerçek veriye erteleniyor.

## Karar: şimdi yapılacaklar (ucuz, geri alınabilir, açık hata düzeltmeleri)
1. **Quiz çeviri/şık denetimi** — kanıtlanmış hata (ör. "lot" sorusunda iki doğru şık olabiliyor); Türkçe anadili konuşan biri örneklem kontrolü yapmalı (Mehmet'in kendisi tek başına yapmamalı — kendi hatasını kendi kontrol etmesin).
2. **`push_opened` olayı** — kontrol grubu ve varyant sistemi olmadan, yalın ölçüm.
3. **İzin penceresi** — açılıştan kaldırılıp bölüm bitiş ekranına, paywall'dan ayrı bir oturuma taşınacak.
4. **Akşam seri bildirimi** — yalnızca zamanlama akşama (19–21) kayacak, metin değişmeyecek.

## Ertelenen (gerçek kullanıcı verisi gelene kadar — lansmandan 2–4 hafta sonra)
- Günlük seri mi, haftalık hedef mi (ürün kimliği kararı — veri gelmeden Mehmet'in sezgisi gerekiyor)
- Profil düzeni, Kaydedilenler/Okuma listem özelliği, Günün Quizi bildirimi
- Paylaşım: önce metin ızgarası denenecek, görsel kart işe yararsa sonra gelir

## Mehmet'in kararları (29 Eki 2026)
1. **Hatırlatma saati:** Kullanıcı kendi seçsin, varsayılan 20:00. ✅ karar verildi.
2. **Quiz serisi:** Okuma serisinden ayrı kalsın; bildirim/profilde yalnız okuma serisi öne çıkar. ✅ karar verildi.
3. **Ad:** "Okuma listem". ✅ karar verildi.
4. **Günlük seri mi, haftalık hedef mi:** Henüz karar verilmedi. Bu soru veri gelmeden karar verilemeyecek kadar sezgisel bulundu — lansmandan 2–4 hafta sonra gerçek kullanıcı veriyle ekip tarafından tekrar Mehmet'e getirilecek. Haftalık şerit tasarımı bu karara kadar bekler.

## İtirazlar (çözülen)
- Kent Bekçi: "Kesinti bütçesi sıfırdan mı yazılacak?" → Hayır, mevcut `CelebrationCoordinator` genişletilecek (devil's advocate'in notuyla uyumlu).
- Nassim Talip: "Ölçüm altyapısı (kontrol grubu + varyant) şimdiden mi kurulsun?" → Hayır, yalnız `push_opened`; kontrol grubu gerçek kullanıcı kitlesi oluşunca değerlendirilir.
