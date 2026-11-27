# 1. Üç başlangıç metni: dokunulan kelimeler, bırakma yeri, bitiren ve bırakanın dokunması

**Kaynak:** canlı veritabanı, salt okuma, 27 Kasım 2026 15:40; yalnız müşteri hesapları (testçi, geliştirici, promosyon hariç). Kişi adı ve e-posta okunmadı.

## Nasıl sayıldı
- **Başlayan:** metin için okuma kaydı açılmış müşteri. **Bitiren:** o kaydı "tamamlandı" olan.
- **Kelimeye dokunma, kişi ve metin başına:** okuma oturumlarının dokunma sayacı (her sürümde tutuluyor).
- **Hangi kelimeye dokunuldu:** dokunma olayındaki kelime. Olayda metin kimliği yalnız 1.0.4'te var (13.326 olayın 1.049'u); kalanı, dokunmanın düştüğü okuma oturumuna göre metne bağlandı. İki yolun ikisi de olan 937 olayda sonuç birebir aynı. 1.643 olay (%12) hiçbir oturuma düşmedi ve sayılmadı; aşağıdaki kişi sayıları bu yüzden biraz eksik.
- **Dokunma = kelime balonunun açılması** (anlam). Dinleme ayrı olaydır (madde 4).

## Özet
| Metin | Kelime | Başlayan | Bitiren | Bırakan | Bırakanlardan ilk sayfada kalan |
|---|---|---|---|---|---|
| 916 Two Cups (A1) | 217 | 151 | 121 (%80) | 30 | 18 |
| 1083 Thirty-One Mornings (A1) | 254 | 71 | 49 (%69) | 22 | 12 |
| 1023 Rabbit Island (A2) | 287 | 118 | 88 (%75) | 30 | 20 |

## Bitiren ve bırakan: dokunma
| Metin | Grup | Kişi | Kişi başına dokunma | Hiç dokunmayan | 100 kelimede dokunma (toplam) | 100 kelimede dokunma (ortanca kişi) | Dakikada dokunma | Kişi başına okuma süresi |
|---|---|---|---|---|---|---|---|---|
| 916 Two Cups | bitiren | 121 | 16,9 | 9 | 7,8 | 5,5 | 2,7 | 6,3 dk |
| 916 Two Cups | bırakan | 30 | 7,0 | 6 | 8,0* | 4,6* | **5,1** | 1,4 dk |
| 1083 Thirty-One Mornings | bitiren | 49 | 23,6 | 5 | 9,3 | 4,3 | 3,2 | 7,3 dk |
| 1083 Thirty-One Mornings | bırakan | 22 | 4,7 | 12 | 3,5* | 0,0* | 4,1 | 1,1 dk |
| 1023 Rabbit Island | bitiren | 88 | 33,0 | 2 | 11,5 | 7,0 | 3,8 | 8,7 dk |
| 1023 Rabbit Island | bırakan | 30 | 8,2 | 7 | 6,8* | 3,9* | 3,6 | 2,3 dk |

\* Bırakanın okuduğu kelime sayısı tutulmuyor; kaldığı sayfa / toplam sayfa oranıyla tahmin edildi (sayfa sayısı telefona göre 2–5 arasında değişiyor), o yüzden bu iki sütun bırakanlar için kabadır. Bırakanlar için güvenilir ölçü **dakikada dokunma**dır.

**Okuma:**
- Bitirenler bile 100 kelimede 8–12 kez dokunuyor (toplam); ortanca kişi 4–7 kez. Ortalama, çok dokunan az sayıda kişi yüzünden ortancanın üstünde.
- Two Cups'ta bırakanlar dakikada bitirenlerin iki katı dokunmuş (5,1'e 2,7); Thirty-One Mornings'te de daha çok (4,1'e 3,2). Rabbit Island'da fark yok (3,6'ya 3,8). Küçük gruplar (22–30 kişi): hipotez.
- Thirty-One Mornings'i bırakan 22 kişinin 12'si **hiç dokunmadan**, ortalama 1 dakikada çıkmış: bu metinde bırakma kelime zorluğundan çok başka bir şeyden (ilgi, uzunluk, yanlışlıkla açma) olabilir.

## Bırakanlar nerede bıraktı
Tutulan ölçü: kaldığı sayfa ve toplam sayfa. Cümle sırası ya da kaydırma yüzdesi **tutulmuyor** (okuma kaydındaki "tamamlanma yüzdesi" ve "okunan kelime" alanları hep 0). Tutmak için: okuyucu, ilerlemeyi kaydederken görünen son cümlenin sırasını da yollayabilir.
| Metin | İlk çeyrek | Yarıya kadar | Dörtte üçe kadar | Son çeyrek |
|---|---|---|---|---|
| 916 Two Cups (30) | 13 | 14 | 1 | 2 |
| 1083 Thirty-One Mornings (22) | 5 | 9 | 4 | 4 |
| 1023 Rabbit Island (30) | 10 | 15 | 4 | 1 |

Üç metinde de bırakanların çoğu metnin ilk yarısında, büyük kısmı daha ilk sayfadayken bırakıyor (Two Cups 18/30, Rabbit Island 20/30, Thirty-One Mornings 12/22).

## En çok dokunulan 20 kelime
"Kişi": o kelimeye en az bir kez dokunan müşteri sayısı. Yüzde, metne başlayanlara göre.

### 916 · Two Cups (A1 başlangıç, 217 kelime, 151 başlayan)
| # | Kelime | Kişi | Başlayanların yüzdesi | Dokunma |
|---|---|---|---|---|
| 1 | bucket | 85 | %56 | 131 |
| 2 | stairs | 69 | %46 | 130 |
| 3 | stood | 69 | %46 | 108 |
| 4 | flat | 65 | %43 | 90 |
| 5 | pot | 57 | %38 | 63 |
| 6 | above | 53 | %35 | 65 |
| 7 | cleans | 50 | %33 | 57 |
| 8 | wet | 43 | %28 | 69 |
| 9 | still | 41 | %27 | 48 |
| 10 | took | 35 | %23 | 51 |
| 11 | downstairs | 34 | %23 | 36 |
| 12 | them | 33 | %22 | 48 |
| 13 | each | 33 | %22 | 44 |
| 14 | gone | 33 | %22 | 38 |
| 15 | grey | 30 | %20 | 34 |
| 16 | glasses | 29 | %19 | 42 |
| 17 | looked | 27 | %18 | 49 |
| 18 | the | 27 | %18 | 40 |
| 19 | comes | 26 | %17 | 31 |
| 20 | dirty | 25 | %17 | 31 |

### 1083 · Thirty-One Mornings (A1 başlangıç, 254 kelime, 71 başlayan)
| # | Kelime | Kişi | Başlayanların yüzdesi | Dokunma |
|---|---|---|---|---|
| 1 | rock | 36 | %51 | 57 |
| 2 | count | 32 | %45 | 36 |
| 3 | path | 28 | %39 | 32 |
| 4 | grass | 23 | %32 | 47 |
| 5 | fox | 21 | %30 | 27 |
| 6 | whole | 20 | %28 | 26 |
| 7 | anyway | 18 | %25 | 23 |
| 8 | quietly | 18 | %25 | 20 |
| 9 | tries | 17 | %24 | 20 |
| 10 | stupid | 17 | %24 | 17 |
| 11 | forty | 16 | %23 | 21 |
| 12 | hands | 16 | %23 | 17 |
| 13 | stand | 16 | %23 | 16 |
| 14 | steps | 15 | %21 | 24 |
| 15 | sees | 15 | %21 | 21 |
| 16 | high | 15 | %21 | 18 |
| 17 | somewhere | 14 | %20 | 17 |
| 18 | boring | 14 | %20 | 15 |
| 19 | being | 13 | %18 | 16 |
| 20 | still | 13 | %18 | 13 |

### 1023 · Rabbit Island: Missing from the Map (eski adı: The Island Where Rabbits Won) (A2 başlangıç, 287 kelime, 118 başlayan)
| # | Kelime | Kişi | Başlayanların yüzdesi | Dokunma |
|---|---|---|---|---|
| 1 | ferries | 71 | %60 | 91 |
| 2 | purpose | 62 | %53 | 83 |
| 3 | concrete | 59 | %50 | 73 |
| 4 | multiplied | 57 | %48 | 84 |
| 5 | southern | 54 | %46 | 72 |
| 6 | removed | 54 | %46 | 68 |
| 7 | chase | 49 | %42 | 65 |
| 8 | erased | 48 | %41 | 58 |
| 9 | released | 45 | %38 | 57 |
| 10 | island | 42 | %36 | 63 |
| 11 | poison | 42 | %36 | 58 |
| 12 | standing | 40 | %34 | 54 |
| 13 | enemies | 39 | %33 | 57 |
| 14 | weapon | 39 | %33 | 52 |
| 15 | ferry | 37 | %31 | 40 |
| 16 | almost | 35 | %30 | 38 |
| 17 | former | 34 | %29 | 46 |
| 18 | bring | 32 | %27 | 50 |
| 19 | empty | 32 | %27 | 45 |
| 20 | simply | 30 | %25 | 41 |
