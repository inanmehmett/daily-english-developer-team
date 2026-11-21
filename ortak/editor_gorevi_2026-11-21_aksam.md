# Editör görevi – 21 Kasım akşam (sıralı)

**Kaynak:** Mehmet (21 Kas 20:16): "Bu işlerin hepsi hemen sırayla yapılsın." Ekip kararları ve gerekçeler: `raporlar/2026-11-21_aksam_ekip_kararlari.md` (bölüm numaraları aşağıda).
**Kural:** sırayla. Her işte önce koda bakılır; kararda yazan şey kodda zaten varsa ya da kodla çelişiyorsa yazılmaz, raporlanır. Kullanım sınırına takılırsan sıra bozulmaz; kaldığın yerden devam edersin. Çeviri işçileri 22 Kasım 04:30'da kendiliğinden başlıyor; bu görev bitmediyse işçileri bu görev bitene kadar ertele.
**Onaylar:** Mehmet'in 20:16 sözü **derleme 50 için "çıkar" sözüdür.** Sunucu PR'ı ve içerik betiği için de bu söz geçerli: tam test temiz geçerse yayınla, betiği yedek alıp çalıştır. Bir şey ters giderse dur ve raporla.

## 0. Önce: ekibin bilgi istekleri (salt okuma, kısa)
Mehmet (20:30): "Bilgiye ihtiyacın varsa editörden iste." Ekip bu soruları Mehmet'e değil sana soruyor. Cevapları raporun en başına koy. Bir cevap bir kararı değiştiriyorsa o işe başlamadan yaz ve dur; ekip aynı gün karar verir.
| # | Soru | Neden |
|---|---|---|
| S1 | Mehmet'in "zor boşluk doldurmayla başlıyor" dediği test hangisi? Mehmet'in hesabının (ve test hesaplarının) 20–21 Kasım'daki seviye ölçümü kayıtları: hangi test başlatıldı, ilk soru neydi | "Seviyeni belgele"de boşluk doldurma yok. Mehmet yeniden ölçmeyi gördüyse yanlış satırı gizliyoruz (T19) |
| S2 | Kariyer sayfasında rozete dokununca bugün ne oluyor? Rütbe kazanmak bir şey açıyor mu? | D6 ve sonraki sürümdeki "rütbe ne getirir" penceresi |
| S3 | Kariyer yolunun ve rozetlerin bugünkü ekran okuyucu etiketleri | D7 |
| S4 | Günün quizi sonucunda yanlış kelimeleri toplu olarak deftere ekleyen bir yol var mı? | Q4'ün ana düğmesi |
| S5 | Günün quizi için bugün hangi olaylar yazılıyor? | Q7 |
| S6 | "Geri dön" bildirimine dokununca uygulama nereye açılıyor (1.0.4 ve 1.0.2)? Sunucu bildirime hikâye kimliği koyuyor mu? | Bölüm 2: dokunma kapak sayfasına açılmalı |
| S7 | 9 metin (C-11 listesi) bir yolculukta, başlangıç paketinde ya da günlük havuzda mı? B1'e geçince kimin önünden kalkar, kimin önüne çıkar? | Etiket değişikliğinin yan etkisi |
| S8 | Ana sayfada bugün hangi kartlar hangi koşulla çıkıyor (ilk hafta sayacı, kişi kartı, yolculuk kartı, seviye kartı ve öbürleri), sırayla | Sadeleşme taslağı (D-14); bu döküm taslaktan önce ekibe gelir |
| S9 | Ana sayfa yolculuk kartı ve "Yarın hatırlat" için var olan bileşen yolculuk sayfasındakiyle aynı mı, yeniden kullanılabilir mi? | G2 iş büyüklüğü |

## A. Uygulama → derleme 50 (`feat/journey-core`)
1. **Ana sayfa kartının gövdesi** yolculuk sayfasını açar; düğme olduğu gibi kalır. Kaynak `home_card_body` (karar 1b-G1).
2. **Hak kullanılmışken ana sayfa kartında "Yarın hatırlat"**: Premium düğmesinin altında, yolculuk sayfasındakiyle aynı biçimde ve aynı davranışla (1b-G2).
3. **Hiç hikâye okunmamış yolculukta sayı yok**: "Senin yolculuğun · {yolculuğun adı}". İlk hikâyeden sonra "n/toplam". Başlangıç yolculuğu değişmez (1b-G3).
4. **Yorum ekranı (T3)**: commit'siz taslak koda alınır. SE 3'te ilk yorumun tamamı ve "Devam" kaydırmadan görünür (1d).
5. **Günün quizi, uygulama tarafı** (bölüm 3): Q2 şık süzgeci (en az 3 harf, aynı tür; kısa karşılıklı kelime çeldirici olmaz; gösterilen şıklar olaya yazılır) · Q3 sonuç metinleri · Q4 ana düğme (toplu ekleme kodda yoksa "Sıradaki hikâye") · Q6 sekmenin ilk ekranı · Q7 olaylar (`daily_quiz_started`, `daily_quiz_completed`, `daily_quiz_abandoned`; var olanları önce dök).
6. **"Seviyeni yeniden ölç" ana sayfa kartından başlatılınca** uygulama "yalnız yükselt" işaretini gönderir (bölüm 5).
7. **Kariyer E1** (bölüm 1a): `mockup/career-readability`'deki E1 ana dala alınır. E2 ve anahtar kaldırılır, metinler çeviri dosyasına girer. Ayrıca K1 büyük yazıda tek satır kayıt kartı, rozeti hiç örtmez (testle) · K2 × düğmesi 44 pt · K3 bayrak rozete 24 pt'den yakın değil · K4 rozetsiz ad çizilmez.
   **Mehmet (20:28) ve Dieter–Don (bölüm 1a-2):** kapı ve eşik işareti yok · sıradaki rozetin çevresindeki halka kalkar · bayrak dolumun ucunda yüzdeyi taşır ("%11"); %0'da "Yeni yol başladı" (D3) · alt şeritteki ilerleme çubuğu kalkar, yalnız cümle kalır (D1) · yüzde etiketi rozete ve ada binmez (D2), en az 13 pt kalın, büyük yazıda 17 pt (D4) · açılışta yalnız XP değiştiyse dolum bir kez 0,6 sn'de dolar, "hareketi azalt"ta yok (D5) · rozet dokunma davranışını ve ekran okuyucu etiketini önce koddan dök (D6, D7). **Derleme 50'den önce** E1'in bu hâlinin SE 3 + büyük yazı görüntüleri (277 XP, %0 ve %92 durumlarıyla) ekibe gelir.
8. **Derleme 50 sürüşü:** SE 3 + büyük yazı. Kariyer, ana sayfa (hak var / hak kullanılmış / ikinci yolculuk), yolculuk sayfası, yorum ekranı, günün quizi (sekme, soru, sonuç). Görüntüler `raporlar/ekran_2026-11-22/` içine. **Görüntüler önce ekibe gider** (Dieter, Don); ekip temiz derse TestFlight ve Play dahili test. Sonra Mehmet'in 10. adımı.

## B. Sunucu → tek PR (yayın: tam test temizse)
9. **"Geri dön" metinleri** (bölüm 2 tablosu, yedek metinler dahil). Dokunma, sıradaki hikâyenin kapak sayfasına açılsın (1.0.4'te). Kodda yoksa ekle; 1.0.2'de ana sayfa.
10. **Günün quizi sunucu tarafı:** "ile başlıyor" kabulü kalkar, tam eşleşme (Q2). Haftalık Şampiyon: hafta kapanınca tek kişiye; şart en az 10 katılımcı ve 300 XP (Q5).

## C. İçerik betiği (canlıya yazma; yedekle)
11. **Seviye etiketleri** (bölüm 4): A2 → B1: Wizard of Oz (1096), Wind in the Willows (1098), Alice (1039), Secret Garden (1097), Jungle Book (1103), Anne of Green Gables (1094), The Country That Eats Breakfast Twice (1063), The Train with No Driver (1089), The See-Through Umbrella (1067). Önce: bu metinler başka bir yolculukta ya da başlangıç paketinde mi? Öyleyse dokunma, raporla.
12. **The Island Where Rabbits Won (1023)** gövdesi bölüm 4'teki A2 yazımıyla değişir. Bölüm başlıkları yeni adlarıyla. Çeviri, sözlük eşleşmesi ve kelime sayısı yenilenir. Eski gövde yedekte kalır (karşılaştırma için).

## D. Veri ve taslak (salt okuma)
13. "Seviyeni belgele"nin **176 sorusunun tam dökümü:** `raporlar/veri_2026-11-22/belge_sorulari.md`, doğru şık işaretli. Ayrıca iki seviye testinin ilk ekranlarının SE 3 görüntüleri.
14. **Ana sayfa sadeleşme taslağı** (1c): önce ana sayfada bugün hangi kartların, hangi koşulla çıktığının koddan dökümü. Sonra A ve B, ayrı dalda, gerçek ekranda, aynı kullanıcı durumlarıyla (yeni kullanıcı, 3. gün, güncelleyen eski kullanıcı). Derleme 50'ye girmez.

## Rapor
`raporlar/2026-11-22_editor_aksam_isi.md`. Her madde için bitti / yapılmadı ve nedeni. İş listesinin "Mehmet'ten doğrudan" bölümüne tek satır.
