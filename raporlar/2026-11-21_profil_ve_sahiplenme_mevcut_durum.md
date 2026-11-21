# Profil, rozet ve sahiplenme: uygulamada bugün ne var

**Tarih:** 21 Kasım 2026 · **Kaynak:** uygulama ve sunucu kodu, Mehmet'in bilgisayarından okundu (Flutter `lib/features/user`, `lib/features/game`, `lib/core/config/app_config.dart`; sunucu `DataAccess/DbInitializer.cs`). Sayılar yok; onlar canlı kayıttan gelecek (toplu görev, bölüm I).
**Neden yazıldı:** ekip 12:23'te profil resmi hakkında koda bakmadan yorum yaptı ("resmi görecek kimse yok", "hazır karakter önerelim"). Mehmet düzeltti: sistem var. Bu belge gerçek durumu sabitler; değerlendirme bunun üstüne yapılır.

## Var olanlar
| Alan | Durum |
|---|---|
| Profil resmi | **Var.** Galeriden seç, fotoğraf çek, görüntüle. **Yalnız üye hesapta:** misafirde kamera düğmesi gizli; yüklemeye çalışan misafire "hesabını koru" (kayıt) ekranı açılıyor |
| Premium işareti | Var: avatarın üstünde altın taç |
| Profil sayfası | Seviye, bu haftaki dakika, kitap sayısı, seri halkası, en uzun seri, rütbe ilerleme çubuğu ve gün tahmini, rozetler (son kazanılanlar + "tümünü gör"), "Okuma listem" rafı, misafire "ilerlemeni kaybetme" kartı |
| Profil bilgileri | Ad ("Sana nasıl hitap edelim?"), kullanıcı adı, biyografi, **"Profil herkese açık"** anahtarı, günlük hedef, öğrenme amacı, öğrenme stili, ilgi alanları, kutlama animasyonu ayarı |
| Rozetler | **Var, geniş.** 12 rütbe rozeti + yaklaşık 60 rozet, 8 küme: Quiz (8), Okuma (8), Kelime (9), Seri (8), Özel (7: Erken Kuş, Gece Kuşu, Geri Dönüş...), Performans (6), Sosyal (6: Top 100, Haftalık Şampiyon...), Gizli (6). Rozet sayfası, ayrıntı sayfası, kutlama, paylaşım kartı var |
| Liderlik tablosu | **Kodu tam, kapalı.** Podyum, profil resimleri, haftalık ve tüm zamanlar; ana sayfa kartı da hazır. `leaderboardEnabled = false`. Sunucu servisi çalışıyor |
| Haftalık özet | Sayfa var (bildirimden açılıyor) |
| Paylaşım | Uygulama davet kartı (ad, kitap sayısı, seri), rozet kartı, kitap kartı |

## Olmayanlar
- Hazır karakter / çizim avatar seçimi.
- Karakter için kazanılan eşya (giysi, gözlük, çanta, kitap): hiçbir altyapı yok.
- Başkasının profilini görme: "Profil herkese açık" anahtarı var ama profili gösterecek tek yer olan liderlik tablosu kapalı.

## Koddan görünen tutarsızlıklar (değerlendirmeye)
1. **Sosyal rozetler görünmeyen bir tablo için veriliyor.** Liderlik tablosu kapalı, ama "Top 100" rozeti kazanılıyor (18 Kasım raporunda ilk hikâye bitişinde 20 kişi almış). 363 müşteride ilk 100 bir başarı değil; kullanıcı hangi tablodan söz edildiğini de göremiyor.
2. **Rozet eşikleri tipik kullanıcıdan uzak.** Okuma: 1, 10, 25, 50... Tipik müşteri 1 hikâye okuyor; ikinci okuma rozeti 10. metinde. Kelime rozetleri "tam öğrenilen" kelimeye bağlı; öğrenilen kelimesi sıfırdan büyük yalnız 2 müşteri var.
3. **Rozet dili ses kuralına uymuyor.** "Quiz Master", "Quiz Legend", "Okuma Immortal" (İngilizce adlar), "sen gerçek bir LEGEND'sın!", büyük harfli "EFSANEVİ!", her cümlede emoji.
4. **Misafir resim yükleyemiyor.** "Kimse yüklemiyor" gözleminin olası nedeni; misafir/üye oranı gelince netleşir.

## Bilinmeyenler (bölüm I ile gelecek)
Misafir ve üye sayısı; resim yükleyen, adını giren, kullanıcı adı alan, biyografi yazan kaç kişi; rozet sayfasını açan oran; müşteri başına kazanılan rozet; hangi rozet kaç kişide; "Okuma listem"e ekleme yapan kaç kişi.
