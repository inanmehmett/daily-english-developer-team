# Sınav sistemi bu sürüme (derleme 50): kapsam, metinler, yeni parçalar

**Tarih:** 22 Kasım 2026, 02:40 · **Mehmet (02:20):** "Ben bu sürümde bu işin hallolmasını istiyorum."
Bu söz `2026-11-22_sinav_sistemi_onerisi_charles.md` içindeki "sıradaki sürüm" ayrımını kaldırır: C1–C9 derleme 50 ile birlikte çıkar. Dışarıda kalan tek şey C10.

## 1. Kapsam
| İş | Nerede | Durum |
|---|---|---|
| C1 ısınma kuralı | Sunucu | Kod hazır (dal `fix/assessment-warmup-by-level`); gönderim ve yayın bekliyor |
| C2 belirsiz dört B1 parçası kapanır, **yerine dört yeni parça girer** (bölüm 4) | Canlı veri | Yeni parçalar yazıldı; editör yükler |
| C3 sonuç, geçilen en yüksek parçanın seviyesini aşmaz | Sunucu | Yazılacak |
| C4 belge testi seviyeyi yalnız yükseltir | Sunucu | Yazılacak |
| C5 kelime taraması kelime bazında kaydedilir | Sunucu | Yazılacak |
| C9 seviye değişince yolculuk (bitmiş hikâye yoksa yeniden atanır) | Sunucu | Yazılacak |
| "…" ile biten 29 soru tam soru cümlesi olur | Canlı veri | Yeni kökler hazır: `veri_2026-11-22/belge_sorulari_yeni_kokler.md` |
| C6 belge testinde sorular tek tek | Uygulama | Yazılacak (editör tahmini yarım–1 gün) |
| C7 sonuç metinleri (bölüm 2) | Uygulama | Metinler hazır; kod yarım–1 gün |
| C8 100 üzerinden puan görünmez (bölüm 3) | Uygulama | C7 ile birlikte |
**Bu sürümde yok (C10):** belge testinin kelime taramasıyla başlaması. Editör tahmini 2–3 gün; ısınma artık kullanıcının seviyesini kullandığı için asıl şikâyeti C1 ve C6 çözüyor. Gerçek deneme verisi gelince bakılır.
**Dürüst sınır:** 176 sorunun 29'u düzeltildi; kalan 147 soru (çoğu metin sorusu) henüz insan gözüyle okunmadı. Belge satırı görünürken bu açık kalıyor; Charles ve Paul'un sıradaki işi. Yeni B1 parçaları da veriyle denenmedi; kalıcı kural gereği 30 gösterimden sonra bakılacak.
**Süre:** uygulama işleri editörün kendi tahminiyle 1–2 gün; derleme 50 o kadar gecikir.

## 2. Sonuç metinleri (Paul; ses kuralları: yargı yok, teşhis var)
**Yeniden ölçme sonucu**
| Durum | Başlık | Alt satır |
|---|---|---|
| İlk ölçüm (önceden seviye seçilmemiş) | Seviyen: {seviye} | {seviye cümlesi} |
| Yükseldi | Seviyen artık {seviye} | {seviye cümlesi} |
| Aynı | Seviyen aynı: {seviye} | Doğru yerdesin. {seviye cümlesi} |
| Sonuç daha düşük, kullanıcı başlattı | Seviyeni güncelledik: {seviye} | Bu seviyedeki hikâyeler sana daha rahat gelecek. |
| Sonuç daha düşük, ana sayfa kartından (seviye korunur) | Seviyen aynı: {eski seviye} | Doğru yerdesin. {seviye cümlesi} |
| Güvenilmez tur | Bu sefer net bir sonuç çıkmadı | Seviyen aynı kaldı. Hakkın da duruyor; istediğinde yeniden deneyebilirsin. |
Her sonucun altında tek ana düğme: "Seviyene göre hikâye: {hikâye}" (sıradaki hikâyenin kapağı). "Seviyen düştü" hiçbir yerde yazılmaz.

**Seviye cümleleri**
- A1 altı: Çok kısa cümleleri ve tanıdık kelimeleri okuyorsun. A1 hikâyeleri tam sana göre.
- A1: Kısa, gündelik metinleri okuyorsun. Her hikâyede birkaç yeni kelimeyle tanışacaksın.
- A2: Gündelik konulardaki kısa hikâyeleri rahat okuyorsun. Sıradaki adım biraz daha uzun metinler.
- B1: Tanıdık konulardaki uzun metinleri takip ediyorsun. Sıradaki adım daha zengin anlatımlar.
- B2: Ayrıntılı ve uzun metinleri rahat okuyorsun. Buradaki en ileri hikâyeler senin.

## 3. Belge testi sonucu (C8)
- Sayı gösterilmez. Başlık: "Okuma seviyen: {seviye}". Altında seviyenin içindeki yer, sözle: aralığın alt üçte biri "{seviye} seviyesinin başındasın", orta "{seviye} seviyesinin ortasındasın", üst "{seviye} seviyesinin sonuna yaklaştın".
- Güven Orta ise ek satır yok (kullanıcıya "orta güven" denmez). Kesin değil: "Bu sefer net bir sonuç çıkmadı. Hakkın duruyor; istediğinde yeniden deneyebilirsin."
- Belgenin üstünde de sayı yok; yalnız seviye ve tarih (bugün de yalnız seviye yazıyor).
- Profil seviyesi yükselmediyse (C4): "Belgen hazır: {seviye}. Okuma seviyen {profil seviyesi} olarak kaldı." Yalnız ikisi farklıysa.

## 4. Dört yeni B1 parçası (Paul yazdı, Charles kuralla denetledi)
Kural: her boşlukta yalnız bir şık cümleye uyar; ipucu boşluğun cümlesinde ya da bir öncekinde; şıklar aynı türden. Doğru şık **kalın**. Yüklerken doğru şıkkın konumu karıştırılır. Bunlar veriyle denenmedi.

**Parça B1-yeni-1**
> Elif started running last spring because her doctor told her to get more exercise. At first she could only run for five minutes before she had to ___. She did not give up, and every week she added one more minute. Now she can run for half an hour and she feels much ___ than before. Next month she will take part in her first ___.
1. **stop** · hurry · win
2. **fitter** · weaker · lazier
3. **race** · match · concert

**Parça B1-yeni-2**
> When the lift in our building broke, the company said the repair would take two weeks. For Mrs Kaya, who lives on the sixth floor and walks with a stick, this was a serious ___. Her neighbours quickly made a plan. Each day a different person carried her shopping up the ___. When the lift finally worked again, she invited them all to dinner to say ___.
1. **problem** · holiday · success
2. **stairs** · roof · wall
3. **thank you** · sorry · goodbye

**Parça B1-yeni-3**
> Tom wanted to save money for a trip to Japan, so he looked carefully at what he spent each month. He was surprised to find that coffee from cafés cost him more than his phone ___. He bought a small machine and began making coffee himself instead of ___ it. After eight months he had saved enough for his plane ___.
1. **bill** · call · screen
2. **buying** · selling · growing
3. **ticket** · pilot · engine

**Parça B1-yeni-4**
> The village of Karaca had no bus on Sundays, which was difficult for people without a car. Last year a retired driver offered to help. Every Sunday morning he takes his neighbours to the market in town and brings them ___ in the afternoon. He does not ask for money, but people usually pay for his ___. Now the village wants the bus to run on Sundays ___.
1. **back** · away · down
2. **petrol** · ticket · licence
3. **too** · never · once
