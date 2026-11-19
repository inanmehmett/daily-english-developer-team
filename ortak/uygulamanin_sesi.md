# Uygulamanın sesi

**Karar:** Mehmet, 18 Kasım 2026: "Kullanıcılar bizim sıcak dostlarımız, canlarımız. Soğukluk olmasın, robotluk da olmasın." · **Sahibi:** Paul Ulus (metin), Dieter Koç (yerleşim).
Uygulamada kullanıcının okuduğu her cümle bu belgeye uyar.

## Kurallar
1. **Bir arkadaş gibi konuş:** "sen" diye, kısa, gündelik Türkçeyle. Resmî ve teknik dil yok.
2. **Önce iyi haber, sonra durum.** "Bugün 25 kelimeye baktın" sınırdan önce gelir.
3. **Sayı ancak yakınsa.** Küçük ve ulaşılabilir sayı cesaret verir ("Çaylak'a 58 XP kaldı"); büyük sayı yıldırır ("3.000 XP kaldı" yazılmaz). Uzaktaysa sayı yerine yol ve davet: "İlerlemeni gör".
4. **Suçlama ve eksik dili yok:** "kaçırdın", "kullandın", "bitti", "yetersiz", "başarısız", "erişim yok" yazılmaz.
5. **Satış da sıcak:** "Premium seni bekliyor", "istersen". Zorlamak, korkutmak, geri sayım yok.
6. **Hata olursa:** kısa bir özür ve ne yapabileceği. Teknik ileti gösterilmez.
7. **Abartı yok:** ünlem ölçülü, övgü gerçek bir şey için. Yapılmayan şey kutlanmaz.
8. **Söz tutulur:** ekrandaki her cümle kodun yaptığıyla aynıdır (README madde 9).

## Bu sürümün metinleri
| Yer | Durum | Metin |
|---|---|---|
| Bitiş ekranı, XP satırı | Sıradaki rütbeye 60 XP ve altı | "+{n} XP · {Rütbe} olmana çok az kaldı!" |
| | 61–200 XP | "+{n} XP · {Rütbe}'a {kalan} XP kaldı" |
| | 200 XP'den uzak | "+{n} XP · {Rütbe} yolunda bir adım daha. İlerlemeni gör ›" |
| | Rütbe o an kazanıldı | "Artık {Rütbe}'sın! Yolunu gör ›" |
| Ana sayfa kişi kartı | Yakın (200 ve altı) | "{Rütbe}'a {kalan} XP · yolunu gör ›" |
| | Uzak | "{Rütbe} yolundasın · ilerlemeni gör ›" |
| Çeviri sınırı | | "Bugün 25 kelimeye baktın, eline sağlık. Yarın yine buradayız. Sınırsız bakmak istersen Premium seni bekliyor." Düğmeler: "Premium'a bak" / "Okumaya devam et" |
| Defter sınırı | | "Defterin 15 kelimeyle doldu, güzel bir başlangıç. Hepsini saklamak istersen Premium'da yer bol." Düğmeler: "Premium'a bak" / "Tamam" |
| Günün son hikâyesi bitti | İlk gün (iki hikâye) | "Bugünlük iki hikâye, harika gidiyorsun. Sıradaki yarın seni bekliyor." |
| | Sonraki günler (bir hikâye) | "Bugünün hikâyesini okudun, harika gidiyorsun. Sıradaki yarın seni bekliyor." |
| Kilitli içerik | | "Bu hikâye Premium'da. İstersen şimdi açalım." Düğmeler: "Premium'a bak" / "Şimdi değil" |
| Günlük açma kullanılmış (kapak sayfası) | Bugün "Bugünkü hakkını kullandın" + geri sayım | "Bugünün hikâyesini okudun. Yenisi yarın açılır; beklemek istemezsen Premium seni bekliyor." Geri sayım kalkar; düğme "Yarın açılır" |
Rütbe adına gelen ek (Çaylak'a, Meraklı'ya, Okur'a) Türkçe ses uyumuna göre yazılır.

## Sonraki iş
Paul, yayından sonraki iki haftada uygulamadaki bütün metinleri bu kurallarla tarar (yalnız metin değişikliği).
