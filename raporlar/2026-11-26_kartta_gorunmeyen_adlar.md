# Kartta görünmeyen Türkçe adlar ve adsız dizi kartı

**Tarih:** 26 Kasım 2026, 21:30 · **Bildiren:** Mehmet ("The Market That Moves ve Rabbit Island'ın Türkçe isimleri ana sayfada kartta görünmüyor. Önerilenler arasında gösterilen Game Day dizisinin ne Türkçe ne de İngilizce adı gösteriliyor.")
**Kaynak:** uygulama kodu, Mehmet'in bilgisayarından okundu (`feat/journey-core`; mağazadaki 1.0.4 bu daldan). Üyeler kurgusaldır.

## 1. Türkçe ad neden görünmüyor
`lib/features/reader/presentation/widgets/book_title_lines.dart`: Türkçe ad **28 karakterden uzunsa satır hiç çizilmiyor** (`maxTrChars = 28`). Koddaki not: "Sınırı aşan ad içerik hatasıdır ve arayüzde '…' olarak görünmemeli: satır hiç çizilmez."
- İstanbul'un Yer Değiştiren Pazarı: 33 karakter → gizli.
- Haritadan Silinen Tavşan Adası: 30 karakter → gizli. **Bu ad 26 Kasım 17:52'de canlıya yazılan onaylı 15 addan biri.**

**Ekibin hatası:** ad listesi üç kez okundu ama kartın 28 karakter sınırına bakılmadı. "Bir özellik hakkında konuşmadan önce koda bak" kuralı ad uzunluğu için uygulanmadı.

### Etkilenen adlar
Onaylı 15 addan beşi sınırı aşıyor ve şu an kartlarda görünmüyor:
| Kimlik | Türkçe ad | Karakter |
|---|---|---|
| 1045 | Baba Yaga: Tavuk Bacaklı Kulübe | 31 |
| 1023 | Haritadan Silinen Tavşan Adası | 30 |
| 1055 | Kasırgadan Sonra Kırk Bir Gün | 29 |
| 1063 | Günde İki Kahvaltı Yapan Ülke | 29 |
| 148 | İtalyanlar Neden Çok Konuşur? | 29 |
Katalogda bunlardan önce de sınırı aşan **23 ad** vardı (hepsi Premium metinlerde; örnek: Shakespeare: Kelime İcat Eden Adam 34, İskenderiye'nin Kayıp Kütüphanesi 33, İstanbul'un Yer Değiştiren Pazarı 33, Küllerinden Doğan Şehir: Londra 31). Toplam 28 metnin Türkçe adı kartlarda yok.
Ana sayfanın üstündeki büyük slayt bu kuralı kullanmıyor; orada uzun ad tek satırda "…" ile kesiliyor.

## 2. Game Day dizi kartı neden adsız
`lib/features/series/presentation/widgets/series_card.dart`: dizi kartı kapağın altına yalnız seviye ve bölüm sayısını yazıyor. Koddaki not: "Koleksiyon adı + başlık kapağın içinde gömülü; altta sadece meta." Yani kart, dizinin adının kapak resminde yazılı olduğunu varsayıyor. Game Day'in kapağında ad yoksa ya da resim yüklenmediyse kartta hiçbir ad kalmıyor.

## 3. Ekip kararı
1. **Arayüz adı gizlemeyecek (sonraki derleme).** Mehmet'in ölçütü: kart uzunluğu için ad kalitesi feda edilmez. Türkçe ad en çok iki satıra sarılır; iki satıra da sığmayan ad son kelimeden kesilir. Görünüm değişikliği: önce taslak (Dieter, Don), sonra kod.
2. **Dizi kartında ad her zaman yazılır:** kapağın altında dizinin adı, altında seviye ve bölüm sayısı. Kapakta ad olsun olmasın.
3. **O derleme mağazaya çıkana kadar:** sınırı aşan beş yeni ad için 28 karakteri geçmeyen karşılık, turlardan geçip Mehmet'in onayına. Eski 23 ad için ayrı liste.
4. **Kural:** bundan sonra her ad önerisinin yanında karakter sayısı yazılır; ad önerilmeden önce o adın göründüğü her yerin sınırı koddan okunur.

## 4. Beş ad için 28 karakteri geçmeyen karşılık (turlu; Mehmet'in onayına)
Tur 1 taslak (Tomris, Paul) → bağımsız göz (adayları görmüş, gerekçeyi görmemiş ayrı oturum; karakterleri tek tek saydı) → tur 3 metinle doğrulama. **Canlıya yazılmadı.**
| Kimlik | İngilizce ad | Şu an (kartta görünmüyor) | Öneri | Karakter | Dayanak |
|---|---|---|---|---|---|
| 1023 | Rabbit Island: Missing from the Map | Haritadan Silinen Tavşan Adası (30) | **Haritadan Silinen Ada** | 21 | Eski ad; "tavşan" üst satırdaki "Rabbit Island"da okunuyor. Açıklama: "Haritalardan bilerek silinmişti." |
| 1055 | Forty-One Days After the Hurricane | Kasırgadan Sonra Kırk Bir Gün (29) | **Kasırgadan Sonra 41 Gün** | 23 | Anlam aynı, yalnız sayı rakamla; kümede "Denizde 133 Gün" de rakamla |
| 1045 | Baba Yaga | Baba Yaga: Tavuk Bacaklı Kulübe (31) | **Baba Yaga ve Yürüyen Kulübe** | 27 | Metin: "It stands on two giant chicken legs, and it can walk." Açıklama: "yürüyen bir kulübe vardır" |
| 1063 | The Country That Eats Breakfast Twice | Günde İki Kahvaltı Yapan Ülke (29) | **İki Kez Kahvaltı Eden Ülke** | 26 | İngilizce adın birebir karşılığı; "kahvaltı etmek" yerleşik fiil |
| 148 | Why Italians Love Talking | İtalyanlar Neden Çok Konuşur? (29) | **İtalyanlar Neden Konuşkan?** | 26 | "Konuşkan" sevecen; "çok konuşur" hafif yergi taşıyordu |

**Turlarda elenenler:** "Silinen Tavşan Adası" (ada yok olmuş gibi okunuyor; uzun adın sakat hâli) · "Tavşan Adası'nın Sırrı" (çocuk kitabı kalıbı, gerçek olayı masallaştırıyor) · "Okyanusta Kırk Bir Gün" ("Denizde 133 Gün" ile karışıyor, kasırga kayboluyor) · "Baba Yaga'nın Kulübesi" (doğru ama kulübeyi özel yapan şey yok) · "Baba Yaga Masalı" (etiket) · "Baba Yaga: Tavuk Bacaklı Ev" (metin "hut" diyor; "ev" tutmuyor) · "Günde İki Kahvaltı Eden Ülke" ("iki kahvaltı etmek" eğreti) · "İki Kahvaltılı Ülke" (otel ilanı dili) · "İtalyanlar Niye Çok Konuşur?" ("niye" yalnız bir harf kazanmak için).
**Sınır yüzünden gerçek kayıp:** yalnız Baba Yaga'da; "tavuk bacaklı" görüntüsü ad ile birlikte 28'e sığmıyor. Arayüz düzeltilince (iki satır) "Baba Yaga: Tavuk Bacaklı Kulübe" geri konabilir. Öbür dördünde kayıp yok; ikisi kısalınca daha doğal oldu.

**Onay (Mehmet, 26 Kas 23:19):** beş ad onaylandı. Editör görevi: `ortak/editor_gorevi_2026-11-26_bes_ad_kisaltma.md`.
