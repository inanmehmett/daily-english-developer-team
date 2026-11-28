# 08 · Başlangıç metinleri, 2. adım (kuyruk 12.1 ve 12.2)

**Tarih:** 28 Kasım 2026 · **Kaynak:** canlı veritabanı (salt okuma) ve kod · 12.3–12.6 henüz yapılmadı.

## 12.1 · 1036 Santorini
- **Erişim: Premium.** `IsStarterPack` = hayır, `IsDailyUnlock` = hayır. Ücretsiz kullanıcı bugün açamıyor.
- **Ses: var.** 17/17 cümle, Google Chirp 3 HD "Charon" (`chirp3-hd-charon`), hız 0,94; 17/17 kelime zamanlamalı.
- **Kelime anlamları:** elle bağlanmış bağlam karşılığı yok. Balonlar çözümleyiciden geliyor, dokunulan cümleye göre.
- **Son hâl yazılırsa etkilenenler** (ayrıntı: `raporlar/2026-11-28_santorini_degisiklik.md`):
  - Ses: 19 cümlenin 9'u yeniden üretilir, 10 klip korunur (6'sı yeni sıraya taşınır). Aynı ses, aynı hız.
  - Kelime zamanlaması: yeni 9 klip için hizalama betiği.
  - Cümle çevirileri: yeni 9 cümle için (DeepL), ses üretimiyle birlikte.
  - Quiz: 4 sorudan 3'ü eski metinden alıntılıyor, uyarlanır.
  - Balonlar: değişen cümlelerde 6 zayıf balon, bağlam karşılığıyla düzeltilir.
  - Kelime sayısı alanı 172 → 182 (ilk metin seçimi bu alana bakıyor, aşağıda).
  - Değişmeyenler: Türkçe ad, açıklama, özet, kapak, okuma süresi (2 dk).

## 12.2 · Başlangıç metnini değiştirmek kod mu, veri mi?
**Veri.** Kural kodda sabit, girdileri veride.

- **Kural (uygulama, `lib/features/home/presentation/widgets/first_read_card.dart:57`, `FirstReadCard.pickBook`):** okurun seviyesindeki **açık** (kilitsiz) metinlerin **en kısası** (kelime sayısına göre). Seviyede açık metin yoksa en yakın seviye; üst seviyeye kaçmak iki kat cezalı. Onboarding sonu (`onboarding_v2_page.dart:447`) ve ana sayfadaki "ilk okuma" kartı aynı kuralı kullanıyor.
- **Açık sayılan:** Premium gerektirmeyen metin, yani başlangıç paketi (`ReadingTexts.IsStarterPack`) ya da o gün günlük hakla açılmış havuz metni.
- **Bugün A2'de:** açık tek başlangıç metni 1023 Rabbit Island (287 kelime). A2 okurun ilk metni bu yüzden Rabbit Island. 127 Ali's First Snow (121 kelime) günlük havuzda; okur onu o gün açtıysa ilk metin kartı ona döner.
- **Başlangıç yolculuğu ayrı bir şey:** `Journeys` / `JourneyStops` tablosu, `starter-a2` durakları 127 → 1070 → 1045 → 1023. Yolculuk kartının sırası; ilk metin kartını belirlemiyor.

**Santorini'yi A2 ilk metni yapmak için:** `ReadingTexts` satırında 1036 için `IsStarterPack` = evet. Santorini (yeni hâliyle 182 kelime) Rabbit Island'dan (287) kısa olduğu için kendiliğinden ilk metin olur; Rabbit Island'ın bayrağına dokunmak gerekmez. Rabbit Island'ın B1'e geçmesi (`TextLevel`) ayrı bir karar. Yan etkisi: Santorini herkese ücretsiz olur. İstenirse `starter-a2` yolculuğuna da durak olarak eklenir (ayrı satır).

**Geri alma:** aynı satırda bayrağı geri çevirmek; betik önceki değeri yedek tabloya alır (ad değişikliği betikleriyle aynı kalıp). Uygulama güncellemesi gerekmez; liste yenilenince etkili olur.

**Sıra:** önce Santorini'nin metni, sesi ve zamanlaması (kuyruk 13), sonra bu bayrak. Mehmet'in ayrı "yap"ıyla.
