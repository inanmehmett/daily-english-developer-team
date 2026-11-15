# Onboarding'den ilk okumaya geçiş – UX tasarım önerisi (Don Normal)

**Tarih:** 15 Kasım 2026 · Tek geçiş. **Durum: öneri, Mehmet onayı bekliyor.** Ekran görülmeden, kod ve analitik okunarak hazırlandı; ekran kaydıyla doğrulanmalı.

## Mevcut akış (koddan)
- Onboarding 17 ekran: değer vaadi, kelimeye dokun, dinle, ilerleme vaadi, isim, seviye, kitap sayısı, hedef, günlük dakika, kelime projeksiyonu, çalışma saati, ilgi alanları, yorum kanıtı, taahhüt, plan hazırlanıyor, plan özeti, "Hemen başlıyorsun, ücretsiz".
- Kullanıcılar neredeyse hepsini geçiyor: başlayan 27 kişiden 26'sı bitirdi, kişi başı ~15 adım kaydı.
- Son ekranın düğmesi "Ücretsiz başla"; basınca ana sayfa açılıyor. Paywall ilk okuma bitene kadar erteleniyor.
- Ana sayfada bu sorun için daha önce yapılmış bir çözüm var: "İlk okumana başla" kartı (seviyeye uygun, kilitsiz, en kısa kitabı önerir).
- Sonuç: kart olmasına rağmen onboarding'i bitiren 26 kişiden 18'i okumaya başlamadı.

## Teşhis (hipotez)
1. **Kapanış hissi:** 17 ekran sonunda "planın hazır" ve "ücretsiz başla" görmek bir işi bitirmiş hissi veriyor. Kullanıcı oturumu orada kapatıyor.
2. **Son ekran yanlış şeyi söylüyor:** fiyatı anlatıyor (ücretsiz, kart yok), okumayı değil. Kullanıcının 17 ekranda verdiği cevapların (seviye, ilgi alanı) karşılığı olan hikâye ona gösterilmiyor.
3. **Ana sayfa bir menü:** kart doğru yerde olsa da selamlama, günün işi, öneriler ile birlikte duruyor; tek bir sonraki adım yok.

## Öneri
1. **Son onboarding ekranı hikâyenin kapısı olsun.** Ekranda kullanıcı için seçilen hikâye görünsün: kapak, başlık, seviye, tahmini süre, "seviyene ve ilgi alanına göre seçtik". Düğme: "İlk hikâyeni oku". "Ücretsiz, kart gerekmez" bilgisi düğmenin altında küçük not olarak kalsın.
2. **Düğme doğrudan okuyucuyu açsın.** Geri tuşu ana sayfaya dönsün.
3. **Çıkış yolu olsun.** Düğmenin altında sessiz ikinci seçenek: "Önce uygulamaya göz atayım" → ana sayfa. Kullanıcı kapana kısılmamalı (README madde 9).
4. **Okuyucuda yeni bir şey eklenmesin.** İlk kullanım ipuçları zaten var.
5. **Ana sayfadaki kart kalsın.** Göz atmayı seçen ya da sonradan dönen kullanıcı için.

## Ölçüm
- Ana sayı: onboarding'i bitirenlerden okumaya başlayanlar (şu an 8/26).
- Yan sayı: "Önce göz atayım" seçenlerin oranı ve bunların sonradan okuyup okumadığı.
- Bozulmaması gereken: ilk metni bitirme oranı (şu an okumaya başlayan 32 kişiden 21'i).

## Bu öneride bilinmeyenler
- Yeni kullanıcının ana sayfada gerçekte ne gördüğü (ekran görülmedi).
- Onboarding'de geçen süre.
- 17 ekranın kısaltılması gerekip gerekmediği: veri kısaltmayı desteklemiyor (27'den 26'sı bitiriyor), bu yüzden önerilmedi.

## Sıradaki tasarım sorusu (bu öneride yok)
İlk metin bitince kullanıcı ana sayfaya dönüyor ve ertelenen paywall orada açılıyor. Metni bitiren 22 kişiden 6'sı sonraki okumaya geçti. İkinci okumaya geçiş anı ayrıca tasarlanmalı.
