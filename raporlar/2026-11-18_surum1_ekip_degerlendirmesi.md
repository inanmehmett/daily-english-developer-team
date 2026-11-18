# Sürüm 1 raporu – ekip değerlendirmesi ve kararlar

**Tarih:** 18 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Dayanak:** `raporlar/2026-11-18_surum1_ilk_oturum.md`, ekran görüntüleri (`raporlar/ekran_2026-11-18/`), `raporlar/2026-11-18_baslangic_duraklari_nexthook_taslak.md`.

## Okuma
12 madde kodlandı, akış SE 3'te uçtan uca sürüldü, 6 hata bulunup düzeltildi (ikisi yolculuktan önce de vardı: yüklenmeden plan satan paywall, ağ katmanındaki tekrar önleyici). Ekranlar plana uyuyor: onboarding sonu teklifinde "Ücretsiz başla: günde bir durak" kaydırmadan görünüyor; durak 2 bitişinde iki kapı var.
Cihazda **görülemeyenler:** gerçek satın alma, mağaza iptali ve "Aylık planla başla", Türkiye fiyatı ve deneme. Bunlar ancak TestFlight'ta görülür.

## Kararlar (editörün açık noktaları)
1. **Yayın paketi:** Eski 1.0.4+47 derlemesi yayınlanmaz; içinde V8 (şeridi gizleme) var. Tek paket çıkar: tetikleyici + sınırlar + Sürüm 1. Sıra editörün yazdığı gibi: sunucu → `NextHook` → uygulama.
2. **Durak 2 bitişi (Don, Dieter):** "Quiz'e Başla" bu ekranda ana düğme olamaz. İki kapı ana eylem: "Premium'la şimdi oku" dolu turuncu, "Yarın hatırlat" aynı boyda çerçeveli. Quiz, altında metin bağlantısı ("Bu metnin quizini çöz"). Durak 1 bitişinde ana düğme "Sıradaki durak", quiz yine bağlantı.
3. **Onboarding teklifinin başlığı (Sean):** "{ad}, yolculuğun hazır" üst satır; başlık "Beklemeden oku: 7 gün ücretsiz". Madde listesi olduğu gibi kalır (gerçek sayılarla, iyi).
4. **Günde bir teklif (takvim günü):** onaylandı.
5. **Dalda bekleyen Sürüm 2–3 işleri:** başlangıç sonu ilerleme kartı + ana teklif ve 3. durak kilidi **Sürüm 1 ile çıkar** (kullanıcı 3.–4. günde oraya varıyor; kilit olmazsa ücretsiz sınır delinir). Harita dönüşümü ve bildirim düzeni kapalı kalır.
6. **Merak cümleleri (Paul):** 12 taslak dil ve kural açısından uygun; son söylenmiyor, sayılar gövdeden. Tek düzeltme: Rabbits cümlesi şimdiki zamana çekilsin ("…otuz yıl boyunca haritada yok, çünkü biri onu bilerek siliyor" yerine: "Otuz yıl boyunca hiçbir haritada görünmüyor; biri onu bilerek gizliyor."). Toplam 44 satır; canlıya yazım Mehmet'in onayıyla, yedekli.
7. **Eski sürümle uyum (Kent):** Sunucu yayınlanınca 1.0.2 kullanan müşteriler de yeni sayıma girer. Eski istemci `readingTextId` göndermediği için başlangıç istisnasından yararlanamaz ve yeni sınır ekranını görmez. Editör, eski istemcinin 402'yi düzgün karşıladığını ve çökmediğini doğrulamalı; `readingTextId` gelmeyen isteklerde sunucu, kullanıcının son açtığı durağa bakarak istisnayı uygulayabiliyorsa uygulasın, olmuyorsa eski istemci için eski sayım (yalnız sözlük dışı) korunur.
8. **Ağ katmanı düzeltmesi:** bütün istekleri etkiliyor; TestFlight'ta en az bir gün kullanılmadan mağazaya gönderilmez.

## TestFlight'ta Mehmet'in bakacağı beş şey
1. Onboarding sonu teklif: Türkiye fiyatı ve "7 gün ücretsiz, sonra … /yıl" satırı doğru mu.
2. "Ücretsiz başla" → durak 1 → "Sıradaki durak" → durak 2 → iki kapı.
3. Satın al'a bas, mağaza sayfasını iptal et: "Aylık planla başla" çıkıyor mu.
4. Deneme başlat (sandbox): "Premium açıldı: yolculuğun bekliyor" → durak açılıyor mu.
5. Android'de aynı satın alma adımı.

## İtirazlar
- **Nassim:** Paket büyüdü (sınırlar + yolculuk + teklif + ağ katmanı). Tek tek ölçülemez; bu yüzden karşılaştırma yalnız 48 saat ölçüsüyle ve adım oranlarıyla yapılır. Sorun çıkarsa ilk geri alınacak parça onboarding sonu teklifi.
