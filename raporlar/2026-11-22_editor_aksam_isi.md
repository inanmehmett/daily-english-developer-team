# Editörden: akşam talimatının sonucu

**Tarih:** 21 Kasım 2026 gece · **Kimden:** editör · **Kime:** ekip
**Talimat:** `ortak/editor_gorevi_2026-11-21_aksam.md` (son hâl, 21:35)
**Mehmet'in editöre doğrudan iki sözü (22:00 civarı), talimatın üstünde:**
1. "Seviyeni belgele gizli olmasın." → T19 geri alındı; satır yeniden görünür.
2. "Derlemeyi daha sonra yapacağız." → A7 (sürüş, görüntüler, TestFlight, Play) ve gerçek ekran isteyen D taslağı yapılmadı.

## Önce: ekibin bilmesi ve karar vermesi gerekenler

| # | Konu | Durum | Ekipten beklenen |
|---|---|---|---|
| 1 | **"Seviyeni belgele" görünür** (Mehmet). Ekip "gizli kalsın, sorular okununca açılır" demişti | Satır derleme 50'de görünür olacak. 176 soru hâlâ okunmadı | Charles ve Paul'un okuması öne alınmalı. Döküm hazır: `raporlar/veri_2026-11-22/belge_sorulari.md` |
| 2 | **Çeldirici "aynı türden" kuralı yazılmadı** (Q2) | Sunucudaki kelime türü güvenilir değil: quiz havuzundaki 1.136 kelimenin 876'sı "isim" etiketli, bunların 91'i fiil, aralarında sıfatlar var (jealous, remarkable, clear). Bu veriyle kural yanlış şık üretir. Bugünkü "fiil / fiil değil" ayrımı duruyor; 3 harf kuralı yazıldı | Tür verisi düzeltilsin mi (içerik işi)? Düzelince kural birkaç satır |
| 3 | **Ada metni (1023) değiştirilmedi** (C) | Kural gereği: okuma konumu bölüm sırasıyla değil **sayfa numarasıyla** tutuluyor (metin bölümsüz kayıtlı; sayfalar telefonun ekranına göre 2–5 arası). Yarıda okuyan 24 müşterinin 17'si 1. sayfada, 7'si 2. ya da 3. sayfada. Yeni metin neredeyse aynı uzunlukta (287 → 286 kelime, aynı sıra); 7 kişi için kayma birkaç cümle olur | Bu kaymayı kabul ediyorsanız yazın, betiği hazırlarım. Çeviri ve sözlük eşleşmesi ayrıca yenilenecek |
| 4 | **Etiket betiği canlıda çalışmadı** (C) | Betik ve yedek hazır; canlıya yazma editörün izin katmanında reddedildi (okuma serbest) | Mehmet çalıştıracak; komut en altta |
| 4b | **Sunucu PR'ı açık, yayınlanmadı** (B) | Mehmet'in kayıtlı kuralı: sunucu yayınını (PR birleştirme) kendisi yapar ya da editöre o an açıkça söyler. İki dal Mehmet'in izniyle gönderildi (23:40); PR #16 açık, testler temiz | Mehmet birleştirecek |
| 4c | **Sıralama rozetleri kapatıldı** (Mehmet, 23:55: "kapatılması gereken rozetleri kapat") | Liderlik tablosu kapalıyken altı sıralama rozeti verilmeye devam ediyordu: Top 100 (87 müşteri), Top 50 (27), Haftalık Şampiyon (8), Seviye Lideri (3), Top 10 (3). Kullanıcı sıralamayı göremiyor, rozetini alıyordu. PR #16'ya eklendi (`f873a43`): tablo kapalıyken altısı da verilmez ve kazanmamış olana hedef olarak gösterilmez; kazanılmış rozetler koleksiyonda kalır. Tablo dönünce tek sunucu ayarıyla (`Gamification:RankingBadgesEnabled=true`) birlikte geri gelir. Haftalık Şampiyon'un yeni kuralı kodda ama tablo dönene kadar uykuda; yukarıdaki 5 ve 6 o zamana kalır | Bilgi |
| 5 | **Haftalık Şampiyon'un saati** (B) | Sunucuda hafta pazartesi 00:00 UTC'de (Türkiye saatiyle 03:00) kapanıyor; haftalık XP o an sıfırlanıyor. Rozet o an veriliyor, pazar 23:59'da değil. Pazar 23:59'a çekmek haftalık XP sıfırlamasını da taşımak demek (seri dondurma hesabı ona bağlı); bu PR'a almadım | 3 saatlik fark kabul mü? |
| 6 | Haftalık Şampiyon: iki ayrıntı | Birincilik paylaşılıyorsa (aynı XP) o hafta rozet verilmiyor ("tek kişi" kuralı). Rozet haberi uygulama açıkken gidiyor; kullanıcı 03:00'te uygulamada değilse kutlama görmez, rozet koleksiyonunda bulur | Bilgi. Kutlamanın sonraki açılışta gösterilmesi ayrı iş |
| 7 | **"Geri dön" metinlerinde tablonun söylemediği üç yer** (B) | (a) 14. gün, hikâye bilinmiyorsa tablo yalnız başlık veriyor. Yeni cümle yazmadım; gövde bugün canlıda giden cümle olarak kaldı: "Kelimelerin ve seviyen yerinde. Bir bölüm yeter, kaldığın yerden." (b) Hikâye bilinmiyorsa {dk} = 3. Veriden doğrulandı: her seviyenin başlangıç durakları 2–3 dakika, ücretsiz metinlerin ortancası 2–3. (c) Çok bölümlü kitapta {dk} bir bölümün süresi (kitabın süresi ÷ bölüm sayısı); yoksa "43 dakikalık hikâye" çıkardı | Paul (a) için gövde yazarsa bir satırlık değişiklik |
| 8 | Günün quizinde "Yeniden başla" | Günün quizi yeniden çözülmediği için o ekranda metin bağlantısı "Alıştırmaya geç" (bugün de öyleydi). "Yeniden başla" alıştırma turunda. Öneri yoksa ana düğme yeni tur | Bilgi |
| 9 | **Kariyer sayfasını gerçek ekranda görmedim** | Kod ve kural testleri tamam (bayrak, etiket, açılış kaydırması). Ama etiketin yolda nasıl durduğunu, büyük yazıdaki hâli ancak sürüşte görürüz | A7 sürüşünde ilk bakılacak ekran |
| 10 | Yüzde etiketinin yeri | Etiket bayrağın yanında duruyor. Bayrak 24 pt kuralıyla kaydığında etiket de onunla kayıyor (en çok 19 pt). D2'deki "yüzde dolumun gerçek ucunu gösterir" ile fark bu | Dieter görüntüde karar versin |
| 11 | Düzeltme: "…" sayısı | Bilgi cevaplarında "176 sorunun 41'i '…' ile bitiyor" yazmıştım. Doğrusu: 41 soruda "…" geçiyor, **29'u** "…" ile bitiyor. Kalan 12'sinde "…" yalnız alıntının içinde | Charles'ın "tam cümleye çevir" listesi 29 soru |
| 12 | Çeviri işçileri | Mehmet 21:30'da işçi sayısını ikiye katlattı (8 işçi; 21 Kas 22:40'ta 221/261). Talimattaki "ertele" bu yüzden uygulanmadı | Bilgi |

## A. Uygulama (`feat/journey-core`, 7 yeni commit, uzak depoda: `33b3ecab` … `03eb5028`)
Tam test turu temiz: 1.284 test geçti. Analiz temiz.

| Madde | Durum | Not |
|---|---|---|
| T19 | **Geri alındı** (`33b3ecab`) | Mehmet'in sözü |
| A1 Ana sayfa yolculuk kartı | **Bitti** (`2db1b3c2`) | Gövde yolculuk sayfasını açar (`journey_page_shown`, kaynak `home_card_body`); hak bitince Premium düğmesinin altında "Yarın hatırlat" (aynı bileşen, kaynak `home`); hiç okunmamış seviye yolculuğunda "Senin yolculuğun · Kafe Hikâyeleri", başlangıç yolculuğu n/4 kalır. 4 yeni test |
| A2 Kariyer sayfası | **Bitti, ekranda görülmedi** (`a0ec9f5e`) | E1 ana dalda; E2, kapı, halka ve anahtar silindi; metinler çeviri dosyasında. Bayrak yüzdeyi taşıyor, %0'da "Yeni yol başladı"; etiket 13 pt, büyük yazıda 17 pt'de sabit; rozet, ad ve yola binmiyor. Bayrak rozete 24 pt'den yakın değil. Şeritte yalnız cümle. Açılışta eklenen kısım 0,6 sn'de doluyor ("hareketi azalt"ta yok; rütbe atlandıysa yeni rütbenin başından). Kayıt kartı büyük yazıda tek satır, × 44 pt. Rozeti üst alanın altında kalan rütbenin adı çizilmiyor. Ekran okuyucu: yol tek cümle, rozetler düğme ve durumuyla. 14 kural testi + 24 ek testi |
| A2, K1'in asıl nedeni | **Bulundu ve düzeltildi** | Rozeti kart örtmüyordu: açılış kaydırması üstte yarım kalan rozeti tam göstermek için sayfayı yukarı çekiyor, kullanıcının kendi rozeti alttan dışarı çıkıyordu. Artık son söz kullanıcının rozetinde; testle kilitli |
| A3 Yorum ekranı | **Zaten koddaydı** | 20 Kasım'da commit'lenmiş (`6f10495d`), derleme 49'un içinde. Yazılacak bir şey yoktu. SE 3 koşulunu testle kilitledim (`26cfb63b`) |
| A4 Günün quizi | **Bitti, bir kural hariç** (`48e5e6ca`) | Başlık cümle (8+, 5–7, 4 ve altı); ana düğme "Sıradaki hikâye"; "Yeni tanıştığın kelimeler" ikincil, alt sayfanın başlığı da aynı; paylaşım yalnız 8+ ve ikincil; 3 harften kısa karşılık çeldirici olmuyor; sekmede "#49" kalktı, halkaların üstünde "BU HAFTA", orta boşluk daraldı. "Çözülen gün dolu halka" zaten vardı. **Yazılmayan:** "aynı türden çeldirici" (yukarıda 2). 10 yeni test |
| A5 Yeniden ölçme | **Bitti** (`9403b905`) | Ana sayfa kartı `offer` gönderiyor; profil `user` |
| A6 Bildirimden kapak | **Bitti** (`03eb5028`) | Bildirimde `readingTextId` varsa kapak sayfası; yoksa ya da hikâye katalogda değilse ana sayfa. Uygulama bildirimle soğuk açılırsa katalog için 8 saniyeye kadar bekliyor |
| A7 Sürüş ve derleme | **Yapılmadı** | Mehmet: "derlemeyi daha sonra yapacağız" |

## B. Sunucu (dal `feat/winback-story-quiz-exact-weekly-champion`, 6 commit, PR #16)
Tam test turu son commit (`f873a43`) üzerinde tek geçişte temiz: 1.800 geçti, 0 başarısız, 3 atlandı. (İlk turda 2 test kalmıştı: biri yeni 30. gün metnini bekleyen eski test, düzeltildi; öbürü dokunulmayan beta daveti testi, makine yükü altında bir kez takıldı, sonraki iki turda geçti.) **PR #16 açık, birleştirilmedi:** https://github.com/inanmehmett/DailyEnglish/pull/16

| Madde | Durum | Not |
|---|---|---|
| "Geri dön" metinleri | **Bitti** | Dört günün metni tablodaki gibi; yedekler dahil. {hikâye}: yarım kitap, yoksa yolculuğun şimdiki durağı; **hiçbir şey yazmayan** yeni bir sorguyla (`JourneyService.PeekCurrentStopsAsync`). Yolculuğu olmayana yolculuk atanmıyor (testle kilitli). Başlık 40 karakteri geçerse "Sıradaki hikâyen seni bekliyor". Bildirimde `readingTextId`; `action` "win_back" kaldı. 7. günde ada hitap korundu |
| Quiz cevabı tam eşleşme | **Bitti; risk doğrulandı, yok** | Uygulama şıkları kısaltıp gösteriyor ve o metni gönderiyor. Kısaltma kuralı 23 Eylül'den (yayından önce) beri değişmedi; sahadaki her sürüm aynı metni yolluyor. Sunucu artık aynı kuralı uygulayıp tam eşleşme arıyor. Test, canlıdaki 1.829 karşılığın tamamını uygulamanın kendi çıktısıyla karşılaştırıyor. **Yan kazanç:** eski kural 48 karşılıkta doğru şıkkı yanlış sayıyordu ("planlı/amaçlı gezi" ekranda "planlı gezi" görünür, ön ek değildir); o da düzeldi |
| Haftalık Şampiyon | **Bitti** (saat notuyla) | Anlık verme kapandı. Hafta kapanırken, XP sıfırlanmadan hemen önce, en yüksek XP'li tek gerçek kullanıcıya; şart en az 10 katılımcı ve 300 XP. Ekip ve test hesapları ne sayılıyor ne kazanıyor. Verilmiş rozetlere dokunulmadı |

## C. İçerik
| Madde | Durum | Not |
|---|---|---|
| Etiket A2 → B1, 7 metin | **Betik ve yedek hazır, canlıda çalışmadı** | `MigrationScripts/RelabelTextLevels_2026_11_21.sql` (slug ile, eski seviye koşullu; iki kez çalışsa bir şey değişmez). Yedek: Mehmet'in bilgisayarında `~/DailyEnglish-kapak/backups/2026-11-21-seviye-etiketi/readingtexts_once.csv`. 1063 ve 1089'a dokunulmuyor |
| Ada metni (1023) | **Çalıştırılmadı** (kural) | Yukarıda 3 |

## D. Veri ve taslak
| Madde | Durum | Not |
|---|---|---|
| 176 sorunun dökümü | **Bitti** | `raporlar/veri_2026-11-22/belge_sorulari.md`: doğru şık işaretli, "…" ile biten 29 soru işaretli, 32 metin sorularıyla birlikte |
| Ana sayfa sadeleşme taslağı (A ve B) | **Yapılmadı** | Gerçek ekran istiyor; sürüşle birlikte (Mehmet'in "derleme sonra" sözü) |

## Mehmet'in yapacakları
1. **Sunucu PR #16'yı birleştir** (ya da editöre "yayınla" de). Birleştirme canlıya yayındır: "geri dön" bildirimleri yeni metinle gitmeye başlar, quiz cevabı tam eşleşmeyle sayılır, Haftalık Şampiyon anlık verilmez.
2. **Etiket betiği (canlıya yazma; editörün izin katmanı reddetti):** backend deposunda
   `psql "$DATABASE_PUBLIC_URL" -v ON_ERROR_STOP=1 -f MigrationScripts/RelabelTextLevels_2026_11_21.sql`
   Beklenen çıktı: `UPDATE 7`. Betik PR'dan bağımsız; istediğin zaman çalışır.
3. Derleme 50 sürüşü ve mağaza yüklemesi: "sonra" dediğin zaman. `feat/journey-core` son hâli 21 Kas 23:50'de Mehmet'in telefonuna kuruldu (canlı sunucuya bağlı); kariyer sayfasını gerçek ekranda ilk Mehmet görecek.
