# 07 · Başlangıç metinlerinde balon ne gösteriyor (kuyruk 11)

**Tarih:** 28 Kasım 2026 · **Kaynak:** canlı veritabanı (salt okuma) ve sunucunun kendi çözüm hattı · yalnız müşteri hesapları, kişi bilgisi okunmadı.

## Nasıl ölçüldü
- **Dokunma sayısı:** `word_lookup` olayları (balonun açılması). Metne bağlama, olaydaki metin kimliğiyle (1.0.4), yoksa olayın düştüğü okuma oturumuyla; 01'deki yöntemle aynı.
- **Balonda görünen anlam:** olayda yalnız kelime var, gösterilen anlam yok. Bu yüzden anlam, uygulamanın gönderdiği isteğin aynısıyla yeniden hesaplandı (kelime + cümle + kelimenin cümledeki sırası), sunucunun salt okuma tanı komutuyla (`resolve-word --requests`). Cümleler metnin ses kliplerinden alındı; klipler sunucunun cümle bölmesiyle birebir.
- Kelime metinde birden çok yerde geçiyorsa **her geçiş ayrı çözüldü**. Dokunmanın hangi geçişte olduğu kayıtta yok.
- 4 metin × 20 kelime, 222 geçiş. İstenen kelimelerin hepsi zaten ilk 20'de.

## Sonuç
- **Anlam cümleye göre seçiliyor.** 222 geçişin 222'si bağlamla çözüldü. Kanıt: aynı kelime farklı cümlede farklı balon veriyor ("looked at" → bakmak, "looked up" → yukarı bakmak; "put" → koymak, "put … down" → bırakmak; "went" → gitmek, "went down" → aşağı inmek).
- **80 kelimeden 1'i yanlış, 1'i yarı yanlış, 7'si zayıf; kalanı doğru.**
  - Yanlış: 1083'te "one whole **second**" → "ikinci". Aynı cümledeki ilk "second" doğru ("saniye").
  - Yarı yanlış: 1023'te "multiplied" → "çoğalmak, çarpmak". İkinci anlam (matematik) bu cümlede yanlış.
- **Ekibin sorduğu kelimeler:** "still" (iki geçiş de "hâlâ"), "stood", "rock", "count", "hands", "steps" doğru. "flat", "above", "gone" zayıf (aşağıda).

## 916 Two Cups (A1)
| Kelime | Dokunma / kişi | Balon | Cümle | Değerlendirme |
|---|---|---|---|---|
| stairs | 151 / 80 | merdiven | The man who cleans our stairs comes at six. | doğru |
| bucket | 150 / 97 | kova | He has a blue bucket. | doğru |
| stood | 116 / 74 | ayakta durmak | I opened the door and stood on the stairs. · I stood there with the two glasses. | doğru (iki geçiş) |
| **flat** | 92 / 67 | **düz** | Outside, the sea was grey and flat. | **zayıf:** deniz için "durgun, dalgasız" |
| wet | 77 / 49 | ıslak | His shoes were wet. | doğru |
| cleans | 73 / 61 | temizlemek | The man who cleans our stairs… | doğru |
| pot | 68 / 60 | demlik | I put water in the pot. | doğru (çay demliği) |
| **above** | 67 / 55 | **üstünde** | He looked up at the stairs above him. | **zayıf:** "yukarıdaki" |
| still | 53 / 45 | hâlâ | The rain was still on them. · They were still dirty. | doğru (iki geçiş) |
| them | 53 / 38 | onları | The rain was still on them. | doğru |
| took | 53 / 36 | almak | He took the glass. (3 geçiş) | doğru |
| looked | 52 / 30 | bakmak · yukarı bakmak | looked at him · looked up at the stairs | doğru, kalıba göre |
| put | 49 / 25 | koymak · bırakmak | I put water… · He put the bucket down. | doğru, kalıba göre |
| the | 49 / 33 | (belirli tanımlık) | 16 geçiş | doğru |
| glasses | 47 / 33 | bardak | Two glasses this time. | doğru |
| each | 45 / 34 | birbirini, birbirine | next to each other | doğru (kalıp) |
| comes | 42 / 35 | gelmek | …comes at six. | doğru |
| went | 40 / 25 | gitmek · aşağı inmek | I went to the kitchen. · went down | doğru, kalıba göre |
| **gone** | 39 / 34 | **gitmek** | My bus was gone. | **zayıf:** "gitmiş (kaçırdım)"; mastar hâli cümleyi kurdurmuyor |
| down | 38 / 22 | bırakmak · aşağı inmek | put … down · went down | doğru (kalıp) |

## 1083 Thirty-One Mornings (A1)
| Kelime | Dokunma / kişi | Balon | Cümle | Değerlendirme |
|---|---|---|---|---|
| rock | 66 / 41 | kaya | The fox is always at the big rock. (4 geçiş) | doğru |
| grass | 48 / 24 | çimen | …in the grass… | doğru |
| count | 43 / 39 | saymak | Emma starts to count steps. | doğru |
| path | 36 / 31 | patika | She walks the same path every day. | doğru |
| fox | 33 / 23 | tilki | 8 geçiş | doğru |
| steps | 32 / 19 | adım | 8 geçiş ("forty steps from the rock") | doğru |
| forty | 29 / 21 | kırk | | doğru |
| the | 26 / 14 | (belirli tanımlık) | 22 geçiş | doğru |
| **whole** | 26 / 20 | **tüm** | …one second — one whole second — … | **zayıf:** "tam, koca (bir saniye)" |
| anyway | 23 / 18 | yine de | Rain comes one morning; she goes anyway. | doğru |
| sees | 23 / 17 | görmek | | doğru |
| tries | 23 / 19 | denemek | She tries. | doğru |
| runs | 22 / 13 | koşmak | 4 geçiş | doğru |
| forest | 20 / 14 | orman | | doğru |
| quietly | 20 / 18 | sessizce | | doğru |
| wet | 20 / 11 | ıslak | | doğru |
| at | 19 / 11 | (bir yer)de · bakmak | at the big rock · looks at her | doğru, kalıba göre |
| hands | 19 / 18 | el | No fast hands. | doğru |
| **second** | 19 / 12 | saniye · **ikinci** | The fox closes its eyes for one second — one whole **second** — … | **ikinci geçiş yanlış** |
| high | 18 / 15 | yüksek | Birds up high. | doğru |

## 1023 Rabbit Island (A2)
| Kelime | Dokunma / kişi | Balon | Cümle | Değerlendirme |
|---|---|---|---|---|
| ferries | 111 / 84 | feribot | Ferries bring visitors every day. | doğru |
| southern | 97 / 73 | güney | …in southern Japan… | doğru |
| purpose | 95 / 73 | kasten, bilerek | …removed from Japanese maps on purpose. | doğru (kalıp) |
| **multiplied** | 85 / 58 | **çoğalmak, çarpmak** | The rabbits multiplied with no natural enemies… | **yarı yanlış:** yalnız "çoğalmak" |
| concrete | 79 / 65 | beton | Their concrete walls… | doğru |
| removed | 75 / 58 | çıkarmak | | doğru |
| island | 72 / 47 | ada · Tavşan Adası | 9 geçiş | doğru |
| chase | 66 / 50 | kovalamak | | doğru |
| erased | 64 / 54 | silmek | The Island That Was Erased | doğru |
| poison | 64 / 48 | zehir | …made poison gas. | doğru |
| released | 61 / 47 | serbest bırakmak | | doğru |
| bring | 60 / 40 | getirmek | | doğru |
| standing | 59 / 45 | ayakta durmak | …the buildings were left standing. | doğru ("ayakta kaldı") |
| enemies | 57 / 39 | düşman | | doğru |
| weapon | 52 / 39 | silah | | doğru |
| visitors | 49 / 30 | ziyaretçi | | doğru |
| empty | 48 / 35 | boş | | doğru |
| **former** | 47 / 35 | **önceki** | …a former worker said… | **zayıf:** "eski (çalışan)" |
| almost | 45 / 41 | hemen hemen | | doğru |
| factory | 45 / 28 | fabrika | | doğru |

## 120 Why Penguins Can't Fly (B1)
| Kelime | Dokunma / kişi | Balon | Cümle | Değerlendirme |
|---|---|---|---|---|
| **trade** | 60 / 35 | **takas** | The Trade · …until the trade was complete. · …the trade looks like a bad deal. | **zayıf:** metindeki anlam "değiş tokuş, bedel" |
| wings | 59 / 31 | kanat | | doğru |
| ancestors | 56 / 41 | ata | | doğru |
| beating | 56 / 42 | çırpmak | wings beating like any bird | doğru |
| hollow | 46 / 34 | içi boş | hollow bones | doğru |
| useless | 42 / 32 | faydasız | | doğru |
| movement | 39 / 31 | hareket | | doğru |
| drops | 38 / 29 | düşmek | drops into the sea like a stone | doğru |
| bones | 37 / 20 | kemik | | doğru |
| flippers | 34 / 28 | yüzgeç | | doğru |
| flew | 33 / 27 | uçmak | | doğru |
| **solid** | 32 / 27 | **katı** | their bones grew heavy and solid | **zayıf:** "içi dolu, sağlam" ("hollow"un karşıtı) |
| jumps | 31 / 29 | atlamak | | doğru |
| tubes | 30 / 26 | boru | | doğru |
| bursts | 28 / 27 | ani hamle | with short bursts much faster | doğru |
| feathers | 28 / 23 | tüy | | doğru |
| tightly | 28 / 21 | sıkıca | | doğru |
| strange | 26 / 22 | garip | | doğru |
| the | 26 / 18 | (belirli tanımlık) | 31 geçiş | doğru |
| folds | 24 / 22 | katlanmak | A big wing folds in water | doğru |

## Anlam nereden geliyor (11.2)
Uygulama kelimeyi, cümlenin tamamını ve kelimenin cümledeki sırasını gönderiyor. Sunucu sırayla şunlara bakıyor: elle yazılmış bağlam karşılığı (`ContextGlosses`, vitrin metinleri için) → kurallı küçük kelimeler (ilgi zamirleri, "that", "like", kısaltmalar, iyelik) → özel isimler → kalıp ve deyimli fiiller ("look up", "on purpose") → sözlükteki anlamlar arasından, kelimenin o cümledeki türüne (isim, fiil, sıfat) göre seçim. Çözümleyici canlıda açık (`WordSenseResolver:Enabled`).

**Zayıflığın nedeni:** tür belli olduktan sonra, aynı türün anlamları arasında bağlama göre seçim yapılmıyor; sözlükteki ilk anlam geliyor ("flat" sıfat → "düz", "solid" sıfat → "katı"). "second"daki hata türün kendisinde: tire ile ayrılan ikinci geçiş sıra sayısı sanılıyor.

**Düzeltme yolu, kod gerektirmeden:** başlangıç metinleri vitrin olduğu için bağlam karşılığı yazmak (Santorini'de bugün yapılan yöntem). Bu dört metin için önerilen karşılıklar (9 kelime; "trade" üç geçişte, toplam 11 kayıt): flat → durgun, dalgasız · above → yukarıdaki · gone → gitmiş · whole → tam, koca · second (ikinci geçiş) → saniye · multiplied → çoğalmak · former → eski · trade (3 geçiş) → değiş tokuş, bedel · solid → içi dolu, sağlam. Yazmak canlıya yazma olduğu için Mehmet'in sözüyle.

## İlk metin kuralı (11.3)
**Kural (uygulama, `first_read_card.dart:57`):** okurun seviyesindeki açık metinlerin en kısası. Seviyede açık metin yoksa en yakın seviye; alt seviye tercih ediliyor (üst seviyeye kaçmak iki kat sayılıyor). Açık = başlangıç paketi ya da o gün günlük hakla açılmış metin. Ayrıntı: `08_baslangic_ikinci_adim.md`.

Bugün başlangıç paketinde üç metin var: A1'de 916 (217 kelime) ve 1083 (254), A2'de 1023 (287). B1 ve üstünde yok.

| Okurun seviyesi | İlk metni bugün |
|---|---|
| A1 | 916 Two Cups |
| A2 | 1023 Rabbit Island |
| **B1** | **1023 Rabbit Island** (B1'de açık metin yok; en yakın alt seviye A2) |
| B2, C1, C2 | 1023 Rabbit Island (aynı nedenle) |

İstisna: okur o gün günlük hakla kendi seviyesinde bir metin açtıysa, kart o metne döner.

**Bunun Santorini kararına etkisi:** Santorini başlangıç paketine alınırsa (182 kelime, A2) yalnız A2'nin değil **B1 ve üstündeki herkesin** de ilk metni Santorini olur. Rabbit Island'ın B1'e geçmesi ve başlangıç paketinde kalması hâlinde B1 okurun ilk metni Rabbit Island olur (seviyesinde tek açık metin).

Başlangıç yolculuğu (`starter-b1`: 1024 → 120 → 1019 → 1059) ayrı bir kart; ilk metin kartını belirlemiyor.
