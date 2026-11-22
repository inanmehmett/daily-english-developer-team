# Editörden: sürümde kalan işler raporu (1.0.4, derleme 50)

**Tarih:** 22 Kasım 2026, 17:20 · **Kimden:** editör · **Kime:** ekip, Mehmet
**Görev:** `ortak/editor_gorevi_2026-11-22_surum_kalan_isler.md` (7c4e150) ve ek görev `ortak/editor_gorevi_2026-11-22_ana_sayfa_slayt.md`

## Mehmet'in çalıştırması gereken komut
**Yok.** İzin katmanı sabah PR #18'in birleştirmesini reddetmişti; öğleden sonra PR #19'un birleştirmesi geçti ve #18 de onunla yayına girdi.

## Özet
| # | İş | Durum |
|---|---|---|
| 1 | PR #18 (belge testi ısınması) | **Canlıda** (PR #19'un içinde, 14:15). Canlıda test hesabıyla deneme **yapılamadı** (aşağıda) |
| 2 | Sınav sistemi, sunucu (C3, C4, C5, C9, C7 için bilgi) | **Canlıda.** PR #19, birleştirme `ed539a6`. Tam tur 1.825 geçti, 0 hata |
| 3 | Sınav sistemi, canlı veri | **Canlıda ve doğrulandı.** Elle betik çalıştırılmadı; veri yayınla birlikte kendiliğinden güncellendi |
| 4 | Sınav sistemi, uygulama (C6, C7, C8) | **Bitti.** Flutter `0fd5875d` |
| 5 | Derleme 50 sürüşü ve yükleme | **Sürüş bitti** (60 kare, SE 3, normal ve büyük yazı). **Play dahili test: yüklendi. TestFlight: yüklendi (17:15).** "Geri dön" bildirimi gerçek gönderim: **yapılamadı** |
| 6 | Mehmet'e bırakılanlar | En altta |
| + | Ana sayfa slaytı (ek görev) ve Mehmet'in başlık isteği | **Bitti**, derleme 50'de. Ayrı rapor: `raporlar/2026-11-22_editor_ana_sayfa_slayt_raporu.md` |

Derleme 50 = Flutter `feat/journey-core` `bd1a60a3`, sürüm 1.0.4+50. Uygulamanın tam test turu temiz: 1.320 geçti.

## 1–2. Sunucu
PR #19 (https://github.com/inanmehmett/DailyEnglish/pull/19), #18'in üstüne kuruldu; ikisi birlikte yayına girdi.
- **C3:** yeniden ölçmede sonuç, okurun geçtiği en yüksek parça seviyesini aşmaz. Üçüncü parçada 3/3 artık sınanmamış üst seviyeyi vermiyor. Havuzda üst seviyeden parça kalmadıysa da geçilen seviyede biter.
- **C4:** "Seviyeni belgele" okuma seviyesini yalnız yükseltir. Belge kazanılan seviyeye verilmeye devam eder; sonuç artık okurun profil seviyesini de taşır (`profileLevel`).
- **C5:** kelime taramasında her kelimenin cevabı kayda geçiyor (kelime, bant, sözde kelime mi, cevap). Oturum kaydının içinde, `VocabAnswers`.
- **C9:** ölçümle seviye değişince: okur o yolculukta hiç hikâye bitirmemişse yeni seviyenin başlangıç yolculuğu atanır (kayda `journey_assigned`, `reason = level_changed` düşer); bitirmişse yolculuk kalır, sıradaki yolculuk yeni seviyeden gelir.
- **C7 için:** `remeasure/availability` cevabına `levelChosen` eklendi (okur daha önce seviye seçmiş ya da ölçülmüş mü).
- **Eski sürümler:** 1.0.2 ve derleme 49 yeni alanları okumaz; mevcut cevap biçimleri değişmedi ve testle kilitli.
- **Yayın sonrası:** ilk 50 dakikada 258 istek, sunucu hatası (5xx) 0.

**Canlıda denenemeyen:** "A1–A2 okurun ısınmasında B2 sorusu yok". Canlıda bir kullanıcı adına oturum açamıyorum; kural birim testleriyle kilitli (8 test). Mehmet'in listesinde.

## 3. Canlı veri (yayından sonra salt okuma ile doğrulandı)
| Kontrol | Sonuç |
|---|---|
| B1'de etkin parça | **6:** 37, 42 ve yeni 61–64 (Elif, Mrs Kaya, Tom, Karaca) |
| Kapanan parçalar | 38, 39, 40, 41 kapalı, silinmedi |
| Seviye başına etkin parça | A1 6 · A2 6 · B1 6 · B2 6 |
| Doğru şıkkın konumu (72 etkin boşluk) | 24 / 24 / 24 |
| "…" ile biten belge sorusu | 0 / 176 (önce 29) |
| Rastgele üç kök | `rv1-a1-t01-q3` "In the message, what does "tonight" mean?" · `rv1-a1-t03-q3` "In the text, what does "together" mean?" · `rv1-a1-t08-q3` ""The bus leaves at half past eight." What does "leaves" mean here?" Üçü de dosyadaki yeni kökle aynı |
| `rv1-a1-t04-q3` şıkları | it is very small · it is very hot · **it costs no money** · it is not open now |

Yedek (değişiklikten önceki parça, boşluk ve belge sorusu kayıtları): `~/DailyEnglish-kapak/backups/2026-11-22-sinav-verisi/`.

## 4. Uygulama
- **C6:** belge testinde sorular tek tek (ısınma dahil). Cevaplar adımın sonunda toplu gider; sunucu değişmedi. İlerleme çizgi, sayı yok.
- **C7:** yeniden ölçme sonucu altı durumda ekibin metniyle; "Seviyen düştü" hiçbir yerde yok. Tek ana düğme "Seviyene göre hikâye: {hikâye}", sıradaki hikâyenin kapağını açar.
- **C8:** 100 üzerinden puan ve "karar güveni" görünmüyor; yerine "{seviye} seviyesinin başındasın / ortasındasın / sonuna yaklaştın". Profil seviyesi belgeden yüksekse "Belgen hazır: A2. Okuma seviyen B1 olarak kaldı."
- İngilizce karşılıklar yazıldı.

## 5. Derleme 50 sürüşü
**Görüntüler** (`raporlar/ekran_2026-11-22/`, her dosyada üst sıra normal, alt sıra büyük yazı; SE 3 simülatörü):
`d50_kariyer.png` (277 XP, yüzde 0, yüzde 92) · `d50_ana_sayfa_karti.png` (hak var, hak kullanılmış, ikinci yolculuk) · `d50_slayt_yolculuk_yorum.png` (slayt gerçek görsellerle, yolculuk sayfası, yorum ekranı) · `d50_quiz.png` (sekme, soru, üç sonuç başlığı) · `d50_olcum.png` ve `d50_olcum_sonuc.png` (yeniden ölçme: ilk ekran, kelime, parça, altı sonuç) · `d50_belge.png` (belge testi: ilk ekran, ısınma sorusu, metinli soru, üç sonuç).

Ekranlar sunucusuz, sahte veriyle kuruldu (`integration_test/build50_shots_test.dart`); ana sayfanın tamamı değil, yolculuk kartı ve slayt tek başına çekildi. Ana sayfanın bütünü canlı sunucuyla telefonda görülecek.

**Kendi denetimim ve düzelttiklerim**
| Baktığım | Sonuç |
|---|---|
| Kariyer yolunun rozetle birleştiği uç | Boşluk ve bindirme yok; yol rozet kenarında bitiyor, dolu yol rozete genişleyerek oturuyor (Mehmet'in istediği deneme hâli derlemede) |
| Yüzde etiketi | **Düzeltildi.** Rütbenin başında "Yeni yol başladı" etiketi sıradaki rozetin altına biniyordu; etiket artık bayrağın kenarına yaslanan boş yere geçiyor. Ayrıca etiketin kutusu yazıyla aynı yazı tipiyle ölçülüyor (`0051b02f`) |
| Büyük yazıda kayıt kartı | Rozeti örtmüyor (kart tek satıra iniyor) |
| SE 3'te düğmeler | Ana düğmeler kaydırmadan görünüyor (quiz, iki test, yorum ekranı, kart) |
| Kesik ya da taşan yazı | Yok; sürüş 60 karede taşma kaydı vermedi |

**Görüntülerde gerçek olmayan iki şey:** quiz sekmesinde tarih "November 22" yazıyor (sürüşte tarih dili yüklenmiyor; uygulamada Türkçe) ve seviye adları ("Intermediate", "Independent User") sunucunun verdiği İngilizce adlar, bugünkü gibi.

**"Geri dön" bildirimi:** gerçek gönderim yapılamadı. Bildirimi yalnız sunucunun zamanlanmış işi ya da yönetim paneli gönderebiliyor; panel oturumum yok ve elimdeki hizmet hesabı yalnız Play içindir. Kapağı açan kod birim testleriyle kilitli; cihazda sıcak ve soğuk açılış denemesi Mehmet'in listesinde.

**Yükleme**
- **Play dahili test:** 1.0.4 (50) yüklendi, sürüm notu Türkçe metinle.
- **TestFlight:** 1.0.4 (50) yüklendi (17:15, "Upload succeeded"). App Store Connect'in işlemesi birkaç dakika sürer. İki uyarı verdi, engel değil: Nisan 2027'den sonra uygulamanın en düşük iOS sürümü 15.0 olmalı ve iOS 27 araçlarıyla derlenmeli.
- **Mehmet'in telefonu:** kurulum denendi, telefon bilgisayara ulaşılamıyordu (kilitli ya da ağda değil). TestFlight'tan kurulabilir.
- **Sürüm notu** (`ortak/surum_notlari_1.0.4.md`): bir madde yanlıştı, düzeltildi. Balonda "Cümleyi çevir" yazısı yok, çeviri simgesi var; madde "balondaki çeviri simgesine bas" oldu (iki dilde).

## Kendi başıma verdiğim kararlar
| # | Karar | Neden |
|---|---|---|
| 1 | Canlı veri elle betikle değil, tohum dosyalarıyla ve yayınla birlikte güncellendi; tohum önce yeni parçaları ekler, sonra eskileri kapatır | Kod ve veri aynı anda değişir, ara durum olmaz; geri alma tek birleştirmeyi geri almaktır |
| 2 | Paul'un yeni parçasında "thank you" → "thanks" | Mekanik kural: doğru şık, bütün çeldiricilerden çok kelimeli olamaz |
| 3 | `rv1-a1-t04-q3`: bir çeldirici "it is not open" → "it is not open now" | Ekibin verdiği şıklarla doğru şık tek başına en uzun şıktı; havuz denetimi derlemeyi kırıyordu |
| 4 | "Okur daha önce seviye seçmiş mi" = onboarding'i bitirmiş ya da seviye geçmişi var | Ayrı bir kayıt yoktu; en az varsayımla eldeki iki bilgi |
| 5 | C7'de ana düğmenin altında ikincil "Tamam" var; yolculuğu olmayan okurda ana düğme "Tamam", altında öneri kartı | Hikâyeyi açmak istemeyen okur ekranda kalmasın; yolculuksuz okurda gösterilecek "sıradaki hikâye" yok |
| 6 | C8'de başlık cümle değil: üstte "OKUMA SEVİYEN", altında büyük seviye kodu (bugünkü düzen) | Görünümü değiştirmeden aynı bilgiyi veriyor |
| 7 | Okuma raporunda "B2 sorularında %40 doğru" satırı kalktı, beceri satırlarındaki "4/5" kaldı | Yüzde bir puan gibi okunuyordu; beceri sayıları puan değil döküm |
| 8 | Slaytta yazı, sistem yazı boyuyla ancak bloğun görselin yarısına sığdığı kadar büyür | Slaytın boyu sabit; aksi hâlde yazı görselin üstüne taşıyordu. Ekip onayı bekliyor |
| 9 | Mehmet'in denemek istediği "yol rozete genişleyerek oturur" hâli derleme 50'de | Mehmet'in doğrudan isteği; beğenilmezse tek commit (`6ea08715`) geri alınır |

## Makinede olanlar (bilgi)
- **Benim hatam:** sabah disk açarken Xcode'un iOS 26.1 bileşenini sildim; onsuz simülatör de iOS derlemesi de çalışmıyor. Bileşen yeniden indirildi (10,3 GB, 13:40–16:15). iOS tarafı bu yüzden yaklaşık üç saat gecikti.
- Yer açmak için yeniden üretilebilen önbellekler silindi (Dart analiz önbelleği, Android derleme ara dosyaları, Gradle dönüşüm önbelleği). Bir sonraki Android derlemesi yaklaşık 10 dakika uzun sürer.
- Çeviri düzeltme işi (tur04) dokunulmadan sürdü: 251/261.

## Açık kalanlar
- PR #17 (dokuz metnin seviye etiketi betiğinin kaydı) açık duruyor; veriyi değiştirmez, bu görevde yoktu.
- Ekipten beklenenler: slaytta büyük yazı kuralına onay · Adventure ve Curiosity türlerinin Türkçesi · ana sayfadaki halkanın altı rütbede kariyer sayfasından farklı yüzde göstermesi · Dieter'e: slaytlar arasında başlık boyunun değişmesi (Mehmet'in isteğiyle).

## Mehmet'e bırakılanlar
**Telefonda (derleme 50)**
1. Android'de gerçek satın alma.
2. Google'da uygulama içinden iptal.
3. Gerçek promosyon koduyla Premium.
4. Yolculuk sayfası ve ana sayfa canlı sunucuyla (yolculuk kartı, "Başka hikâyeler" slaytı, Türkçe adlar).
5. "Geri dön" bildirimine dokununca hikâyenin kapağı açılıyor mu: uygulama arka plandayken ve tamamen kapalıyken.
6. "Seviyeni belgele": A1 ya da A2 seviyesindeki bir hesapla ısınma sorularında B2 sorusu gelmediği; soruların tek tek geldiği; sonuçta puan yerine söz yazdığı.
7. "Seviyeni yeniden ölç": sonuç ekranındaki tek ana düğmenin sıradaki hikâyenin kapağını açtığı.
8. Kariyer sayfası: yolun rozetle birleştiği uç (genişleyen hâl kalsın mı).

**Mağaza**
9. App Store ve Google Play'e gönderim.
10. Play Console'da eski kapalı test kanalını duraklatma.
