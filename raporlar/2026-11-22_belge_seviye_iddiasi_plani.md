# Belge "B1" yazacak: iddianın arkasını doldurma planı

**Tarih:** 22 Kasım 2026, 22:15 · **Yazan:** Charles (ekip; kurgusal üye) · **Mehmet (22:07):** "B1 yazsın. Gerekli şeyler varsa yapalım."
Karar Mehmet'in: belgede CEFR seviyesi (A1, A2, B1, B2) yazmaya devam eder. Bu rapor, o yazının savunulabilir olması için gerekenleri ve sırasını verir. Çerçeve: Avrupa Konseyi'nin sınavları CEFR'e bağlama kılavuzundaki dört adım (tanıma, betimleme, standart belirleme, doğrulama), küçük bir uygulamanın ölçeğine indirilerek.

## Bugünkü durum (editörün dökümlerinden)
- 176 soru üretimle yazıldı; seviyeleri yazılırken verildi. 29'unun kökü düzeltildi; kalan 147'si insan gözüyle okunmadı.
- Müşteriden henüz tamamlanmış belge denemesi yok; hiçbir soru veriyle sınanmadı.
- Seviye eşikleri (hangi puan hangi seviye) kodda sabit; neye göre seçildiği yazılı değil.
- Belgenin üstünde ve mağaza açıklamasında tam olarak ne yazdığını bilmiyoruz (editöre soruldu, aşağıda).

## Dört adım ve bizdeki karşılığı
| Adım | Ne demek | Bizde yapılacak | Kim | Ne zaman |
|---|---|---|---|---|
| 1. Tanıma ve test tanımı | Her seviyenin okuma tanımı yazılır; test neyi, hangi metinle, hangi soruyla ölçüyor | `ortak/belge_testi_tanimi.md` yazıldı (bu turda): dört seviyenin okuma tanımı, metin ve soru ölçütleri | Charles, Paul | **Bitti** |
| 2. Betimleme (içerik denetimi) | Her metin ve soru tanıma göre okunur | 176 sorunun ve metinlerinin okunması: tek doğru cevap mı, cevap metinden mi çıkıyor, çeldiriciler akla yatkın mı, metin o seviyenin tanımına uyuyor mu. Uymayan soru kapatılır ya da düzeltilir | Charles, Paul | **Sıradaki iş** (tek büyük oturum) |
| 3. Standart belirleme | Hangi soru hangi seviyeyi gerektirir, eşik neden orada | "Sepet yöntemi": iki değerlendirici her soruyu "bunu doğru yapmak için en az hangi seviye gerekir" diye bir sepete koyar; etiketle uyuşmayan sorular yeniden etiketlenir. Eşiklerin gerekçesi tanım dosyasına yazılır | Charles, Paul; kod değişikliği gerekirse editör | 2 ile birlikte |
| 4. Doğrulama | İddia veriyle ve dışarıdan sınanır | (a) Her soru için kolaylık ve ayırt edicilik; 30 cevaptan sonra. (b) İki testin (yeniden ölçme, belge) aynı kişiye verdiği seviyenin örtüşmesi. (c) **Dış göz:** en az bir insan İngilizce öğretmeninin, tercihen CEFR sınavı tecrübesi olan birinin, her seviyeden bir metin ve soru örneğini görmesi | Editör (veri), Nate; (c) için Mehmet'in bulacağı biri | Yayından sonra, veri geldikçe |

## Dürüstlük sınırı (Mehmet'in bilmesi gereken)
1. **Dış göz olmadan zincir eksik kalır.** Soruları yapay zekâ yazdı; denetimi de biz (yine yapay zekâ destekli bir ekip) yapıyoruz. 4c'deki insan öğretmen kontrolü, bizim kendi kendimize kapatamayacağımız tek adımdır. Birkaç saatlik iş: her seviyeden iki metin ve sekiz soru, toplam 32 soru.
2. **"B1" yazmak ile "resmî B1 sertifikası" demek ayrı şeyler.** Belge bir kurumun sınav sonucu değil. Belgede ve mağazada "sertifika", "resmî", "geçerli" gibi sözler varsa değişmeli; yerine "Daily English okuma testi sonucu, CEFR ölçeğine göre: B1" gibi bir ifade. Bu hem kullanıcıyı yanıltmamak hem de mağaza kuralları (yanıltıcı iddia) için gerekli. Editör bugünkü metinleri dökünce Paul yeni metni yazar.
3. **Kısa testin hatası vardır.** Sınırdaki okur bir denemede B1, ötekinde A2 çıkabilir. Belgede seviye tek başına yazar; uygulamadaki sonuç ekranı seviyenin içindeki yeri sözle söyler (derleme 50'de yapıldı).

## Editöre (salt okuma; cevap `raporlar/2026-11-23_editor_belge_iddiasi_cevabi.md`)
| # | İstenen |
|---|---|
| B1 | Belgenin üstündeki bütün yazılar (Türkçe ve İngilizce), paylaşım görselindeki metin, belgeye götüren ekranlardaki vaat cümleleri, mağaza açıklamasında ve sitede seviye ya da sertifika iddiası geçen her cümle |
| B2 | Belge testinde puandan seviyeye giden eşikler ve varsa bunların neye göre seçildiğine dair not (kod yorumu, commit, teslim dosyası) |
| B3 | Belge testinde soru bazında cevap kaydı tutuluyor mu? Tutulmuyorsa eklemenin iş büyüklüğü (doğrulama adımı buna bağlı) |
| B4 | Her metnin kelime sayısı, cümle başına kelime ve soru türlerinin seviyeye göre dökümü (tanım dosyasındaki ölçütlerle karşılaştırmak için) |
Kod değişikliği istenmiyor. 2. ve 3. adımların sonunda kapatılacak ya da düzeltilecek sorular ayrı bir dosyayla gelecek.

## Sıra
1. (Bitti) Test tanımı.
2. (Sıradaki, ekip) 176 sorunun okunması ve sepetlenmesi → düzeltme ve kapatma listesi.
3. (Editör) B1–B4 cevapları; sonra düzeltme listesinin canlıya işlenmesi (yedekli; Mehmet'in sözüyle).
4. (Paul) Belge ve mağaza metinleri.
5. (Mehmet) Dış göz için bir öğretmen; örnek paketini ekip hazırlar.
6. (Yayından sonra) Soru istatistikleri; 30 cevap kuralı.
