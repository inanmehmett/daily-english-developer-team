# H3 – Soru bankaları: "Seviyeni yeniden ölç"

**Kaynak:** canlı veritabanı (`PlacementVocabItems`, `PlacementPassages`, `PlacementQuestions`), 22 Kasım 2026, salt okuma. "Seviyeni belgele" soruları ayrı dosyada: `../belge_sorulari.md`.

## Seviyeleri kim, neye göre verdi
- **Kelime taraması:** kelimeler bantlara **elle** seçildi. Kod notu: katalogdaki kelime seviyesi etiketleri güvenilir bulunmadığı için kullanılmadı (`DataAccess/Seed/PlacementVocabSeed.cs`). Bir sıklık listesine ya da dış ölçüte dayandığına dair kayıt yok.
- **Boşluk doldurma parçaları:** 8 Eylül 2026 teslimi (commit `e40044c`): 24 parça × 3 boşluk = 72 madde. Parçalar ve maddeler üretimle yazıldı (yapay zekâ destekli; commit imzası), seviyeler yazılırken verildi. Bir insan uzmanın seviye onayına dair kayıt yok. Mekanik denetimden geçti: doğru cevap parçada geçmiyor, boşluk sayısı soru sayısına eşit, doğru şık tek başına en uzun değil, doğru şıkkın konumu üçe eşit dağılıyor.
- **"Seviyeni belgele" soruları:** teslim dosyalarından (`Assessment/reading-v1-*.json`); her sorunun seviyesi dosyada yazılı, yine üretimle. 176 soru insan okumasından geçmedi (Mehmet'in kararıyla yayınlandı).
- **Gerçek kullanıcıyla kalibrasyon yapılmadı.** Aşağıdaki H4 dosyası ilk gerçek veriyi veriyor.

## 1. Kelime taraması havuzu: 60 gerçek + 35 sözde kelime
Bir turda her banttan 4 gerçek kelime (5 bant × 4 = 20) ve 10 sözde kelime, karışık sırayla: 30 kelime. Kullanıcı her biri için "biliyorum / bilmiyorum" der.

| Bant | Kelimeler |
|---|---|
| A1 | fish, bridge, window, chair, morning, salt, cheese, key, phone, bottle, sugar, green |
| A2 | towel, blanket, basket, tent, oven, wheel, shoulder, carpet, ceiling, hill, cough, gate |
| B1 | border, layer, pipe, profit, accent, corridor, cushion, ditch, kettle, rhythm, witness, damp |
| B2 | glacier, compromise, exile, errand, crumb, depot, fleet, inventory, murmur, blizzard, quarry, harness |
| C1 | rehearse, reverence, audacity, solemn, betrayal, verdict, plausible, confession, terminus, acquaintance, ingenuity, chagrin |
| Sözde (35) | blorn, tarpel, vindle, crelt, shomber, dworse, frample, gorbin, smulch, harvish, plinter, cravot, dreffle, yalter, cobrant, skelth, vurnip, bractle, nempid, florst, wibbon, jarnock, tuppel, drimble, scrandle, pelvish, thurnid, quilve, nodrant, vamble, chumble, delth, prunty, trisk, vanter |

## 2. Boşluk doldurma parçaları: 24 etkin parça
Havuzda 60 parça var; 36 tanesi eski tür (parça hakkında soru) ve **pasif**, sunulmuyor. Aşağıda yalnız etkin olanlar. Metindeki her `___` sırayla bir soruya karşılık gelir. Doğru şık **✔ kalın**.

### A1

#### Parça 50 · 44 kelime · ortalama cümle 5.5

> Emma goes to school on Monday. Her school is near the ___. She sees boats from her class. She has four lessons every day. Her favourite lesson is ___. She likes to sing. After school she plays with friends. She ___ home at four.

1. `s124` (gömülü boşluk) Her school is near the ___.: farm · **✔ lake** · park
2. `s125` (gömülü boşluk) Her favourite lesson is ___.: **✔ music** · maths · sport
3. `s126` (gömülü boşluk) She ___ home at four.: makes · **✔ comes** · opens

#### Parça 53 · 42 kelime · ortalama cümle 6

> Ali gets up at six every day. He drinks a glass of ___. Then he walks to the stop on the corner. The ___ comes at seven. He reads a book on it. Nobody talks. He likes the quiet ___ to work.

1. `s133` (gömülü boşluk) He drinks a glass of ___.: **✔ milk** · bread · rice
2. `s134` (gömülü boşluk) The ___ comes at seven.: shop · **✔ bus** · park
3. `s135` (gömülü boşluk) He likes the quiet ___ to work.: milk · bed · **✔ ride**

#### Parça 54 · 37 kelime · ortalama cümle 7.4

> Mia has a small cat. The cat is white and ___. It sleeps on the sofa all day. In the evening it ___ with a ball. Mia gives it food at eight, because then it is ___.

1. `s136` (gömülü boşluk) The cat is white and ___.: from · **✔ grey** · very
2. `s137` (gömülü boşluk) In the evening it ___ with a ball.: reads · cooks · **✔ plays**
3. `s138` (gömülü boşluk) Mia gives it food at eight, because then it is ___.: **✔ hungry** · yellow · asleep

#### Parça 55 · 45 kelime · ortalama cümle 7.5

> Tom gets up at seven. He makes tea and eats ___ in the kitchen. He has no car, so he ___ to work. His office is near the park. He likes the trees. There are no cars there, so it is ___ in the morning.

1. `s139` (gömülü boşluk) He makes tea and eats ___ in the kitchen.: **✔ toast** · water · juice
2. `s140` (gömülü boşluk) He has no car, so he ___ to work.: drives · **✔ walks** · swims
3. `s141` (gömülü boşluk) There are no cars there, so it is ___ in the morning.: noisy · busy · **✔ quiet**

#### Parça 56 · 39 kelime · ortalama cümle 5.57

> Anna is at the market. She wants apples and some ___ for breakfast. The apples are red and big. She ___ six. It is warm and fresh. She pays and says thank you. Then she goes home by ___.

1. `s142` (gömülü boşluk) She wants apples and some ___ for breakfast.: paper · **✔ bread** · shoes
2. `s143` (gömülü boşluk) She ___ six.: sells · makes · **✔ buys**
3. `s144` (gömülü boşluk) Then she goes home by ___.: **✔ bus** · cloud · door

#### Parça 57 · 44 kelime · ortalama cümle 4.89

> This is my family. My father is a ___. My mother is a teacher. I have one ___. Her name is Lily. She is ten. We live in a small flat. We have a ___. It is black and it sleeps on my bed.

1. `s145` (gömülü boşluk) My father is a ___.: baby · door · **✔ cook**
2. `s146` (gömülü boşluk) I have one ___.: **✔ sister** · garden · answer
3. `s147` (gömülü boşluk) We have a ___.: bus · **✔ cat** · cup

### A2

#### Parça 32 · 64 kelime · ortalama cümle 12.8

> Last summer we travelled to a small town by the ___. The weather was bad on the first day, so we ___ in the hotel. On the second day the sun came out and we walked along the beach. We ate fish at a little restaurant and talked for hours. We will go there again next year, because the town was quiet and ___.

1. `s70` (gömülü boşluk) a small town by the ___.: hill · **✔ sea** · road
2. `s71` (gömülü boşluk) so we ___ in the hotel.: cooked · danced · **✔ stayed**
3. `s72` (gömülü boşluk) the town was quiet and ___.: **✔ cheap** · noisy · large

#### Parça 33 · 58 kelime · ortalama cümle 11.6

> A new ___ moved into the flat above us last week. She is a teacher and she works at a school in the centre. On Saturday she ___ on our door and asked for some sugar. My mother invited her for tea, and they talked about the city. Next week we will help her to ___ the kitchen.

1. `s73` (gömülü boşluk) A new ___ moved into the flat above us.: colleague · assistant · **✔ neighbour**
2. `s74` (gömülü boşluk) On Saturday she ___ on our door.: **✔ knocked** · climbed · shouted
3. `s75` (gömülü boşluk) we will help her to ___ the kitchen.: enter · **✔ paint** · count

#### Parça 52 · 57 kelime · ortalama cümle 8.14

> Last night Maria came home late. She looked for her ___ in her bag, but they weren't there. She checked her coat and her pockets. Nothing. Then she ___: she left them on her desk at work. She called her friend Sam, who lives nearby. Sam had a ___ key, so Maria slept at home after all.

1. `s130` (gömülü boşluk) She looked for her ___ in her bag.: **✔ keys** · boots · coins
2. `s131` (gömülü boşluk) Then she ___: she left them on her desk.: understood · **✔ remembered** · complained
3. `s132` (gömülü boşluk) Sam had a ___ key.: broken · golden · **✔ spare**

#### Parça 58 · 52 kelime · ortalama cümle 8.67

> Yesterday Deniz lost the ___ of his flat. He looked for it in his bag and in his coat. Then he remembered the cafe near the office. He went back and ___ the waiter about it. The waiter smiled and gave it to him. Deniz was very ___ to have it back.

1. `s148` (gömülü boşluk) Yesterday Deniz lost the ___ of his flat.: **✔ key** · bill · map
2. `s149` (gömülü boşluk) He went back and ___ the waiter about it.: hugged · **✔ asked** · phoned
3. `s150` (gömülü boşluk) Deniz was very ___ to have it back.: late · tired · **✔ glad**

#### Parça 59 · 54 kelime · ortalama cümle 10.8

> Next Saturday, Ben and his cousin are going to the ___. They will take the early train, because the beach is ___ after eleven. Ben wants to swim, but his cousin doesn't like cold water. So they made a deal. They swim in the morning and have a long ___ in a fish restaurant.

1. `s151` (gömülü boşluk) Ben and his cousin are going to the ___.: forest · **✔ coast** · museum
2. `s152` (gömülü boşluk) the beach is ___ after eleven.: empty · closed · **✔ busy**
3. `s153` (gömülü boşluk) have a long ___ in a fish restaurant.: **✔ lunch** · train · beach

#### Parça 60 · 56 kelime · ortalama cümle 9.33

> Leo started a new job at a bookshop two weeks ago. At first he was ___, because he didn't know where anything was. Customers asked for books and he had to look everywhere. Now he knows where every book is on the ___. Yesterday a woman ___ him for finding a book quickly. He felt proud.

1. `s154` (gömülü boşluk) At first he was ___.: famous · patient · **✔ nervous**
2. `s155` (gömülü boşluk) Now he knows where every book is on the ___.: **✔ shelves** · prices · streets
3. `s156` (gömülü boşluk) Yesterday a woman ___ him.: followed · **✔ thanked** · reminded

### B1

#### Parça 37 · 58 kelime · ortalama cümle 14.5

> The bookshop on the corner has been open since my grandfather was a boy. Its ___, who knows every customer by name, keeps a list of the books they love. If you ask him for a ___, he will disappear behind the shelves for a minute. He always comes back with something you did not know you ___.

1. `s85` (gömülü boşluk) Its ___, who knows every customer by name.: **✔ owner** · reader · author
2. `s86` (gömülü boşluk) If you ask him for a ___.: explanation · **✔ suggestion** · translation
3. `s87` (gömülü boşluk) something you did not know you ___.: ordered · returned · **✔ wanted**

#### Parça 38 · 58 kelime · ortalama cümle 14.5

> When Selin moved to a new city, she had not expected the ___ of the evenings. She had lived in a noisy street for years, and she ___ the sound of traffic. If she had known, she would have chosen a flat near the centre. After a few months, however, the quiet became the thing she liked ___.

1. `s88` (gömülü boşluk) she had not expected the ___ of the evenings.: comfort · **✔ silence** · expense
2. `s89` (gömülü boşluk) she ___ the sound of traffic.: hated · feared · **✔ missed**
3. `s90` (gömülü boşluk) the quiet became the thing she liked ___.: **✔ most** · less · least

#### Parça 39 · 58 kelime · ortalama cümle 14.5

> Murat has been working at the animal ___ every Saturday since he finished university. The dogs, which arrive frightened and thin, learn to ___ him within a few weeks. If a family wants to adopt one, he asks them careful questions about their home. He would rather wait a month than send an animal to the ___ place.

1. `s91` (gömülü boşluk) Murat has been working at the animal ___.: hospital · market · **✔ shelter**
2. `s92` (gömülü boşluk) learn to ___ him within a few weeks.: **✔ trust** · avoid · follow
3. `s93` (gömülü boşluk) than send an animal to the ___ place.: quiet · **✔ wrong** · usual

#### Parça 40 · 62 kelime · ortalama cümle 12.4

> When Priya decided to spend a week without her phone, her friends laughed and said she wouldn't ___ two days. She did, but not in the way she expected. The first evenings were long and strangely ___. By Thursday she had finished a book she'd carried around for months. She had also noticed things on her street that she'd ___ for years.

1. `s94` (gömülü boşluk) she wouldn't ___ two days.: **✔ last** · mind · wait
2. `s95` (gömülü boşluk) The first evenings were long and strangely ___.: short · **✔ empty** · loud
3. `s96` (gömülü boşluk) things on her street that she'd ___ for years.: counted · repeated · **✔ ignored**

#### Parça 41 · 58 kelime · ortalama cümle 9.67

> Daniel's bakery had been open for a year. Then the supermarket across the road began selling fresh bread. He couldn't ___ on price, so he stopped trying. Instead, he put a table outside and learned his regular customers' ___. Sales didn't rise much, but nobody ___. By spring the supermarket had quietly moved its bread to the back.

1. `s97` (gömülü boşluk) He couldn't ___ on price.: decide · **✔ compete** · survive
2. `s98` (gömülü boşluk) learned his regular customers' ___.: orders · faults · **✔ names**
3. `s99` (gömülü boşluk) Sales didn't rise much, but nobody ___.: **✔ left** · paid · asked

#### Parça 42 · 58 kelime · ortalama cümle 9.67

> Most people learn to swim as children, so Omar never told anyone he ___. At thirty-four he finally signed up for adult lessons. He half expected to be the ___ person there. He wasn't. The class had a retired nurse, two students and a sailor. By the sixth week Omar could ___ the pool without touching the bottom.

1. `s100` (gömülü boşluk) Omar never told anyone he ___.: wouldn't · shouldn't · **✔ couldn't**
2. `s101` (gömülü boşluk) He half expected to be the ___ person there.: **✔ oldest** · fittest · calmest
3. `s102` (gömülü boşluk) Omar could ___ the pool.: clean · **✔ cross** · close

### B2

#### Parça 43 · 66 kelime · ortalama cümle 16.5

> The council's decision to ban late-night deliveries was announced as a ___ for residents, and for a few weeks it felt like one. Streets that had rattled with lorries at three in the morning fell silent. What the announcement did not mention was that the same deliveries would now arrive at seven, ___ when the school run began. Complaints did not fall; they simply changed ___.

1. `s103` (gömülü boşluk) was announced as a ___ for residents.: **✔ victory** · warning · proposal
2. `s104` (gömülü boşluk) at seven, ___ when the school run began.: similarly · **✔ precisely** · generally
3. `s105` (gömülü boşluk) they simply changed ___.: opinion · purpose · **✔ address**

#### Parça 44 · 70 kelime · ortalama cümle 17.5

> It was widely ___ that handwriting would disappear within a generation, and in offices it very nearly has. Yet stationery shops report that sales of notebooks have risen for six ___ years, driven not by older customers but by people in their twenties. Asked why, they rarely mention nostalgia. More often they describe something closer to ___: a page that does not update, notify, or suggest what to write next.

1. `s106` (gömülü boşluk) It was widely ___ that handwriting would disappear.: forgotten · **✔ predicted** · concluded
2. `s107` (gömülü boşluk) risen for six ___ years.: challenging · predictable · **✔ consecutive**
3. `s108` (gömülü boşluk) something closer to ___: a page that does not update.: **✔ relief** · regret · wonder

#### Parça 45 · 74 kelime · ortalama cümle 18.5

> The map in the museum's back corridor is wrong in almost every detail, which is exactly why the curator ___ to move it. It was drawn in 1702 by a surveyor who had never left the capital. It places the river a mile east of where it runs, and visitors who notice tend to ___. The curator's point is that the map records not the land but what the city once ___ about it.

1. `s109` (gömülü boşluk) which is exactly why the curator ___ to move it.: agreed · offered · **✔ refused**
2. `s110` (gömülü boşluk) visitors who notice tend to ___.: **✔ laugh** · leave · argue
3. `s111` (gömülü boşluk) what the city once ___ about it.: decided · **✔ believed** · reported

#### Parça 46 · 67 kelime · ortalama cümle 16.75

> The bridge, which was built more than a century ago by engineers who had never seen the valley, still ___ the morning traffic without complaint. Local officials announced last year that it would be closed for repairs, but the work has been ___ twice since then. No one has explained why. Residents say that the delay, although irritating, is ___ to the noise of a building site.

1. `s112` (gömülü boşluk) still ___ the morning traffic.: **✔ carries** · blocks · reduces
2. `s113` (gömülü boşluk) the work has been ___ twice since then.: completed · **✔ postponed** · inspected
3. `s114` (gömülü boşluk) the delay is ___ to the noise of a building site.: comparable · unrelated · **✔ preferable**

#### Parça 47 · 64 kelime · ortalama cümle 16

> When the journalist asked her whether she ___ leaving the company, she replied that the question was less simple than it sounded. She explained that the decision, taken during a difficult winter, had ___ her to work on projects nobody else would fund. The room went quiet. What she did not say, though it was obvious to everyone, was that she ___ her colleagues.

1. `s115` (gömülü boşluk) asked her whether she ___ leaving the company.: announced · **✔ regretted** · confirmed
2. `s116` (gömülü boşluk) had ___ her to work on projects.: asked · urged · **✔ freed**
3. `s117` (gömülü boşluk) was that she ___ her colleagues.: **✔ missed** · blamed · warned

#### Parça 48 · 59 kelime · ortalama cümle 19.67

> The results, surprising as they were, had been ___ by a graduate student whose paper the committee rejected two years earlier. Had the panel read it more carefully, the laboratory might have ___ a considerable amount of money. The student, now working abroad, says that she bears no ___, although her supervisor admits that the episode was badly handled.

1. `s118` (gömülü boşluk) had been ___ by a graduate student.: rejected · requested · **✔ predicted**
2. `s119` (gömülü boşluk) the laboratory might have ___ a considerable amount of money.: **✔ saved** · spent · owed
3. `s120` (gömülü boşluk) she bears no ___.: burden · **✔ grudge** · excuse

