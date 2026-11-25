# Bildirimlere dönüş oranı ve derlemesiz yorum isteme

**Tarih:** 25 Kasım 2026, 17:35 · Tek geçiş; üyeler kurgusaldır (Nate, Sean, Don, Nassim).
**Mehmet (17:17):** "App Store ve Play Store için kullanıcılardan yorum isteyelim. Derlemesiz, uygulama içinden isteyebilir miyiz? Bir de bildirimlere geri dönüş oranı nedir, onu incele."

## 1. Bildirimlere dönüş
**Kaynak:** editörün canlı veri dökümü, `raporlar/2026-11-21_kanal_ve_bildirim_verisi.md` bölüm 2 (lansmandan 21 Kasım'a: 317 müşteriye 1.376 gönderim). **22 Kasım'daki değişikliklerden (7 bildirim sınırı, yeni "geri dön" metinleri) önceki dönem;** sonrası editörden istendi.

| Tür | Gönderim | Dokunma | Dokunma oranı | 24 saat içinde uygulamayı açan |
|---|---|---|---|---|
| Seri hatırlatma (3+ gün serisi olana) | 30 | 5 | **%16,7** | 13/26 (%50) |
| Seri başlat (1–2 gün serisi olana) | 209 | 8 | %3,8 | 41/188 (%22) |
| Günün quizi | 250 | 9 | %3,6 | 37/225 (%16) |
| Günlük hatırlatma | 90 | 2 | %2,2 | 10/73 (%14) |
| İlk okumaya çağrı | 186 | 3 | %1,6 | 11/162 (%7) |
| Kelime tekrarı | 261 | 3 | %1,1 | 25/224 (%11) |
| Günlük açılan metin (12 Kas'ta kapatıldı) | 154 | 1 | %0,6 | 15/154 (%10) |
| Geri dön | 185 | 1 | **%0,5** | 2/155 (%1) |
| **Toplam** | **1.376** | **32** | **%2,3** | 157/1.218 (%13) |
Dokunan kişi: 18 (bildirim alan 317 kişinin %6'sı).

**Okuma (Nate):**
1. **Genel dönüş düşük: 43 bildirimde bir dokunma.** Dokunmaların tamamı 18 kişiden geliyor.
2. **Bildirim, zaten gelen kullanıcıda işe yarıyor.** Serisi olan kullanıcıya giden hatırlatma altıda bir dokunuluyor; uygulamayı bırakmışa giden "geri dön" iki yüzde bir. Bildirim alışkanlığı korur, gideni geri getirmez (dokuz tür, tek dönem; hipotezden güçlü ama ders değil).
3. **En çok gönderilen tür en az işe yarayanlardan:** kelime tekrarı 261 gönderimle birinci, dokunma %1,1. Üstelik 3 gün ara kuralı çalışmıyor: 182 tekrarın 122'si 3 günden önce gitmiş; 34 kişi dört ve daha çok kez almış (araya başka tür girince sayaç sıfırlanıyor).
4. **İlk bildirimi 3 günden eski 207 müşterinin 136'sı (%66) uygulamayı bir daha hiç açmadı.** Bildirimlerin çoğu çoktan gitmiş kişiye gidiyor.
5. **Bildirimi uygulamadan kapatan müşteri yok;** yani rahatsızlık ölçülebilir bir kapatmaya dönmedi (telefon ayarından kapatanlar görülemiyor).

**Ölçümün sınırları:** dokunma eksik sayılıyor (uygulama açıkken gelen bildirime dokunma ve hemen kapatılan uygulamadaki dokunma kaydedilmiyor). "24 saat içinde açan" bildirimin etkisi değildir; o gün zaten açacak olanı da sayar. Karşılaştırma grubu yok.

**Yapılanlar (22 Kas, canlıda):** bırakan kullanıcıya en çok 7 bildirim; "geri dön" metinleri sıradaki hikâyenin adıyla; 1.0.4'te bildirim hikâyenin kapağını açıyor.
**Öneriler (ekip):**
| # | Öneri | Tür | Ölçü |
|---|---|---|---|
| 1 | Kelime tekrarında 3 gün arası, araya başka tür girse de tutulsun | Sunucu, küçük; derleme yok | Kişi başına kelime tekrarı sayısı; dokunma oranı |
| 2 | "İlk okumaya çağrı" 1. gün metni her zaman hikâyenin adını taşısın (bugün iki biçimden biri adlı) | Sunucu, metin | Dokunma %1,6'dan yukarı |
| 3 | 22 Kasım sonrası "geri dön" sonuçları ayrı okunsun; iki hafta sonra hâlâ %1'in altındaysa 14. ve 30. gün bildirimleri kapatılsın | Veri, sonra karar | Dokunma oranı |
| 4 | Serisi olana giden hatırlatma korunur; bildirimlerin hedefi geri getirmek değil, ilk haftada alışkanlığı tutmak diye yeniden yazılır | Karar | 2–7. gün dönüşü |
| 5 | Karşılaştırma grubu: koşula giren kullanıcıların onda birine o tür gönderilmez, fark ölçülür | Sunucu; sayı küçük olduğu için **şimdi değil** (Nassim) | – |

## 2. Yorum isteme: derlemesiz olur mu
**Kısa cevap:** uygulamanın içinden, mağazanın yıldız penceresiyle istemek için o pencereyi çağıran kodun uygulamada bulunması gerekir. Bugün var mı bilmiyoruz; editöre soruldu (A6). Yoksa yeni derleme gerekir; iş küçüktür.
**Kural (Apple, doğrulandı):** yorum istemek için Apple'ın kendi penceresi kullanılmalı; özel yorum isteme pencereleri yasak (App Review Guidelines 5.6.1; [MacRumors özeti](https://www.macrumors.com/2020/03/04/apple-shares-updated-app-store-guidelines/), [9to5Mac](https://9to5mac.com/2017/06/09/app-rating-custom-prompts-app-store-banned/)). Yani sunucudan açılan kendi kartımızla "bize yıldız ver" demek iOS'ta riskli.

**Derlemesiz seçenekler:**
| Yol | Yapılabilir mi | Değerlendirme |
|---|---|---|
| Profildeki "mağazada değerlendir" girişi | Zaten var | Kimse görmüyor; yerini değiştirmek derleme ister |
| Bildirimle istemek | Teknik olarak evet (bildirim uygulamayı açar, mağazayı açıp açamadığı bilinmiyor) | **Önerilmez.** Dönüş %2 dolayında; "yorum yaz" bildirimi bildirim hakkını harcar ve özel yorum isteme sayılabilir |
| Sunucudan açılan uygulama içi kart | Böyle bir altyapı var mı bilinmiyor (editöre soruldu) | iOS'ta özel istem sayılır; Android'de de kendi kartımız yerine Play'in penceresi doğru yol |
| **@gunluk_ingilizce'den istemek** (hikâye ya da gönderi: "Uygulamayı kullanıyorsan mağazada yorumun bize çok yardımcı olur" + mağaza bağlantısı) | **Evet, bugün** | Uygulama dışı olduğu için mağaza kuralına takılmaz. Ödül, çekiliş ya da "5 yıldız ver" istenmez (iki mağazada da yasak). Instagram ekibinin işi; iki depoya da yazılır |
| Var olan yorumlara cevap | Evet, bugün | Yorum yazanı ve okuyanı etkiler; Tony taslak yazar |

**Derlemeli doğru çözüm (sonraki derleme, küçük iş):** mağazanın uygulama içi değerlendirme penceresi, kullanıcının bir şeyi başardığı anda (üçüncü hikâyenin bitişi ya da yolculuğun tamamlanması), kişi başına bir kez. Pencerenin ne sıklıkta gösterileceğini mağaza kendisi sınırlar; her çağrıda görünmeyebilir. Ölçü: çağrı sayısı, mağazadaki yorum sayısı ve puan (bugün Play'de 4,75; yorum sayıları bu turda okunmadı).

**Ekibin kararı:** (1) Instagram'dan istemek için metni Instagram ekibi hazırlar, Mehmet onaylar. (2) Uygulama içi pencere sonraki derlemenin işi; editörün A6 cevabına göre kodda zaten varsa yalnız tetikleyen an değişir. (3) Bildirimle yorum istenmez.

## İtirazlar
| Kim | İtiraz | Sonuç |
|---|---|---|
| Nassim | Tutunma %6 iken yorum istemek, memnun olmayan kullanıcıdan da yorum getirir; puan düşebilir | **Kabul, kısmen.** Bu yüzden istek başarı anına bağlanıyor ve Instagram'da "kullanıyorsan" diye soruluyor; yine de risk var, kayda geçti |
| Nassim | Bildirim tablosundaki "24 saat içinde açan" sütunu etki gibi okunmasın | **Kabul.** Raporda uyarı var; kararlar dokunma oranına dayanıyor |
| Sean | Yorum sayısı az kaldıkça mağaza dönüşümü (%6,97) sınırlı kalır; bu iş beklemesin | **Kabul.** Instagram yolu bugün başlar |
