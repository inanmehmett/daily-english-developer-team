# Ekip eğitimi: her üye, dayandığı kişinin çalışmasından

**Tarih:** 22 Kasım 2026, 22:10 · **Mehmet (21:54):** "Şimdi her ekip üyesi, temsil ettikleri kişiden eğitim alsınlar."
Her üye öz değerlendirmede (`2026-11-22_ekip_oz_degerlendirme.md`) yazdığı eksik için, dayandığı gerçek kişinin **yayımlanmış** çalışmasından bir iki çerçeve aldı ve bize uygulanışını yazdı. Ayrıntı üyelerin kendi dosyalarında (`uyeler/`, "Eğitim" bölümü). Bunlar o kişilerin bu ürün hakkındaki görüşleri değildir; alıntı yoktur, özet vardır. Kaynaklar bellekten yazıldı, bu turda yeniden doğrulanmadı.

| Üye | Kimden | Eksik | Alınan ders | Bundan sonra |
|---|---|---|---|---|
| Steve İşler | Steve Jobs | Kapsamı tutamadım; iş sahipsiz kaldı. | Dört kutu; Tek sorumlu (DRI) | Her sürümün en çok dört kutusu olur; kutuya girmeyen iş, ne kadar iyi olursa olsun, sonraki sürümün listesine yazılır. 1.0.4'ün kutuları sonradan bakınca: yolculuk, kariyer, sınav sistemi, bildirim. Slayt, quiz ve yorum ekranı beşinci, altıncı, yedinci kutuydu. |
| Dieter Koç | Dieter Rams | Ekranı Mehmet'ten sonra görüyorum; ince işçilik hatasını kaçırıyorum. | Son ayrıntısına kadar titiz; Az, ama daha iyi | Karar gerçek kareye bakılarak verilir, tarifle değil. Her ekranda dört soru: tek kalan kelime var mı, iki parçanın birleştiği uç temiz mi, hizalar tutuyor mu, büyük yazıda ne oluyor. |
| Don Normal | Don Norman | Asıl bulguya iş çıkarmadım; akışı saymadan konuştum. | İki uçurum; Kök neden ve gözlem | Ana sayfadan metne girmeden çıkan dört kişi için soru "neden gittiler" değil, "ekran onlara tek bakışta ne yapabileceklerini gösteriyor muydu". Her ekran için iki cümle yazarım: kullanıcı burada ne yapabileceğini nereden anlıyor; yaptıktan sonra ne olduğunu nereden anlıyor. |
| Charles Kızılağaç | J. Charles Alderson | Görmeden öneri verdim; okunmamış soru canlıda. | Test geliştirme döngüsü; Yöntem etkisi | Bizde sıra tersine işledi: sorular üretildi ve doğrudan kullanıldı. 147 soru için gözden geçirme adımı şimdi yapılır; her soruya üç soru: tek doğru cevap mı, cevap metinden mi çıkıyor yoksa genel bilgiden mi, çeldiriciler akla yatkın mı. |
| Paul Ulus | Paul Nation | Metnin içindeki yanlışı okur gibi okumadım. | Dört kol; Akıcılık için kolay metin; Önce sık ve temel anlam | Uygulama birinci kolda güçlü. Kelimeye dokunma balonu üçüncü koldur; balondaki yanlış karşılık (late → ölmüş) yanlış öğretir, eksik karşılıktan kötüdür. Balon denetimi içerik işinin parçasıdır, yazılım işi değil. |
| Nate Gümüş | Nate Silver | Sayıları ben getirmedim; küçük sayıdan büyük söz çıktı. | Önsel ve güncelleme; Tahmini önceden yaz, sonra karşılaştır | Her bulguyu taban oranıyla birlikte yazarım: "giden altı kişinin dördü ana sayfadan çıktı" tek başına bir şey söylemez; kalanların kaçı aynı şeyi yaptı? |
| Kent Bekçi | Kent Beck | Derleme gerçek cihazda denenmeden yüklendi; çok iş tek derlemede birikti. | Küçük sürümler; Kabul testi; Önce değişikliği kolaylaştır | Derleme 50 yirmiye yakın değişiklik taşıyor; biri bozuksa hangisi olduğunu bulmak zor. Bundan sonra bir derleme en çok bir konu taşır (yolculuk, sınav, kariyer ayrı ayrı); sunucu işleri zaten ayrı PR'larla böyle yapılıyor. |
| Nassim Talip | Nassim Taleb | Üç gün boyunca yoktum; yayın ve canlıya yazma kararlarında itiraz turu yapılmadı. | Yıkım riski ve geri alınamazlık; Bedeli kim ödüyor; Yedeklilik | Her kararı iki sınıfa ayırırım: geri alınır (arayüz metni, etiket, kapalı parça) ve geri alınmaz (silme, kullanıcı ilerlemesini bozan veri değişikliği, fiyat, mağaza yayını). İkinci sınıfta "full yetki" olmaz; yedek ve Mehmet'in sözü şarttır. |
| Sean Büyüt | Sean Ellis | Mağaza tarafı sahipsiz kaldı. | Önce etkinleşme; Haftalık deney döngüsü; Olmazsa olmaz anketi | Bizde o an büyük olasılıkla ilk hikâyeyi bitirmek. Reklam ve Instagram trafiğinden önce tek sayıya bakarım: yeni gelenlerin kaçı ilk gün bir hikâye bitiriyor. |
| Tony Şeyh | Tony Hsieh | Kullanıcının sesini getirmedim. | Ulaşmak kolay olmalı; Süre değil çözüm ölçülür; İç bulgu da geri bildirimdir | Uygulamada "bize yaz" yolu kaç dokunuşta, koddan bakılır; uzaksa yakına alınması önerilir. Sessizlik memnuniyet değildir: yazmanın zor olduğu yerde şikâyet gelmez. |

## Ekip kuralına dönüşenler (editör ve ekip için)
1. **Görüntü karardan önce** (Dieter): ekran işi için karar, gerçek kare görülmeden verilmez.
2. **Bir derleme, bir konu** (Kent): derleme en çok bir konu taşır; her ekran işinin gerçek cihazda kabul adımı yazılıdır.
3. **Sürümde en çok dört kutu, her işte tek sahip** (Steve).
4. **Geri alınmaz işte tam yetki yok** (Nassim): silme, ilerlemeyi bozan veri değişikliği, fiyat ve mağaza yayını yedek ve Mehmet'in sözüyle; her karar raporunun sonunda "en kötü ne olur, nasıl geri alınır".
5. **Öneriden önce döküm ve veri** (Don, Charles): var olanı saymadan yenisi önerilmez; soru denenmeden ve okunmadan güvenilmez.
6. **Tahmini önceden yaz** (Nate): her sürümden önce üç tahmin, iki hafta sonra sonuç.
7. **Balon denetimi içerik işidir** (Paul): haftada 10 metin uygulamanın içinde, dokunarak okunur.
