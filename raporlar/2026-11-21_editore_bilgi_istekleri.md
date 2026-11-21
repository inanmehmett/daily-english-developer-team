# Editöre: ekibin bilgi istekleri

**Tarih:** 21 Kasım 2026, 20:35 · **Kimden:** ekip · **Kime:** editör
**Kaynak:** Mehmet (20:30, 20:34): "Bilgiye ihtiyacın varsa editörden iste. Bir rapor yaz repoya, editör oradan okusun."

## Nasıl çalışılır
- Bu dosya tek başına okunur. Hepsi **salt okuma**: kod, canlı veritabanı (yalnız sorgu) ve kayıtlar. Hiçbir şey değişmez, yayınlanmaz.
- **Önce bu sorular, sonra kod.** Sıralı görevin (`ortak/editor_gorevi_2026-11-21_aksam.md`) A bölümüne bunlar cevaplanmadan başlanmaz.
- Cevaplar: `raporlar/2026-11-22_editor_bilgi_cevaplari.md`. Her soru için: kısa cevap, baktığın dosya ya da sorgu, emin olamadığın yer. Bilinmiyorsa "bilinmiyor" yaz; tahmin yazma.
- Bir cevap aşağıdaki "karar değişirse" sütunundaki durumu doğuruyorsa o işe başlama, cevabı gönder ve öbür işlerle devam et. Ekip aynı gün karar verir. Mehmet'e soru sorulmaz.
- Kararların gerekçesi: `raporlar/2026-11-21_aksam_ekip_kararlari.md`.

## Sorular
| # | Soru | Ekip neden soruyor | Karar değişirse |
|---|---|---|---|
| S1 | Mehmet 21 Kasım 00:37'de "Seviyeni belgele doğrudan zor bir boşluk doldurmayla başlıyor" dedi. Mehmet'in hesabında ve test hesaplarında 20–21 Kasım'daki seviye ölçümü kayıtları: hangi test başlatıldı ("Seviyeni belgele" mi, "Seviyeni yeniden ölç" mü), nereden başlatıldı, ilk gösterilen soru neydi? | "Seviyeni belgele"de boşluk doldurma yok; boşluk doldurma yeniden ölçme testinde. T19 ile belgeleme satırını gizliyoruz; Mehmet öbür testi gördüyse yanlış satır gizleniyor | Görülen test yeniden ölçmeyse: T19'u geri alma, dur ve yaz. Ekip iki testten hangisinin gizleneceğine karar verir |
| S2 | Kariyer sayfasında bir rozete (kazanılmış, sıradaki, uzak) dokununca bugün ne oluyor? Rütbe kazanmak kullanıcıya bir şey açıyor mu (içerik, hak, görünüm)? | Halka kalkıyor (Mehmet 20:28); rozetin dokunma davranışı belirsiz kalmasın. "Rütbe ne getirir" penceresi sonraki sürümde düşünülüyor | Rozet bugün bir şey açıyorsa davranış aynı kalır. Açmıyorsa ekleme yapma |
| S3 | Kariyer yolunun, rozetlerin ve alt şeridin bugünkü ekran okuyucu etiketleri (VoiceOver / TalkBack) | Yeni etiket yazılacak: "Meraklı'ya giden yolun yüzde 11'i. Yaklaşık 5 günlük okuma kaldı." | – |
| S4 | Günün quizi sonuç ekranında yanlış bilinen kelimeleri **toplu** deftere ekleyen bir yol kodda var mı? Tek tek ekleme nasıl çalışıyor; ücretsiz kullanıcı defter sınırına (15) çarpınca ne görüyor? | Sonuç ekranının ana düğmesi (Q4) | Toplu ekleme yoksa ana düğme "Sıradaki hikâye" olur; toplu ekleme yazılmaz |
| S5 | Günün quizi için bugün hangi olaylar yazılıyor (giriş, soru, bitiş, skor, yarıda bırakma)? Son 7 günde kaç tur başladı, kaçı bitti? | Q7 ölçümü; "zorlananlar bitirmeden çıkıyor mu" sorusu (Q1 buna bağlı kapatıldı) | Yarıda bırakma A1'de belirgin yüksekse yaz; ekip Q1'i yeniden açar |
| S6 | "Geri dön" bildirimine dokununca uygulama nereye açılıyor (1.0.4 ve 1.0.2)? Sunucu bildirime hikâye kimliği koyuyor mu? Sunucu o kullanıcı için "sıradaki hikâye"yi gönderim anında hesaplayabiliyor mu (yolculuk durağı, yarım kitap)? | Yeni metinler sıradaki hikâyenin adını ve süresini söylüyor; dokunma o hikâyenin kapak sayfasına açılmalı | Sunucu sıradaki hikâyeyi bilemiyorsa yalnız yedek metinler yayınlanır; adlı metinler bekler |
| S7 | Şu 9 metin bir yolculukta, başlangıç paketinde, günlük havuzda ya da bir önerinin içinde mi: 1096, 1098, 1039, 1097, 1103, 1094, 1063, 1089, 1067? Etiket A2'den B1'e geçince hangi kullanıcıların önünden kalkar, hangilerinin önüne çıkar? Yarıda okuyan var mı? | Etiket değişikliğinin yan etkisi (içerik betiği, C-11) | Bir metin A2 yolculuğunun durağıysa ya da yarıda okuyanı varsa o metne dokunma, yaz |
| S8 | Ana sayfada bugün hangi kartlar, hangi koşulla ve hangi sırayla çıkıyor? (Kişi kartı, ilk hafta sayacı, yolculuk kartı, seviye ölçüm kartı, Premium şeridi ve öbürleri.) Üç durum için sırayla: yeni kullanıcı, 3. gün, güncelleyen eski kullanıcı | Giden sadık kullanıcıların dördü ana sayfadan metne girmeden çıktı. Sadeleşme taslağı (D-14) bu dökümden sonra çizilir | Döküm taslaktan **önce** ekibe gelir |
| S9 | Yolculuk sayfasındaki "Yarın hatırlat" düğmesi ve davranışı ana sayfa kartında yeniden kullanılabilir mi, yoksa yeniden mi yazılır? | G2'nin iş büyüklüğü | Yeniden yazmak gerekiyorsa ve derleme 50'yi bir günden fazla geciktirecekse yaz; ekip G2'yi ilk düzeltme sürümüne alır |

## Ekibin önceki raporlarda kullandığı, senden doğrulanması istenen iki sayı
- "A2 metinlerinin 69.091 kelimesinin 46.546'sı altı klasik uyarlamadan geliyor" (ekip betikle saydı; kaynak `veri_2026-11-21/A2_metinleri.md`). Veritabanındaki kelime sayılarıyla tutuyor mu?
- "The Island Where Rabbits Won, A2 kullanıcısının ilk ücretsiz hikâyesi" (93 başlayan). A2 başlangıç paketinin sırası gerçekten bu mu?
