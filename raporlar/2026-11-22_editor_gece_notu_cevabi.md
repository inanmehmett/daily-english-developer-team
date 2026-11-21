# Editörden: gece notunun cevabı (ilk bölüm)

**Tarih:** 22 Kasım 2026, 01:45 · **Kimden:** editör · **Kime:** ekip
**Not:** `ortak/editor_notu_2026-11-22_gece.md`
**Bu dosyada:** bölüm 1 (ısınma soruları) ve bölüm 2 (sınav sistemi, H1–H8) tamam. Bölüm 5, 3 ve 4 sırada; hazır oldukça bu dosyaya eklenecek.

## Önce: ekibin karar vermesi gerekenler
| # | Konu | Ne bulundu | Beklenen karar |
|---|---|---|---|
| 1 | **Isınmada B2 yerine A1 sorusu tek başına yetmiyordu** | Isınmadan başlangıç seviyesi **kaç soru bilindiğine** bakıyor, hangilerinin bilindiğine değil: 4 doğru = ilk metin B2. B2 sorusunu A1 ile değiştirince A1–A2 okurun 4 doğru yapması kolaylaşıyor ve ilk metni yine B2'den geliyordu. Bu yüzden bir kural daha ekledim: **başlangıç, ısınmada sorulan en yüksek seviyeyi geçmez** (A1–A2 okurda B1). Tavan değil: metinlerde iyi giden okur yine B2'ye çıkabiliyor (testle kilitli) | Charles: eklediğim kural doğru mu? Yanlışsa PR birleşmeden söyleyin |
| 2 | **Boşluk doldurma, B1 ve B2'de şans düzeyinde** | Müşteri turlarında doğru boşluk oranı: A1 %83, A2 %69, **B1 %42, B2 %33**. Sorular 3 şıklı; rastgele işaretleme %33 verir. B2'de veri az (42 boşluk), B1'de değil (243 boşluk) | Charles: B1 parçaları ayırt ediyor mu, yoksa çok mu zor? Ayrıntı `H4` bölüm 4 |
| 3 | **İki test de seviyeyi düşürebiliyor**, belge testi dahil | "Yalnız yükselt" kuralı yalnız ana sayfa teklifinden başlayan yeniden ölçmede var. Belge almak için giren kullanıcının okuma seviyesi düşebilir | Belge testi seviyeyi düşürmeli mi? |
| 4 | **Seviye değişince yolculuk yeniden atanmıyor** (1.0.4) | Yolculuk ilk açılışta o günkü seviyeye göre atanıyor; sonradan ölçümle seviye değişse de aynı kalıyor. Ana sayfanın ilk kartı yolculuk olacak | Ürün kararı: ne zaman yeniden atansın (yolculuğun ortasındaki kullanıcı?) |
| 5 | **Kelime taraması kelime bazında kaydedilmiyor** | Hangi kelimeye "biliyorum" dendiği tutulmuyor; kelimelerin bantlara doğru yerleşip yerleşmediği sınanamıyor | Eklensin mi? Yarım gün, yalnız sunucu |
| 6 | "Her seviyeye belge" önerisi | **Zaten var:** A1, A2, B1, B2 sonuçlarının hepsine belge veriliyor | Bilgi |
| 7 | Ekip notundaki "seviyesi düşen 4 müşteri" | Kayıtta **12** düşüş var | Bilgi |

## 1. "Seviyeni belgele" ısınma soruları
- **Nerede belirleniyor:** seçim de sıra da **sunucuda** (`AssessmentService.PickRoutingAsync`, `AssessmentRouter.RoutingLevels`). Uygulama soruları geldiği sırayla gösteriyor. **Yeni derleme gerekmiyor.**
- **Sıra:** zaten kolaydan zora (A1, A2, A2, B1, B1, B2). Dokunmadım.
- **Yapılan** (sunucu dalı `fix/assessment-warmup-by-level`, commit `87021a7`):
  - Seviyesi Pre-A1, A1 ya da A2 olan okurda B2 sorusu yerine bir A1 sorusu gelir: A1, A1, A2, A2, B1, B1.
  - Başlangıç seviyesi ısınmada sorulan en yüksek seviyeyi geçmez (yukarıda 1).
  - B1 ve üstü okurda hiçbir şey değişmedi.
- **Testler:** 8 yeni test; tam sunucu turu temiz (1.812 geçti, 0 başarısız).
- **Durum:** dal yerelde, commit'li. Uzak depoya göndermem izin katmanında reddedildi; PR açılamadı. Mehmet dalı gönderince PR'ı açarım; **yayın Mehmet'in sözüyle.**
- **Yapılmayan:** altı sorunun tek sayfada gösterilmesi uygulama işi (H8-b, yarım–1 gün, yeni derleme); bu notta istenmedi.

## 2. Sınav sistemi: Charles için dosyalar
Hepsi `raporlar/veri_2026-11-22/sinav_sistemi/` altında.

| Dosya | İçinde |
|---|---|
| `H1_H2_akis_ve_puanlama.md` | İki testin adım adım akışı, soru seçimi, yarıda çıkma, puanlama ve seviye kararı kuralları, belge koşulu, "yalnız yükselt"; sonunda Charles için beş not |
| `H3_soru_bankalari.md` | Kelime taraması havuzu (60 gerçek + 35 sözde kelime) ve 24 etkin boşluk doldurma parçasının tam dökümü; seviyelerin kim tarafından, neye göre verildiği |
| `H4_gercek_veri.md` | 118 müşteri turu: sonuçlar, süre, yarıda kalma adımı, tarama bandı ile sonuç, önce ve sonra seviye, parça ve boşluk bazında doğruluk |
| `H5_olcumden_sonra.md` | Seviyesi değişenlerin sonraki 7 gündeki okuması |
| `H6_H7_H8.md` | Seviyenin kullanıldığı yerler, silinen geçiş sınavı, beş önerinin kaba maliyeti |
| `../belge_sorulari.md` | (Önceden gönderildi) belge testinin 176 sorusu |

### Öne çıkan olgular
- **Üç değil iki test var.** Onboarding'de ayrı bir yerleştirme yok: kullanıcı seviyesini listeden seçiyor; "emin değilsen ölçelim" bağlantısı yeniden ölçme testini açıyor.
- **Yeniden ölçme:** 118 müşteri turu, 107 kişi; 106 tamamlandı, 11 yarıda (5'i kelime taramasında), 1 okunmadan geçildiği için geçersiz. Ortanca süre 3,2 dakika; 13 tur 2 dakikanın altında.
- **Belge testi:** müşteriden **0** deneme. Soru bazında müşteri verisi yok.
- **Tarama A1 kestirip sonucu B2 çıkan 5 tur var** (üç parçada üst üste 3/3).
- **Seviye değişimi:** 106 kayıtta 66 yükselme, 28 aynı, 12 düşme. Ama 86'sında "önceki seviye" A1: ölçüm onboarding'de seviye seçilmeden yapıldığında profilde varsayılan A1 duruyor; bunlar gerçek yükselme değil, ilk ölçüm.
- **Ölçümden sonra okunan metin seviyeyle pek değişmiyor** (H5). Hipotez: ücretsiz okurun açabildiği metinler az ve sabit.

### Bilinmeyenler
- 100 kelimede dokunma: müşteri sürümünde kelime bakışı metnin kimliğini taşımıyor; ölçülemedi.
- Seviyeleri bir insan uzmanın onaylayıp onaylamadığı: kayıt yok.
- Canlıda eşiklerin ortam değişkeniyle değiştirilip değiştirilmediği: bakmadım; depodaki ayar dosyası kod varsayılanlarıyla aynı.
- Ana sayfa kartından ve profilden başlayan yeniden ölçmeler ayırt edilemiyor (ikisi de aynı işareti gönderiyordu; derleme 50 ile ayrılacak).

## Sırada
Bölüm 5 (S13–S15: hesap hatırlatmaları), bölüm 3 (yolculuk dökümü, S10–S12), bölüm 4 (profil resmi). Henüz başlanmadı.

## Ayrıca (Mehmet'in doğrudan sözü, 01:10)
Kariyer sayfasında yol ile rozetler arasında boşluk vardı ("kopukluk hissi veriyor"). Neden: yol rozetin çevresindeki dairenin dışında bitiyordu, rozet ise altıgen; düz kenarlarda 10–12 pt boşluk kalıyordu. Yol artık geldiği yönde altıgenin görünen kenarına kadar gidiyor ve ucu rozetin altına 4 pt giriyor (`0039a0ac`, `feat/journey-core`). Mehmet'in telefonuna kuruldu; görüşü bekleniyor.
