# Editör görevi – satış sürümü

**Tarih:** 18 Kasım 2026 · **Dayanak:** `raporlar/2026-11-18_odeme_alma_plani.md` · **Öncelik:** yolculuk işinden önce. Ücretsiz sınır işi (başlangıç istisnasıyla) bu sürüme dâhil.
Canlı veritabanına yazma yok; sürüm yayını Mehmet'te. Her madde ayrı commit; analyzer ve testler temiz.

1. **İptal/hata sonrası ikinci yol:** Satın alma iptal edilince ya da başarısız olunca paywall açık kalsın; seçili plan yıllıksa altta tek satır: "Yıllık fazla mı geldi? Aylık planla başla" → aylık planı seçer. İndirim ya da geri sayım yok. Olay: `purchase_downsell_shown`, `purchase_downsell_accepted`.
2. **Fiyat açıklığı:** Yıllık kartta aylığa bölünmüş fiyat; deneme satırı "7 gün ücretsiz, sonra {fiyat}/{dönem}; istediğin an iptal". Metinler mağazadan gelen gerçek fiyatla dolar.
3. **Ertesi gün tek hatırlatma:** Satın al'a basıp tamamlamayan kullanıcıya 24 saat sonra, 09–21 arasında bir bildirim (TrialEnding/Promotion türlerinden uygun olanla ya da yeni tür). Kişi başına bir kez.
4. **Onboarding sonu teklifi geri:** "Planın hazır" ekranından sonra paywall (tetikleyici `onboarding`); "Şimdilik ücretsiz devam et" düğmesi ana düğmeyle aynı ekranda, kaydırmadan görünür. Kapatınca doğrudan ilk okumaya gider. 24 Eylül'deki erteleme mantığının hangi kısmının kaldığını raporla.
5. **Teklif sayısı:** İlk oturumda ekranı kesen en çok iki teklif (onboarding sonu, ilk metin bitişi); sonraki günlerde günde bir. Şerit ve kilitli içerik sayılmaz.
6. **Paywall içeriği:** İlk ekranda Premium'un açtıkları gerçek sayılarla (etkin metin sayısı sunucudan). "Günlük 3 okuma limiti" gibi yanlış satırlar yok.
7. **Kilitli içerik ekranı:** kilitli metnin/bölümün adı, tek ana düğme "Premium'la şimdi oku", ikincil "Bugünkü ücretsiz hakkımla aç" (hak varsa). Tetikleyici ayrı adla.
8. **Küçük ekran:** SE 3 ve en büyük yazı boyutunda seçili plan + satın al düğmesi birlikte görünür. Ekran görüntüsüyle kanıtla.
9. **Android:** Satın alma akışını koddan iOS ile karşılaştır (ürün kimlikleri, deneme teklifi, hata işleme); fark varsa raporla. Gerçek cihaz denemesi Mehmet'te.

Rapor: `raporlar/2026-11-1X_satis_surumu.md` – maddeler, ekran görüntüleri (onboarding sonu teklifi, ikinci yol, kilitli içerik, SE 3), olay adları.
