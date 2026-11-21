# Editör durum raporu

**Tarih:** 21 Kasım 2026, 11:45 · **Hazırlayan:** editör · Önceki: `2026-11-20_editor_durum_raporu.md` (Ek 4: derleme 49)

## Özet

- **Mağazalarda değişen bir şey yok.** Derleme 49 TestFlight'ta ve Play dahili testte duruyor; üretime ya da incelemeye bir şey gönderilmedi.
- **Derleme 50 için yedi iş dalda hazır;** Mehmet "çıkar" deyince derlenecek.
- **Sunucuda bildirim düzeltmeleri PR #15'te hazır;** Mehmet "yayınla" deyince canlıya girer. Ekibin "1.0.4 çıkmadan düzen değişmez" kararıyla çelişiyor; Mehmet'in doğrudan sözüyle yapıldı.
- **Canlıya tek yazma:** "come here" kalıbı sözlüğe eklendi.
- **Üç veri görevi bitti** (aşağıda bağlantılar).
- **Çeviri işi (tur04) 195/261;** gece kullanım sınırına takıldı, sabah makine yeniden başlayınca durdu, 11:35'te yeniden başlattım.

## 1. Derleme 50'yi bekleyenler (uygulama, `feat/journey-core`)

| İş | Commit | Ne değişti |
|---|---|---|
| Seslendirme, devamda geri sarma | `a9249148` | 300 ms yerine 150 ms geriye bakıyor; cümle sonundaki sessizlikte bitmiş kelimeyi tekrar okumuyor |
| T15 iptal penceresi | `3e6fd9b9` | Tarih "19 Kas 2027", düğme yazısı tek satır, başlık "Üyeliği iptal et" |
| T17 balondaki çeviri simgesi | `3e6fd9b9` | Çeviriyi sessiz açıyor; basılı tutma seslendiriyor |
| T18 Quiz sekmesi rozeti | `3e6fd9b9` | Oturum yüklenince yeniden hesaplanıyor |
| T19 "Seviyeni belgele" | `3e6fd9b9` | Satır gizli (tek anahtar; değerlendirme sayfası ve sunucu ucu yerinde) |
| Bildirime dokunma ölçümü | `7273ca60` | Uygulama açıkken gelen şeride dokunma ve telefonun kendi kurduğu hatırlatmaya dokunma artık ölçülüyor |
| Bildirim ayarını kaydetme | `7273ca60` | Sunucuya yazılamazsa bir kez yeniden deniyor ve "kaydedildi" demiyor |

Uygulama testleri: 1.223 geçti.

**Eksikler, olduğu gibi:**
- T15 ve T17'yi ekranda görmedim; görüntüleri derleme 50 sürüşünde alınacak.
- T18'de kesin neden kanıtlanmadı. En olası neden düzeltildi (rozet açılışta bir kez hesaplanıyor, oturum o an yüklenmemişse sönük kalıyordu). İkinci olasılık düzeltilmedi: uygulama gece yarısı açıkken gün değişirse rozet, uygulama arka plana gidip gelene kadar güncellenmiyor.
- Seslendirme ayarını kulakla deneyemedim; Mehmet'in telefonuna kuruldu, geri bildirim bekliyor.
- Yeni görünen tek metin: "Ayarlar telefonda kaydedildi ama sunucuya ulaşılamadı. Biraz sonra yeniden kaydet." (ayar sunucuya yazılamazsa çıkan uyarı). Paul bakarsa iyi olur.

## 2. Sunucu: PR #15 (yayınlanmadı)

| Ölçülen sorun | Değişiklik |
|---|---|
| Bildirim ayarını kaydetme 500 (7 müşteri, onboarding sonunda) | Çakışmada taze satırla yeniden deniyor; bildirim adresi kaydı da aynı |
| Kelime tekrarının 3 günlük arası çalışmıyordu | Ara gönderim kaydından okunuyor |
| Bırakmış kişiye üst üste bildirim (72 kişi 5 gün ve üstü) | Üst üste 3 bildirim cevapsız kalırsa yenisi gitmez; kullanıcı uygulamayı açınca sıfırlanır. Deneme bitiş uyarısı hariç |
| Gönderimlerin %9'u 22:05'te | Kullanıcının seçmediği saatte en geç 21:05. Kendi seçtiği saat (22:00 dahil) geçerli |
| Başarısız gönderim kaydedilmiyordu | Yeni tablo (hata kodu, tür, adres silindi mi); yayında kendiliğinden kurulur |

- **Günün quizi her gün gitmeye devam ediyor** (Mehmet: "günlük seri o"). İlk yazdığım iki günlük ara çıkarıldı. Uygulamayı açmayan kişide 3 cevapsız bildirim sınırı onu da durdurur.
- **Sayılar editörün seçimi:** 3 bildirim, 21:05. İkisi de tek sabit.
- **Dokunulmadı:** bildirim metinleri (Paul yazacak), günde 1 sınırı, öncelik sırası.
- **Test:** tam koşuda 1.757 geçti, yeni tabloyla ilgili 2 koruma testi düştü; düzeltildi. Ardından yalnız bildirim ve hesap silme testleri koşuldu (139 geçti). Düzeltmeden sonra tam koşu tekrarlanmadı.
- Önce PR #15 yayınlanırsa iyi olur: derleme 50'deki "ayar kaydedilemedi" uyarısının asıl nedeni sunucuda, onunla düzeliyor.

## 3. Canlıya yazılan

- **"come here → buraya gelmek"** kalıp sözlüğüne eklendi (Mehmet'in sözüyle). Tür: fiilli sabit birliktelik ("fall asleep", "take place" gibi); phrasal verb quizine girmez. Yerelde denendi; canlıda satır okunarak doğrulandı. Canlı balonu uçtan uca deneyemedim (canlıda deneme hesabı açmak gerekiyor, izin verilmedi).

## 4. Veri raporları

| Rapor | İçinde |
|---|---|
| `2026-11-20_ilerleme_verisi.md` | Dört sayı, dağılım, rütbe eşikleri, seviye altyapısı |
| `2026-11-21_kanal_ve_bildirim_verisi.md` | Satışlar, geliş kaynağı (Android'de Instagram %62), 17 Kasım sıçraması, bildirim türleri, metinler, sıklık, saatler |
| `2026-11-21_seviye_quiz_guncelleme_verisi.md` | A1–A2 metinleri ve metin başına veri, iki seviye testi, günün quizi, sürüm dağılımı, güncelleme ayarı |
| `veri_2026-11-21/` | A1 ve A2 metin dökümü (84 metin), metin başına tablo, soru örnekleri |

Yapılmayan: iki seviye testinin SE 3 ekran görüntüleri (akışlar metinle anlatıldı; sıradaki sürüşe eklenecek).

Önceki raporlarımdaki iki yanlışı bu raporlarda düzelttim: "dokunma kaydı türü taşımıyor" (taşıyor, birebir eşleşiyor) ve "geliş kaynağı tutulmuyor" (Android'de tutuluyor).

## 5. Çeviri işi (Premium metinlerde elle düzeltme, tur04)

- **195 / 261 parça hazır;** 66 parça kaldı.
- Gece 01:34'ten sonra kullanım sınırına takıldı (sınır bu oturumla ortak; gece boyu süren derleme ve rapor işi sınırı yedi). İşçiler bekleme döngüsündeyken makine sabah yeniden başladı ve hepsi kapandı.
- 11:35'te yeniden başlattım; dört işçi çalışıyor, biten parçaları atlıyor.
- Tahmin: saatte 2–4 parçayla 17–33 saat; 22 Kasım içinde biter. Bu oturumda ağır iş olursa uzar.
- Bitince sıra: doğrulama → kabul → SQL → yerelde kontrol → canlıya yazmadan önce Mehmet'e soru.

## 6. Başlanmayanlar

- Ekibin 21 Kasım'da eklediği iki görev: sadık kullanıcıların son oturumu; ad ve açıklama dökümü. Mehmet henüz istemedi.
- Ana sayfa kartının gövdesinden yolculuk sayfasına giriş (Mehmet'in sorusu; öneri iş listesinde, karar bekliyor).

## 7. Mehmet'ten beklenenler

1. "PR 15'i yayınla" (sunucu).
2. "Derleme 50'yi çıkar" (uygulama).
3. Telefonda bakılacaklar: seslendirme devamı (geri sarma yeterince kısaldı mı), "come here" balonu.
4. "Seviyeni belgele"de gördüğü zor sorunun ekran görüntüsü: o testte boşluk doldurma yok; boşluk doldurma "Seviyeni yeniden ölç"te. Hangisi olduğu netleşmeli.
