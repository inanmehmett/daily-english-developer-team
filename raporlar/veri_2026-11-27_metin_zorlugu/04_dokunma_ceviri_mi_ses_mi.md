# 4. Dokunma kaydı "çeviri için" ile "ses için" dokunmayı ayırıyor mu?

**Kısa cevap:** kelimeye dokunma kaydı tek tür ve **anlam balonunun açılmasıdır**; amacı ayırmıyor. Dinleme ayrı kayıtlarda tutuluyor, biri hariç.

**Koddan (uygulama, 1.0.4):**
| Okurun yaptığı | Kayıt | Not |
|---|---|---|
| Kelimeye dokunur | `word_lookup` | Balon açılır, anlam görünür. Dokununca ses kendiliğinden çalmıyor |
| Balondaki "dinle" simgesine dokunur | **tutulmuyor** | Kelime seslendirilir ama olay yazılmıyor |
| Cümleyi dinler (basılı tutma ya da sesli okuma) | `sentence_listened` | Cümle sırası ve süreyle |
| Cümle çevirisini açar | `sentence_translated` | – |

Kayıttaki `source` alanı amacı değil, anlamın nereden geldiğini söylüyor (ağ, bellek); "çeviri mi, ses mi" sorusuna cevap vermez.

**Sayılar (müşteriler, bugüne kadar):**
| Kayıt | Olay | Kişi |
|---|---|---|
| Kelimeye dokunma (balon) | 13.326 | 294 |
| Cümle dinleme | 9.382 | 250 |
| Cümle çevirisi | 2.646 | 120 |
- Okuma kaydı olan 300 müşterinin 294'ü en az bir kelimeye dokunmuş, 250'si en az bir cümle dinlemiş.
- Süresi olan 1.683 okuma oturumunun 718'inde kelimeye dokunulmuş, 675'inde ses dinlenmiş, 245'inde cümleye dokunulmuş. Toplam 3.985 dakika okumanın 764 dakikası ses.

**Sonuç:** "100 kelimede dokunma" sayıları anlam balonunu sayıyor; ses için dokunma bu sayıya **karışmıyor**. Yani 8–12 dokunma, okurun anlamına baktığı kelimelerdir (merak için bakılanlar dahil). Balondaki "dinle"nin ne kadar kullanıldığı bilinmiyor; tutmak için o düğmeye tek bir olay eklemek yeter (uygulama değişikliği).
