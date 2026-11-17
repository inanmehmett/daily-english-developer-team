# Öneri: "Okuma Yolculuğun"u okuma yoluna çevirmek

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Durum: yön önerisi, Mehmet onayı bekliyor.**
**Dayanak (canlı veri):** `raporlar/2026-11-16_neden_kalmiyorlar.md` (ilk gün metin bitirenlerin D1'i 19/53, iki ve üzeri bitirenlerin 7/11 [az veri], hiç okumayanların 3/58; gidenlerden 51 kişi bir metni bitirip 32'si ikinci metne geçti), `raporlar/2026-11-17_okuma_yolculugu_verisi.md` (sayfayı müşterilerin %10'u görüyor, okumaya ek yöneltmesi yok).
**Koddan:** Rütbeler zaten CEFR bantlarına bağlı (`career_level.dart`, her rütbenin `cefrLevel` alanı); ilerleme XP ile, okuma yeterliğiyle değil. Seviye ölçümü ve yeniden ölçüm özelliği var (`level_progression/`).

## Teşhis
Sayfa "ne kadar puan topladın"ı gösteriyor, "sırada ne var"ı göstermiyor. Düğümler XP eşikleri; bir düğüme dokununca okunacak bir şey yok. Kullanıcı yolu görmek için sayfaya gitmek zorunda; %90'ı gitmiyor.

## Öneri: düğüm = metin, yol = ana sayfa
1. **Her düğüm okunacak bir metin** (ya da bir dizinin bölümü). Bugünün düğümü bir sonraki metin; metni bitirmek düğümü açar, yol bir adım ilerler.
2. **Yol kullanıcının seviyesinde kurulur** (onboarding'deki ölçüm/beyan), ilgi alanlarıyla sıralanır. İlk düğümler kısa ve bitirilebilir.
3. **Yolun omurgası CEFR, rütbe adları değil.** "A2 · 6/20" gibi. Bant sonunda seviye yeniden ölçülür (mevcut ölçüm özelliği); geçen bir sonraki banda geçer.
4. **Yol ana sayfaya taşınır:** ana sayfanın ilk kartı "yolundaki sıradaki durak". Ayrı sayfa haritayı ve geçmişi gösterir.
5. **Metin bitince döngü:** bitiş ekranı bir sonraki durağı gösterir ("Sıradaki: …, ~4 dk"). Bu metinde baktığın kelimeler ertesi günün kısa tekrarı olur; günlük bildirim yarının durağını söyler (README madde 9: sahte aciliyet yok).

## Üyeler
- **Steve:** Veri tek bir şeyi net gösteriyor: ilk gün metin bitiren dönüyor. Yol, "bir metin daha"yı kolaylaştırmanın düzenli hali. En küçük sürümden başlansın.
- **Paul:** CEFR omurgası gerçek bir anlam taşıyor; Türk öğrenci A2/B1'i sınavlardan tanıyor. Ama bir CEFR bandı aylar sürer; ilerleme hissi için bant içi adım (metin sayısı) şart. XP'yle ilerleyen bir "B1" rozeti okuru yanıltır; banda geçiş ölçümle olmalı.
- **Don:** Kullanıcı hiçbir zaman "şimdi ne yapayım" diye kalmamalı. Yol ana sayfada değilse yine %10 görür.
- **Dieter:** Harita görseli var; düğümlerin anlamını değiştirmek yeni ekran yapmaktan ucuz. Ana sayfadaki kart tek ana düğmeli olmalı.
- **Sean:** "B1'e geçiş" gerçek bir hedef; Premium'un vaadi bu olabilir (bant sonunda ücretsiz metinler biter, yol Premium'la devam eder). Paywall'u yolun içine koymak bugünkü dağınık şeritlerden daha dürüst.
- **Nate:** Ölçülecek tek sayı: ilk gün iki metin bitirenlerin oranı ve D1. "İki metin bitiren daha çok dönüyor" bir bağıntı; yol bunu artırır ama dönüşü artıracağı kanıtlanmadı.
- **Nassim:** İkinci metne geçenler zaten istekli olanlar olabilir; yolu kurmak onları çoğaltmaz, yalnız saydırır. Büyük yeniden tasarıma girmeden önce küçük bir sınama yapılmalı.

## Önerilen sıra
1. **Küçük sınama (1–2 gün iş):** metin bitiş ekranında bir sonraki metin önceden seçilmiş olarak tek düğmeyle sunulsun ("Sıradaki: …"); ana sayfanın ilk kartı da aynı metni göstersin. Ölçü: ilk gün ikinci metne geçiş ve D1, sürüme göre.
2. **Sınama işe yararsa:** yol sayfası düğüm = metin olarak yeniden kurulur, CEFR omurgası ve bant sonu ölçümüyle.
3. **CEFR'e geçiş:** rütbe adları ya kaldırılır ya da CEFR'in altında süs olarak kalır (karar Mehmet'in).

## Mehmet'ten beklenen
- Yön onayı (düğüm = metin, yol ana sayfada).
- Rütbe adları: kalksın mı, CEFR'in altında kalsın mı?
- Bant içi adım: metin sayısı mı, kelime sayısı mı?
