# Editör görevi: kartta görünmeyen beş Türkçe adın düzeltilmesi

**Veren:** ekip (Tomris, Paul) · **Onay:** Mehmet, 26 Kas 2026 23:19 ("tamam, editöre prompt ver"). **Dayanak:** `raporlar/2026-11-26_kartta_gorunmeyen_adlar.md` (bölüm 4; turlu, bağımsız gözden geçti).
**Neden:** kartlar 28 karakterden uzun Türkçe adı hiç çizmiyor (`BookTitleLines.maxTrChars = 28`). 26 Kasım 17:52'de canlıya yazılan 15 addan beşi sınırı aşıyor ve kartlarda görünmüyor.

## Değişecek (yalnız `SubtitleTR`; `Title` ve `Slug` değişmez)
| Kimlik | İngilizce ad (değişmez) | Türkçe ad: şimdi | Türkçe ad: yeni | Karakter |
|---|---|---|---|---|
| 1023 | Rabbit Island: Missing from the Map | Haritadan Silinen Tavşan Adası | Haritadan Silinen Ada | 21 |
| 1055 | Forty-One Days After the Hurricane | Kasırgadan Sonra Kırk Bir Gün | Kasırgadan Sonra 41 Gün | 23 |
| 1045 | Baba Yaga | Baba Yaga: Tavuk Bacaklı Kulübe | Baba Yaga ve Yürüyen Kulübe | 27 |
| 1063 | The Country That Eats Breakfast Twice | Günde İki Kahvaltı Yapan Ülke | İki Kez Kahvaltı Eden Ülke | 26 |
| 148 | Why Italians Love Talking | İtalyanlar Neden Çok Konuşur? | İtalyanlar Neden Konuşkan? | 26 |

## Yapılacak
1. Canlıda beş satırın şu anki `SubtitleTR` değeri tablodaki "şimdi" sütunuyla birebir aynı mı, oku; değilse dur ve yaz.
2. `RenameFifteenTexts_2026_11_26.sql` ile aynı kalıpta betik ve geri alma betiği; eşleşme adresle; beş satırın beşi bulunmazsa hiçbir şey yazmaz; önceki adlar yedek tabloya.
3. **Canlıya yazma Mehmet'in sözüyle.** Betik hazır olunca Mehmet'e sor; "yap" deyince çalıştır.
4. Yazdıktan sonra: beş satırı canlıdan oku; uygulamada (1.0.4) ana sayfa rafında beş kartın Türkçe adının göründüğünü bir görüntüyle doğrula. Önbellek varsa ne zaman yenilendiğini yaz.
5. Bildirim metinleri Türkçe adı kullandığı için ayrıca bir şey gerekmiyor; web ana sayfasında ya da başka bir yerde eski ad sabit yazılıysa birlikte düzelt.
6. Bundan sonrası için: betik deposuna ya da test takımına "etkin metinlerde `SubtitleTR` 28 karakteri geçemez" denetimi eklenebiliyorsa ekle (arayüz iki satıra geçene kadar); eklenemiyorsa yaz.

## Rapor
`raporlar/2026-11-26_editor_ad_degisiklikleri.md` dosyasına ek bölüm.
