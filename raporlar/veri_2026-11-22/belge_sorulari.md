# "Seviyeni belgele": 176 sorunun tam dökümü

**Tarih:** 21 Kasım 2026 gece · **Kimden:** editör · **Kime:** Charles, Paul
**Kaynak:** canlı veritabanı (`AssessmentItems`, `AssessmentStimuli`), salt okuma. Hepsi etkin (176/176).

## Nasıl okunur
- Doğru şık **✔ kalın** yazıldı.
- **⟨…⟩** işareti: soru kökü "…" ile bitiyor (tamamlama sorusu). Toplam **29** soru: ısınmada 4, metin sorularında 21, sınır adımında 4.
- Her sorunun altında anahtarı, seviyesi ve türü; varsa metindeki kanıt ve Türkçe gerekçe.
- Şıkların buradaki sırası kayıttaki sıradır. Bir metnin dört sorusu ekranda karışık sırayla geliyor (`AssessmentService.cs:552`); şıkların karıştırılıp karıştırılmadığına bakmadım.
- **Düzeltme:** bilgi cevapları raporunda "176 sorunun 41'i '…' ile bitiyor" yazmıştım. Doğrusu: 41 soruda "…" **geçiyor**, bunların 29'u "…" ile **bitiyor** (tamamlama sorusu). Kalan 12'sinde "…" yalnız alıntının içinde ("… while a white surface reflects most of it." gibi) ve soru tam cümle.

| Bölüm | Soru | "…" ile biten |
|---|---|---|
| 1. Isınma (yönlendirme) | 24 | 4 |
| 2. Metin soruları | 128 | 21 |
| 3. Sınır adımı | 24 | 4 |
| **Toplam** | **176** | **29** |

## 1. Isınma (yönlendirme): kısa tek sorular, 6 soru tek sayfada

### A1

**1. Sign: "Shop open 9:00–17:00, Monday to Saturday." When is the shop closed?**  
`rv1-r-a1-01` · A1 · Ayrıntı

- **✔ On Sunday**
- On Monday
- On Friday
- On Saturday

Kanıt: "Monday to Saturday"  Gerekçe: Pazartesiden cumartesiye açık; pazar kapalı.

**2. Note: "Mum, I'm at Ben's house. I'm home at six. Love, Sam." Where is Sam now?**  
`rv1-r-a1-02` · A1 · Ayrıntı

- At his home
- **✔ At Ben's house**
- At his school
- At the station

Kanıt: "I'm at Ben's house."  Gerekçe: Sam şu an Ben'in evinde; altıda eve dönecek.

**3. "The water is very hot. Don't drink it now." "Hot" is the opposite of …** ⟨…⟩  
`rv1-r-a1-03` · A1 · Bağlamda kelime

- big
- new
- **✔ cold**
- fast

Kanıt: "The water is very hot."  Gerekçe: "Hot" sıcak; zıttı "cold" soğuk.

**4. "This is Maria. She is my teacher." Who is "she"?**  
`rv1-r-a1-04` · A1 · Bağlaşıklık

- My mother
- My friend
- My sister
- **✔ Maria**

Kanıt: "This is Maria. She is my teacher."  Gerekçe: "She" bir önceki cümledeki Maria'yı gösteriyor.

**5. Card: "Happy birthday, Lucy! You are seven today! Love, Grandma." What is the card for?**  
`rv1-r-a1-05` · A1 · -

- **✔ A birthday**
- A new house
- A wedding
- A new job

Kanıt: "Happy birthday, Lucy!"  Gerekçe: Kart doğum günü için.

**6. "The bus to the airport is number 12. It comes every twenty minutes." Which bus goes to the airport?**  
`rv1-r-a1-06` · A1 · Ayrıntı

- Number 20
- **✔ Number 12**
- Number 2
- Number 10

Kanıt: "The bus to the airport is number 12."  Gerekçe: Havaalanı otobüsü 12 numara; yirmi dakikada bir geliyor.

### A2

**7. "Sorry, I missed the train, so I'll be about twenty minutes late. Start without me!" What does the writer want?**  
`rv1-r-a2-01` · A2 · Ayrıntı

- **✔ The others should start now**
- The others should wait for her
- The meeting should stop
- Someone should call her

Kanıt: "Start without me!"  Gerekçe: Geç kalacak; başlamalarını istiyor.

**8. "We've sold all the tickets for Saturday. There are a few left for Sunday." What can you do?**  
`rv1-r-a2-02` · A2 · Çıkarım

- Buy a ticket for Saturday
- **✔ Buy a ticket for Sunday**
- Get a free ticket
- Buy tickets for both days

Kanıt: "There are a few left for Sunday."  Gerekçe: Cumartesi biletleri bitti; yalnız pazar için kaldı.

**9. "The road is closed, so the bus will take a different route." "Route" means …** ⟨…⟩  
`rv1-r-a2-03` · A2 · Bağlamda kelime

- ticket
- driver
- **✔ way to go**
- timetable

Kanıt: "the bus will take a different route"  Gerekçe: "Route" güzergâh, gidilen yol.

**10. "My sister gave me a book and a scarf. I love it, because it is warm." What does the writer love?**  
`rv1-r-a2-04` · A2 · Bağlaşıklık

- The book
- Her sister
- The day
- **✔ The scarf**

Kanıt: "I love it, because it is warm."  Gerekçe: Sıcak olan atkı; "it" atkıyı gösteriyor.

**11. "Lost: a brown wallet near the station on Monday. It has photos of my children inside. Please call 0712 555 300." Why was this written?**  
`rv1-r-a2-05` · A2 · -

- **✔ To find something that is lost**
- To sell a brown wallet
- To show some family photos
- To ask for a taxi to the station

Kanıt: "Lost: a brown wallet near the station on Monday."  Gerekçe: Kaybolan cüzdanı bulmak için yazılmış.

**12. "The museum is free on the first Sunday of every month. On other days, tickets cost eight pounds." When is it free?**  
`rv1-r-a2-06` · A2 · Ayrıntı

- Every Sunday
- **✔ One Sunday a month**
- Every day in May
- On Mondays and Fridays

Kanıt: "The museum is free on the first Sunday of every month."  Gerekçe: Her ayın ilk pazarı ücretsiz; yani ayda bir pazar.

### B1

**13. "I'd love to come to your party, but I've promised to help my brother move house that weekend." What will the writer do?**  
`rv1-r-b1-01` · B1 · Çıkarım

- Go to the party
- **✔ Help her brother**
- Move to a new house
- Have a party at home

Kanıt: "I've promised to help my brother move house that weekend"  Gerekçe: Partiye gelemiyor; kardeşine taşınmada yardım edecek.

**14. "The concert was postponed because the singer was ill. It will now take place next month." "Postponed" means …** ⟨…⟩  
`rv1-r-b1-02` · B1 · Bağlamda kelime

- cancelled for ever
- stopped in the middle
- **✔ moved to a later date**
- moved to a new city

Kanıt: "It will now take place next month."  Gerekçe: "Postpone" ertelemek; konser gelecek ay yapılacak.

**15. "Customers who spend over £50 get free delivery. Orders under £50 cost £4.99 to deliver." Sam spends £45. What does he pay for delivery?**  
`rv1-r-b1-03` · B1 · Ayrıntı

- Nothing
- **✔ £4.99**
- £50
- £45

Kanıt: "Orders under £50 cost £4.99 to deliver."  Gerekçe: 45 pound 50'nin altında; teslimat 4,99.

**16. "From Monday, all visitors must sign in at reception and wear a badge. This is to keep staff and patients safe." What is the message about?**  
`rv1-r-b1-04` · B1 · -

- New opening hours for patients
- A change in hospital staff
- Where to park at the hospital
- **✔ A new safety rule for visitors**

Kanıt: "all visitors must sign in at reception and wear a badge"  Gerekçe: Ziyaretçiler için yeni bir güvenlik kuralı.

**17. "Maria lent her laptop to Tom because his was broken. He gave it back on Friday." What did Tom give back?**  
`rv1-r-b1-05` · B1 · Bağlaşıklık

- **✔ Maria's laptop**
- His own laptop
- A new laptop
- Maria's phone

Kanıt: "Maria lent her laptop to Tom because his was broken. He gave it back on Friday."  Gerekçe: "It" Maria'nın ödünç verdiği bilgisayarı gösteriyor.

**18. "Jake has been learning Japanese for six months, and next week he is moving to Tokyo for work." Why is Jake probably learning Japanese?**  
`rv1-r-b1-06` · B1 · Çıkarım

- For a school exam
- Because his friend is Japanese
- **✔ For his new job in Japan**
- To read Japanese comics

Kanıt: "next week he is moving to Tokyo for work"  Gerekçe: İş için Tokyo'ya taşınıyor.

### B2

**19. "Had I known the traffic would be this bad, I would have taken the train." What does the speaker mean?**  
`rv1-r-b2-01` · B2 · Çıkarım

- **✔ They drove and regret it**
- They took the train
- They prefer driving to trains
- The train was also delayed

Kanıt: "Had I known the traffic would be this bad, I would have taken the train."  Gerekçe: Trafiği bilseydi trene binerdi: arabayla gitti ve pişman.

**20. "The new manager was reluctant to change the schedule, but eventually agreed after several complaints." "Reluctant" means …** ⟨…⟩  
`rv1-r-b2-02` · B2 · Bağlamda kelime

- eager
- **✔ unwilling**
- unable
- frightened

Kanıt: "but eventually agreed after several complaints"  Gerekçe: "Reluctant" isteksiz; sonunda şikâyetlerle kabul etti.

**21. "Oh, wonderful. The printer has broken again, five minutes before the deadline." What is the speaker's tone?**  
`rv1-r-b2-03` · B2 · Amaç ve ton

- Grateful
- Encouraging
- **✔ Sarcastic**
- Relieved

Kanıt: "The printer has broken again, five minutes before the deadline."  Gerekçe: "Wonderful" kötü bir durum için söyleniyor: alaycı.

**22. "The study compared two groups of patients. The former received the new drug, while the latter were given a placebo." Who received the new drug?**  
`rv1-r-b2-04` · B2 · Bağlaşıklık

- The second group
- Both groups
- Neither group
- **✔ The first group**

Kanıt: "The former received the new drug"  Gerekçe: "The former" ilk anılan grubu gösterir.

**23. "Although electric cars produce no exhaust, building their batteries requires mining that can damage the environment. Their overall impact depends heavily on how the electricity is produced." What is the main point?**  
`rv1-r-b2-05` · B2 · -

- **✔ Electric cars are not automatically clean**
- Electric cars should be banned
- Batteries are cheap to produce
- Mining is the main cause of air pollution

Kanıt: "Their overall impact depends heavily on how the electricity is produced."  Gerekçe: Elektrikli araçlar kendiliğinden temiz değil; etkisi koşullara bağlı.

**24. "Applications received after 5 p.m. on Friday will be considered only if places remain." What happens to a late application?**  
`rv1-r-b2-06` · B2 · Ayrıntı

- It is rejected immediately
- It is accepted without question
- **✔ It may be considered later**
- It moves to the top

Kanıt: "will be considered only if places remain"  Gerekçe: Geç başvuru yer kalırsa değerlendirilir.

## 2. Metin soruları: 32 metin, her metinde 4 soru

### A1

#### Metin `rv1-a1-t01` · message · 38 kelime

> Hi Tom, I am at the shop now. I want to make a cake tonight. Do we have eggs at home? I can see milk and sugar here, but I can't find butter. Please call me. Thanks, Anna

**25. Why does Anna write to Tom?**  
`rv1-a1-t01-q1` · A1 · -

- **✔ To ask about eggs at home**
- To invite him to her party
- To say that she is ill
- To tell him about a film

Kanıt: "Do we have eggs at home?"  Gerekçe: Anna kek için evde yumurta olup olmadığını soruyor.

**26. What can't Anna find in the shop?**  
`rv1-a1-t01-q2` · A1 · Ayrıntı

- Milk
- **✔ Butter**
- Sugar
- Coffee

Kanıt: "but I can't find butter"  Gerekçe: Süt ve şekeri görüyor, tereyağını bulamıyor.

**27. In the message, "tonight" means …** ⟨…⟩  
`rv1-a1-t01-q3` · A1 · Bağlamda kelime

- last night
- next week
- **✔ this evening**
- this morning

Kanıt: "I want to make a cake tonight."  Gerekçe: "Tonight" bu akşam demek.

**28. "Please call me." Who is "me"?**  
`rv1-a1-t01-q4` · A1 · Bağlaşıklık

- Tom
- The shop
- A friend
- **✔ Anna**

Kanıt: "Please call me. Thanks, Anna"  Gerekçe: Mesajı yazan Anna; "me" onu gösteriyor.

#### Metin `rv1-a1-t02` · notice · 40 kelime

> CITY POOL. Open every day from eight in the morning to eight in the evening. Children under ten must swim with an adult. Lifeguards are here all day. They can help you. On Mondays the pool closes at two o'clock.

**29. What is this notice about?**  
`rv1-a1-t02-q1` · A1 · -

- **✔ The pool rules**
- A new sports shop
- A swimming lesson
- A job at the pool

Kanıt: "Children under ten must swim with an adult."  Gerekçe: Duyuru havuzun saatlerini ve kurallarını anlatıyor.

**30. When does the pool close on Monday?**  
`rv1-a1-t02-q2` · A1 · Ayrıntı

- At eight
- **✔ At two**
- At ten
- At seven

Kanıt: "On Mondays the pool closes at two o'clock."  Gerekçe: Pazartesi saat ikide kapanıyor.

**31. In the notice, "an adult" means …** ⟨…⟩  
`rv1-a1-t02-q3` · A1 · Bağlamda kelime

- a person under ten
- a pool worker
- **✔ a grown-up person**
- a good swimmer

Kanıt: "Children under ten must swim with an adult."  Gerekçe: "Adult" yetişkin demek; on yaş altı çocuk bunun tersi.

**32. "They can help you." Who are "they"?**  
`rv1-a1-t02-q4` · A1 · Bağlaşıklık

- Small children
- The pool owners
- The adults
- **✔ The lifeguards**

Kanıt: "Lifeguards are here all day. They can help you."  Gerekçe: "They" bir önceki cümledeki cankurtaranları gösteriyor.

#### Metin `rv1-a1-t03` · narrative · 50 kelime

> My name is Kerem. I live in a small flat with my sister, Elif. She is a nurse and she works at night. I work in a bank in the day. We are not at home together very much. On Sundays we cook lunch and eat it in the park.

**33. What is the text about?**  
`rv1-a1-t03-q1` · A1 · -

- **✔ Kerem and his sister's life**
- Kerem's new job at a hospital
- A long trip to a big city
- Elif's school and her friends

Kanıt: "I live in a small flat with my sister, Elif."  Gerekçe: Metin Kerem ile kız kardeşinin günlük hayatını anlatıyor.

**34. When does Elif work?**  
`rv1-a1-t03-q2` · A1 · Ayrıntı

- In the morning
- **✔ At night**
- On Sundays
- In the day

Kanıt: "She is a nurse and she works at night."  Gerekçe: Elif hemşire ve geceleri çalışıyor.

**35. In the text, "together" means …** ⟨…⟩  
`rv1-a1-t03-q3` · A1 · Bağlamda kelime

- at the bank
- in different rooms
- **✔ with each other**
- on their own

Kanıt: "We are not at home together very much."  Gerekçe: "Together" birlikte demek.

**36. "She is a nurse." Who is "she"?**  
`rv1-a1-t03-q4` · A1 · Bağlaşıklık

- Kerem
- His mum
- **✔ Elif**
- A doctor

Kanıt: "with my sister, Elif. She is a nurse"  Gerekçe: "She" bir önceki cümlede adı geçen Elif'i gösteriyor.

#### Metin `rv1-a1-t04` · menu · 38 kelime

> SUN CAFE. Breakfast from seven to eleven. Eggs and bread: four pounds. Big breakfast: seven pounds. Tea or coffee: two pounds. Fresh orange juice: three pounds. It is free for children under five. We are closed on Tuesday.

**37. What can you read here?**  
`rv1-a1-t04-q1` · A1 · -

- **✔ Food and prices at a cafe**
- Times of the city trains
- A list of school lessons
- A shop for children's toys

Kanıt: "Eggs and bread: four pounds."  Gerekçe: Metin bir kafenin yemek ve fiyat listesi.

**38. How much is a big breakfast?**  
`rv1-a1-t04-q2` · A1 · Ayrıntı

- Four pounds
- **✔ Seven pounds**
- Three pounds
- Two pounds

Kanıt: "Big breakfast: seven pounds."  Gerekçe: Büyük kahvaltı yedi pound.

**39. "It is free for children under five." "Free" means …** ⟨…⟩  
`rv1-a1-t04-q3` · A1 · Bağlamda kelime

- very small
- very hot
- **✔ no money**
- not open

Kanıt: "It is free for children under five."  Gerekçe: "Free" burada ücretsiz demek.

**40. "We are closed on Tuesday." Who are "we"?**  
`rv1-a1-t04-q4` · A1 · Bağlaşıklık

- The children
- The customers
- The city
- **✔ The cafe**

Kanıt: "We are closed on Tuesday."  Gerekçe: Menüyü yazan kafe kendinden "we" diye söz ediyor.

#### Metin `rv1-a1-t05` · email · 44 kelime

> Dear Mr Brown, I am sorry, but my son Ali is ill today. He has a cold and a bad headache. He can't come to school. I think he can come back on Thursday. Can you send me his homework? Thank you. Sara Demir

**41. Why does Sara write this email?**  
`rv1-a1-t05-q1` · A1 · -

- **✔ Her son is not well**
- Her son has a new teacher
- She wants a job at school
- She lost her son's bag

Kanıt: "my son Ali is ill today"  Gerekçe: Oğlu hasta olduğu için okula gelemeyeceğini bildiriyor.

**42. When can Ali go back to school?**  
`rv1-a1-t05-q2` · A1 · Ayrıntı

- This morning
- **✔ On Thursday**
- On Wednesday
- Next week

Kanıt: "I think he can come back on Thursday."  Gerekçe: Perşembe dönebileceğini düşünüyor.

**43. In the email, "ill" means …** ⟨…⟩  
`rv1-a1-t05-q3` · A1 · Bağlamda kelime

- late
- happy
- **✔ sick**
- busy

Kanıt: "my son Ali is ill today"  Gerekçe: "Ill" hasta demek.

**44. "Can you send me his homework?" Whose homework?**  
`rv1-a1-t05-q4` · A1 · Bağlaşıklık

- Mr Brown's
- Sara's
- Tom's
- **✔ Ali's**

Kanıt: "Can you send me his homework?"  Gerekçe: "His" e-postada sözü edilen Ali'yi gösteriyor.

#### Metin `rv1-a1-t06` · advert · 42 kelime

> Room for rent. A big room in a quiet house near the station. It has a bed, a desk and a window over the garden. The kitchen is new. No pets, please. Two hundred pounds a month. Call Mrs Hill after six.

**45. What is this advert for?**  
`rv1-a1-t06-q1` · A1 · -

- **✔ A room you can live in**
- A new kitchen for sale
- A job at the station
- A pet that needs a home

Kanıt: "Room for rent."  Gerekçe: İlan kiralık bir oda için.

**46. What can you see from the window?**  
`rv1-a1-t06-q2` · A1 · Ayrıntı

- The station
- **✔ The garden**
- The kitchen
- The street

Kanıt: "a window over the garden"  Gerekçe: Pencere bahçeye bakıyor.

**47. In the advert, "quiet" means …** ⟨…⟩  
`rv1-a1-t06-q3` · A1 · Bağlamda kelime

- very big
- very old
- **✔ not noisy**
- not cheap

Kanıt: "a quiet house near the station"  Gerekçe: "Quiet" sessiz, gürültüsüz demek.

**48. "It has a bed, a desk and a window." What is "it"?**  
`rv1-a1-t06-q4` · A1 · Bağlaşıklık

- The station
- The garden
- The kitchen
- **✔ The room**

Kanıt: "A big room in a quiet house near the station. It has a bed"  Gerekçe: "It" kiralık odayı gösteriyor.

#### Metin `rv1-a1-t07` · narrative · 52 kelime

> Every Saturday my grandfather and I go to the river. He likes to fish, but I like to read. We take sandwiches and hot tea. He talks to the fish and I laugh. We go home at four. He never takes a fish home. He puts them all back in the water.

**49. What is the text about?**  
`rv1-a1-t07-q1` · A1 · -

- **✔ Saturdays at the river with Grandad**
- How to cook fresh fish at home tonight
- A school trip to the river in summer
- A new book about animals and birds

Kanıt: "Every Saturday my grandfather and I go to the river."  Gerekçe: Metin büyükbabayla nehirde geçen cumartesileri anlatıyor.

**50. What does the writer like to do at the river?**  
`rv1-a1-t07-q2` · A1 · Ayrıntı

- Fish
- **✔ Read**
- Swim
- Sleep

Kanıt: "He likes to fish, but I like to read."  Gerekçe: Yazar okumayı seviyor; balık tutan büyükbaba.

**51. "He never takes a fish home." "Never" means …** ⟨…⟩  
`rv1-a1-t07-q3` · A1 · Bağlamda kelime

- one time
- every day
- **✔ not at any time**
- on some days only

Kanıt: "He never takes a fish home."  Gerekçe: "Never" hiçbir zaman demek; balıkları suya geri bırakıyor.

**52. "He puts them all back." What are "them"?**  
`rv1-a1-t07-q4` · A1 · Bağlaşıklık

- The sandwiches
- The books
- The cups
- **✔ The fish**

Kanıt: "He puts them all back in the water."  Gerekçe: "Them" tutulan balıkları gösteriyor.

#### Metin `rv1-a1-t08` · message · 44 kelime

> Hello class! The museum trip is on Friday. Please come to school at eight. The bus leaves at half past eight. Bring a coat, because it is cold. You need some money for lunch. We come back at three. See you there! Ms Green

**53. What is the message about?**  
`rv1-a1-t08-q1` · A1 · -

- **✔ A class visit to a museum**
- A new teacher at school
- A party on a Friday night
- A test in the classroom

Kanıt: "The museum trip is on Friday."  Gerekçe: Mesaj sınıfın müze gezisini anlatıyor.

**54. What time does the bus leave?**  
`rv1-a1-t08-q2` · A1 · Ayrıntı

- At ten past eight
- **✔ At half past eight**
- At ten past three
- At half past three

Kanıt: "The bus leaves at half past eight."  Gerekçe: Otobüs sekiz buçukta kalkıyor; sekizde okulda olunmalı.

**55. "The bus leaves at half past eight." "Leaves" means …** ⟨…⟩  
`rv1-a1-t08-q3` · A1 · Bağlamda kelime

- comes back
- stops
- **✔ goes away**
- waits

Kanıt: "The bus leaves at half past eight."  Gerekçe: "Leave" ayrılmak, yola çıkmak demek.

**56. "Bring a coat, because it is cold." What is cold?**  
`rv1-a1-t08-q4` · A1 · Bağlaşıklık

- The bus
- The museum
- The classroom
- **✔ The weather**

Kanıt: "Bring a coat, because it is cold."  Gerekçe: "It is cold" havanın soğuk olduğunu söylüyor; bu yüzden mont getirilmeli.

### A2

#### Metin `rv1-a2-t01` · email · 73 kelime

> Hi Jess, thanks for your email. I'm sorry I didn't answer sooner, but we moved to the new flat last week and the internet only started working yesterday. The flat is smaller than our old one, but it's much closer to my office, so I can walk to work now. There's a nice bakery downstairs too, which is dangerous! Are you free next Saturday? Come for lunch and see the place. Love, Mia

**57. What is Mia's email mainly about?**  
`rv1-a2-t01-q1` · A2 · -

- **✔ Her new home and an invitation**
- A problem with her new job
- A holiday she wants to take with Jess
- A birthday party for Jess

Kanıt: "we moved to the new flat last week"  Gerekçe: Mia yeni evini anlatıyor ve Jess'i öğle yemeğine çağırıyor.

**58. Why didn't Mia answer sooner?**  
`rv1-a2-t01-q2` · A2 · Ayrıntı

- She was ill all week
- **✔ Her internet did not work**
- She was on holiday
- She lost Jess's email address

Kanıt: "the internet only started working yesterday"  Gerekçe: Yeni evde internet ancak dün çalışmaya başladı.

**59. Why does Mia say the bakery is "dangerous"?**  
`rv1-a2-t01-q3` · A2 · Çıkarım

- It is very old and unsafe
- The owner is not very friendly
- **✔ She will buy too many cakes**
- It is open late at night

Kanıt: "There's a nice bakery downstairs too, which is dangerous!"  Gerekçe: Şaka yapıyor: fırın çok yakın, çok fazla tatlı alacak.

**60. In the email, "closer to" means …** ⟨…⟩  
`rv1-a2-t01-q4` · A2 · Bağlamda kelime

- more expensive than
- much bigger than
- older than
- **✔ nearer to**

Kanıt: "it's much closer to my office, so I can walk to work now"  Gerekçe: "Closer to" daha yakın demek; artık işe yürüyebiliyor.

#### Metin `rv1-a2-t02` · news · 73 kelime

> A small library in the town of Bridgefield is now open twenty-four hours a day. Visitors use a card to open the door, and cameras keep the building safe at night. The library has no staff after six in the evening, but people can still borrow books with a machine. Since the change in March, the number of visitors has doubled. Many of the new visitors are students and people who work late.

**61. What is the news story about?**  
`rv1-a2-t02-q1` · A2 · -

- **✔ A library that never closes**
- A new school for students
- A bookshop that is closing soon
- A job at a town library

Kanıt: "is now open twenty-four hours a day"  Gerekçe: Kütüphane artık günün yirmi dört saati açık.

**62. How do people borrow books at night?**  
`rv1-a2-t02-q2` · A2 · Ayrıntı

- They ask a worker
- **✔ They use a machine**
- They call the library
- They come with a teacher

Kanıt: "people can still borrow books with a machine"  Gerekçe: Akşam altıdan sonra personel yok; kitaplar makineyle alınıyor.

**63. "The number of visitors has doubled." This means there are …** ⟨…⟩  
`rv1-a2-t02-q3` · A2 · Bağlamda kelime

- half as many visitors
- the same number of visitors
- **✔ twice as many visitors**
- no new visitors

Kanıt: "the number of visitors has doubled"  Gerekçe: "Double" iki katına çıkmak demek.

**64. "Since the change in March …" What was the change?**  
`rv1-a2-t02-q4` · A2 · Bağlaşıklık

- It got a new café for visitors
- It got many new books for students
- It started to close early every night
- **✔ It began to open all day and night**

Kanıt: "is now open twenty-four hours a day"  Gerekçe: "The change" kütüphanenin artık hep açık olmasını gösteriyor.

#### Metin `rv1-a2-t03` · instructions · 73 kelime

> How to look after your new plant. Put it in a bright place, but not in hot sun. Give it a little water once a week. If the leaves turn yellow, you are giving it too much water. In winter, it needs less water than in summer. Turn the pot every few weeks, so all sides get light. Do not move it to a new room too often, because it doesn't like change.

**65. What do these instructions explain?**  
`rv1-a2-t03-q1` · A2 · -

- **✔ How to care for a plant**
- How to grow vegetables
- Where to buy a new plant
- How to paint a flower pot

Kanıt: "How to look after your new plant."  Gerekçe: Talimatlar bitkinin nasıl bakılacağını anlatıyor.

**66. What does it mean if the leaves turn yellow?**  
`rv1-a2-t03-q2` · A2 · Ayrıntı

- The plant needs much more sun
- **✔ The plant gets too much water**
- The plant is too cold
- The pot is too small

Kanıt: "If the leaves turn yellow, you are giving it too much water."  Gerekçe: Sararan yaprak fazla sulamanın işareti.

**67. It is December. What should you do?**  
`rv1-a2-t03-q3` · A2 · Çıkarım

- Water it more than in July
- Put it in hot sun all day
- **✔ Water it less than in July**
- Move it to a new room

Kanıt: "In winter, it needs less water than in summer."  Gerekçe: Aralık kış ayı; kışın yazdan daha az su gerekir.

**68. "… because it doesn't like change." What is "it"?**  
`rv1-a2-t03-q4` · A2 · Bağlaşıklık

- The room
- The water
- The window
- **✔ The plant**

Kanıt: "Do not move it to a new room too often, because it doesn't like change."  Gerekçe: "It" metnin konusu olan bitkiyi gösteriyor.

#### Metin `rv1-a2-t04` · narrative · 70 kelime

> Last year my grandmother started to learn the guitar. She was seventy-two. Her friends laughed and said she was too old, but she didn't listen to them. She practised every evening for thirty minutes. At first her fingers hurt and the music sounded terrible. After six months she could play three songs. At my birthday party, she played for everyone, and nobody laughed. Now her friends want to learn too.

**69. What is the story mainly about?**  
`rv1-a2-t04-q1` · A2 · -

- **✔ An old woman who learns something new**
- A party that went very badly
- A guitar teacher and all her young students
- A group of friends who sing

Kanıt: "Last year my grandmother started to learn the guitar."  Gerekçe: Yetmiş iki yaşında gitar öğrenen bir büyükanneyi anlatıyor.

**70. How long did she practise every evening?**  
`rv1-a2-t04-q2` · A2 · Ayrıntı

- Six minutes
- **✔ Thirty minutes**
- One hour
- Three whole hours

Kanıt: "She practised every evening for thirty minutes."  Gerekçe: Her akşam otuz dakika çalıştı.

**71. Why did nobody laugh at the party?**  
`rv1-a2-t04-q3` · A2 · Çıkarım

- They did not hear her
- The party ended early
- **✔ She played well**
- Her friends were not there

Kanıt: "At my birthday party, she played for everyone, and nobody laughed."  Gerekçe: Altı ayda iyi çalmayı öğrenmişti; bu yüzden kimse gülmedi.

**72. "The music sounded terrible." "Terrible" means …** ⟨…⟩  
`rv1-a2-t04-q4` · A2 · Bağlamda kelime

- very quiet
- very fast
- very new
- **✔ very bad**

Kanıt: "the music sounded terrible"  Gerekçe: "Terrible" çok kötü demek; başta parmakları acıyordu.

#### Metin `rv1-a2-t05` · advert · 71 kelime

> Summer swimming course for adults. Never learned to swim? It's not too late! Our ten-week course starts on the 3rd of June at the Riverside Pool. Lessons are on Tuesday evenings from seven to eight. Groups are small: only six people in each group. You don't need any special clothes, only a swimsuit and a towel. The price is ninety pounds. Book before the end of May and pay only seventy.

**73. Who is this course for?**  
`rv1-a2-t05-q1` · A2 · -

- **✔ Adults who cannot swim**
- Children in summer camp
- Teachers at the pool
- People who swim very well

Kanıt: "Never learned to swim? It's not too late!"  Gerekçe: Kurs yüzme bilmeyen yetişkinler için.

**74. How many people are in each group?**  
`rv1-a2-t05-q2` · A2 · Ayrıntı

- Three
- **✔ Six**
- Ten
- Seven

Kanıt: "only six people in each group"  Gerekçe: Her grupta altı kişi var.

**75. Ella books the course on the 20th of May. How much does she pay?**  
`rv1-a2-t05-q3` · A2 · Çıkarım

- Ninety pounds
- Sixty pounds
- **✔ Seventy pounds**
- Nothing at all

Kanıt: "Book before the end of May and pay only seventy."  Gerekçe: Mayıs bitmeden yazılan yetmiş pound öder.

**76. "Book before the end of May." Here "book" means …** ⟨…⟩  
`rv1-a2-t05-q4` · A2 · Bağlamda kelime

- read a story
- write a long letter
- buy a towel
- **✔ reserve a place**

Kanıt: "Book before the end of May"  Gerekçe: Burada "book" kitap değil, yer ayırtmak demek.

#### Metin `rv1-a2-t06` · blog · 74 kelime

> I didn't want to go camping. I don't like insects, and I hate cold showers. But my friends wanted to go to the lake, so I went with them. The first night was terrible because it rained and our tent was wet. Then the weather changed. We swam in the lake, cooked fish on a fire and looked at the stars. On the last day, I was the one who wanted to stay longer.

**77. What is the writer's main message?**  
`rv1-a2-t06-q1` · A2 · -

- **✔ She changed her mind about camping**
- Camping is always too cold
- Her friends never really listen to her
- Fishing is difficult to learn

Kanıt: "On the last day, I was the one who wanted to stay longer."  Gerekçe: Kampı istemiyordu ama sonunda en çok kalmak isteyen o oldu.

**78. Why was the first night bad?**  
`rv1-a2-t06-q2` · A2 · Ayrıntı

- There were too many insects in the tent
- **✔ It rained and the tent was wet**
- The shower was too cold
- They had no food to eat

Kanıt: "The first night was terrible because it rained and our tent was wet."  Gerekçe: Yağmur yağdı ve çadır ıslandı.

**79. How did the writer feel at the end of the trip?**  
`rv1-a2-t06-q3` · A2 · Çıkarım

- Tired and angry
- Cold and bored
- **✔ Happy to be there**
- Glad to go back home

Kanıt: "I was the one who wanted to stay longer"  Gerekçe: Daha uzun kalmak istemesi orada mutlu olduğunu gösteriyor.

**80. "… so I went with them." Who are "them"?**  
`rv1-a2-t06-q4` · A2 · Bağlaşıklık

- The insects
- Her parents
- The fish
- **✔ Her friends**

Kanıt: "But my friends wanted to go to the lake, so I went with them."  Gerekçe: "Them" göle gitmek isteyen arkadaşlarını gösteriyor.

#### Metin `rv1-a2-t07` · message · 69 kelime

> Hi everyone, a quick change for tomorrow's meeting. Room 4 is not free, so we will meet in the small kitchen on the second floor instead. The time is the same: ten o'clock. Please bring your notes from last week. Paul can't come because he is at a conference, so Sara will tell us about the new project. There will be coffee, but bring your own cup, please. Thanks, Linda

**81. Why does Linda send this message?**  
`rv1-a2-t07-q1` · A2 · -

- **✔ To say where the meeting is now**
- To cancel tomorrow's meeting
- To invite people to a conference
- To ask for help in the kitchen

Kanıt: "we will meet in the small kitchen on the second floor instead"  Gerekçe: Toplantının yeri değişti; bunu bildiriyor.

**82. What time is the meeting?**  
`rv1-a2-t07-q2` · A2 · Ayrıntı

- At nine
- **✔ At ten**
- At four
- At two

Kanıt: "The time is the same: ten o'clock."  Gerekçe: Saat aynı: on.

**83. Why will Sara talk about the project?**  
`rv1-a2-t07-q3` · A2 · Çıkarım

- She is the new manager
- She asked to do it
- **✔ Paul is not there**
- It is her first day

Kanıt: "Paul can't come because he is at a conference, so Sara will tell us about the new project."  Gerekçe: Projeyi anlatacak olan Paul konferansta; yerine Sara anlatıyor.

**84. "… in the small kitchen on the second floor instead." "Instead" means …** ⟨…⟩  
`rv1-a2-t07-q4` · A2 · Bağlamda kelime

- as well as Room 4
- at the same time
- after the coffee break
- **✔ in place of Room 4**

Kanıt: "Room 4 is not free, so we will meet in the small kitchen on the second floor instead."  Gerekçe: "Instead" yerine demek: 4 numaralı oda yerine mutfak.

#### Metin `rv1-a2-t08` · article · 74 kelime

> Why do cats sleep so much? An adult cat sleeps between twelve and sixteen hours a day. This is not because cats are lazy. In the wild, cats hunt small animals, and hunting needs a lot of energy. They sleep to save energy for short, fast runs. Cats are also most active early in the morning and in the evening. That is why your cat may wake you up before your alarm clock does.

**85. What does the text explain?**  
`rv1-a2-t08-q1` · A2 · -

- **✔ The reason cats sleep a lot**
- How to train a young kitten
- What cats like to eat
- Where wild cats live

Kanıt: "Why do cats sleep so much?"  Gerekçe: Metin kedilerin neden çok uyuduğunu açıklıyor.

**86. How many hours does an adult cat sleep a day?**  
`rv1-a2-t08-q2` · A2 · Ayrıntı

- Six to eight
- **✔ Twelve to sixteen**
- Two to four
- Eighteen to twenty

Kanıt: "An adult cat sleeps between twelve and sixteen hours a day."  Gerekçe: Yetişkin kedi günde on iki ile on altı saat uyur.

**87. Why may your cat wake you up early?**  
`rv1-a2-t08-q3` · A2 · Çıkarım

- It is hungry all night
- It does not like your alarm
- **✔ It is active in the morning**
- It sleeps only at noon

Kanıt: "Cats are also most active early in the morning and in the evening."  Gerekçe: Kediler sabah erken en hareketli; bu yüzden erken uyandırabilir.

**88. "They sleep to save energy …" Who are "they"?**  
`rv1-a2-t08-q4` · A2 · Bağlaşıklık

- The small animals
- The people
- The alarm clocks
- **✔ The cats**

Kanıt: "In the wild, cats hunt small animals, and hunting needs a lot of energy. They sleep to save energy"  Gerekçe: "They" avlanan kedileri gösteriyor; küçük hayvanlar av.

### B1

#### Metin `rv1-b1-t01` · article · 129 kelime

> Several companies in Iceland tried a four-day working week between 2015 and 2019. About 2,500 workers took part. They worked fewer hours, usually 35 or 36 instead of 40, but their pay stayed the same. Researchers wanted to know whether the workers would get less done. The results surprised many managers. In most workplaces, the amount of work stayed the same, and in some it even went up. Workers said they felt less stressed and had more time for their families and hobbies. One reason was that teams cut long meetings and stopped doing tasks that were not really necessary. After the trial, unions in Iceland agreed new contracts, and today a large number of workers have the right to shorter hours. Other countries, including Spain and the UK, have since started their own trials.

**89. What is the text mainly about?**  
`rv1-b1-t01-q1` · B1 · -

- **✔ A trial of shorter working weeks**
- Why managers in Iceland earn more
- How families spend their weekends
- A plan to close offices on Fridays

Kanıt: "Several companies in Iceland tried a four-day working week"  Gerekçe: Metin İzlanda'daki dört günlük çalışma haftası denemesini anlatıyor.

**90. How many hours did the workers usually work during the trial?**  
`rv1-b1-t01-q2` · B1 · Ayrıntı

- 40 hours
- **✔ 35 or 36 hours**
- 45 hours
- 25 or 30 hours

Kanıt: "usually 35 or 36 instead of 40"  Gerekçe: Deneme sırasında genelde 35-36 saat çalıştılar.

**91. Why did the amount of work not go down?**  
`rv1-b1-t01-q3` · B1 · Çıkarım

- Workers were paid more money
- Workers stayed late at night
- **✔ Teams wasted less time**
- Managers hired new workers

Kanıt: "teams cut long meetings and stopped doing tasks that were not really necessary"  Gerekçe: Uzun toplantıları ve gereksiz işleri bıraktılar; yani daha az vakit harcadılar.

**92. "… and in some it even went up." What went up?**  
`rv1-b1-t01-q4` · B1 · Bağlaşıklık

- The workers' pay
- The number of meetings
- The stress at work
- **✔ The amount of work**

Kanıt: "the amount of work stayed the same, and in some it even went up"  Gerekçe: "It" iş miktarını gösteriyor; maaş aynı kaldı.

#### Metin `rv1-b1-t02` · email · 136 kelime

> Dear Sir or Madam, I am writing about the jacket I ordered from your website on 2 May. When the parcel arrived a week later, the jacket was the right size but the wrong colour: I ordered dark blue and received bright green. I returned it the same day, using the label that came in the box, and I asked for a refund. Your website says refunds take five working days, but it is now three weeks later and I still have not received my money. I have called your customer service number twice. Both times I waited for over twenty minutes, and then the call ended. I would be grateful if you could return the full amount of £64 to my card as soon as possible. I look forward to hearing from you. Yours faithfully, Daniel Hart

**93. Why is Daniel writing?**  
`rv1-b1-t02-q1` · B1 · -

- **✔ He wants his money back**
- He wants a different size
- He wants to order a new jacket
- He wants to work for the shop

Kanıt: "I asked for a refund"  Gerekçe: Ceketi iade etti, parası hâlâ gelmedi; parasını istiyor.

**94. What was wrong with the jacket?**  
`rv1-b1-t02-q2` · B1 · Ayrıntı

- It was too big for him
- **✔ It was the wrong colour**
- It had a broken zip
- It arrived without a label

Kanıt: "the jacket was the right size but the wrong colour"  Gerekçe: Beden doğruydu, renk yanlıştı.

**95. "I would be grateful if …" Here "grateful" means …** ⟨…⟩  
`rv1-b1-t02-q3` · B1 · Bağlamda kelime

- angry
- surprised
- **✔ thankful**
- worried

Kanıt: "I would be grateful if you could return the full amount"  Gerekçe: "Grateful" minnettar, teşekkür eden demek.

**96. What happened when Daniel phoned the company?**  
`rv1-b1-t02-q4` · B1 · Çıkarım

- He got his refund at once
- Someone was very rude
- They sent a new jacket
- **✔ He never spoke to anyone**

Kanıt: "Both times I waited for over twenty minutes, and then the call ended."  Gerekçe: İki kez de beklerken arama kesildi; kimseyle konuşamadı.

#### Metin `rv1-b1-t03` · blog · 132 kelime

> For years I travelled the way most people do: a cheap flight, a busy weekend, as many famous sights as possible, and a flight home. I came back with hundreds of photos and very few memories. Last summer I tried something different. I took the train from London to Rome, which took two days, and I stayed in one small town for a whole week. I didn't make a plan. I bought bread from the same baker every morning, and by Thursday she was asking about my family. I learned more Italian in that week than in a year of lessons. Of course, slow travel isn't for everyone. It costs more time, and sometimes more money. But if you want to understand a place rather than just see it, I'd recommend it.

**97. What is the writer's main point?**  
`rv1-b1-t03-q1` · B1 · -

- Famous sights are always far too crowded
- **✔ Travelling slowly can be more rewarding**
- Trains are cheaper than planes
- Italian is easy to learn quickly

Kanıt: "if you want to understand a place rather than just see it, I'd recommend it"  Gerekçe: Yazar yavaş seyahatin daha doyurucu olduğunu söylüyor.

**98. How long did the train journey take?**  
`rv1-b1-t03-q2` · B1 · Ayrıntı

- One day
- A week
- **✔ Two days**
- Three hours

Kanıt: "I took the train from London to Rome, which took two days"  Gerekçe: Tren yolculuğu iki gün sürdü; bir hafta kasabada kaldı.

**99. Why was the baker asking about the writer's family by Thursday?**  
`rv1-b1-t03-q3` · B1 · Çıkarım

- She knew his family from London
- She needed help in her shop
- She wanted him to leave town
- **✔ They had got to know each other**

Kanıt: "I bought bread from the same baker every morning"  Gerekçe: Her sabah aynı fırına gittiği için birbirlerini tanıdılar.

**100. "I'd recommend it." What would the writer recommend?**  
`rv1-b1-t03-q4` · B1 · Bağlaşıklık

- **✔ Slow travel**
- Taking cheap flights
- Italian lessons
- Busy weekends

Kanıt: "Of course, slow travel isn't for everyone."  Gerekçe: "It" yavaş seyahati gösteriyor.

#### Metin `rv1-b1-t04` · notice · 137 kelime

> Notice to all residents. On Wednesday 14 June, engineers will replace the main water pipe under the building. The water will be turned off from 9 a.m. until approximately 3 p.m. During this time, toilets will flush only once, so please fill a bucket the night before if you need to. The lifts will not be affected, but the car park entrance will be closed until noon because the engineers' vans will be parked there. If you have a medical reason for needing water during the day, please contact the building manager by Monday so that we can make other arrangements. We apologise for any inconvenience and thank you for your patience. When the water comes back on, it may look brown for a few minutes. This is normal; just let the tap run until it is clear.

**101. What is the notice mainly about?**  
`rv1-b1-t04-q1` · B1 · -

- New rules for the car park
- A change of building manager
- **✔ A day when the water is off**
- Repairs to the lifts next week

Kanıt: "The water will be turned off from 9 a.m."  Gerekçe: Duyuru suyun kesileceği günü anlatıyor.

**102. When can residents use the car park entrance again?**  
`rv1-b1-t04-q2` · B1 · Ayrıntı

- At 9 a.m.
- At 3 p.m.
- On Monday
- **✔ At noon**

Kanıt: "the car park entrance will be closed until noon"  Gerekçe: Otopark girişi öğlene kadar kapalı.

**103. "… until approximately 3 p.m." "Approximately" means …** ⟨…⟩  
`rv1-b1-t04-q3` · B1 · Bağlamda kelime

- **✔ about**
- exactly
- after
- before

Kanıt: "until approximately 3 p.m."  Gerekçe: "Approximately" yaklaşık demek.

**104. Who should contact the manager by Monday?**  
`rv1-b1-t04-q4` · B1 · Çıkarım

- Residents who will be away on Wednesday
- **✔ Someone who needs water for health**
- Anyone who uses the lifts
- Residents who have a car

Kanıt: "If you have a medical reason for needing water during the day, please contact the building manager by Monday"  Gerekçe: Sağlık nedeniyle suya ihtiyacı olanlar yöneticiye haber vermeli.

#### Metin `rv1-b1-t05` · narrative · 148 kelime

> When Leo's flight was cancelled, the airline offered him a hotel room and a seat on the next morning's plane. Most passengers accepted and went straight to the hotel. Leo, however, had a job interview in Madrid at ten o'clock the next morning, and the next flight would land at eleven. He looked at the train timetable on his phone. There was a night train that left in forty minutes, but the station was on the other side of the city. He ran to the taxi queue, explained his problem to the woman at the front, and she let him take her taxi. He caught the train with two minutes to spare, slept badly in his seat, and arrived in Madrid at seven. He got the job. Six months later, at a company party, he recognised the woman from the taxi queue: she was his new boss's sister.

**105. What is the story mainly about?**  
`rv1-b1-t05-q1` · B1 · -

- Why Leo's flight was cancelled
- A night in an airport hotel
- **✔ How Leo got to an interview on time**
- Leo's first day at the new company office

Kanıt: "Leo, however, had a job interview in Madrid at ten o'clock"  Gerekçe: Hikâye Leo'nun mülakata yetişme çabasını anlatıyor.

**106. Why couldn't Leo take the morning flight?**  
`rv1-b1-t05-q2` · B1 · Ayrıntı

- It was more expensive than the train
- **✔ It arrived after his interview**
- It was also cancelled
- It had no free seats left

Kanıt: "the next flight would land at eleven"  Gerekçe: Uçak on birde inecekti; mülakat ondaydı.

**107. "… and she let him take her taxi." Who is "she"?**  
`rv1-b1-t05-q3` · B1 · Bağlaşıklık

- A worker from the airline desk
- Leo's future boss
- A driver at the taxi queue
- **✔ A woman waiting for a taxi**

Kanıt: "explained his problem to the woman at the front, and she let him take her taxi"  Gerekçe: "She" taksi kuyruğunun başındaki kadını gösteriyor.

**108. How did Leo probably feel when he saw the woman at the party?**  
`rv1-b1-t05-q4` · B1 · Çıkarım

- **✔ Surprised**
- Angry
- Bored
- Frightened

Kanıt: "he recognised the woman from the taxi queue: she was his new boss's sister"  Gerekçe: Taksideki kadının patronunun kız kardeşi çıkması onu şaşırtmış olmalı.

#### Metin `rv1-b1-t06` · advert · 130 kelime

> Weekend Guides Wanted. The City Museum is looking for friendly, reliable people to lead tours for visitors on Saturdays and Sundays. Each tour lasts about an hour and is for groups of up to fifteen people. You don't need a history degree; we will give you four weeks of training, and you'll learn everything you need to know about our collections. What you do need is confidence speaking in front of groups and a good level of English. A second language, especially Spanish or Chinese, would be a big advantage, as many of our visitors come from abroad. Guides are paid £14 an hour and get free entry to all museum events. To apply, send a short video (no longer than two minutes) introducing yourself to jobs@citymuseum.org before 30 April.

**109. What is the advert for?**  
`rv1-b1-t06-q1` · B1 · -

- **✔ A job showing visitors around**
- A history course at the museum
- A museum event at the weekend
- Free tickets for foreign visitors

Kanıt: "is looking for friendly, reliable people to lead tours"  Gerekçe: İlan ziyaretçilere tur yaptıracak rehber arıyor.

**110. What must people send to apply?**  
`rv1-b1-t06-q2` · B1 · Ayrıntı

- A copy of their degree
- A list of languages they speak
- **✔ A short video of themselves**
- A letter from a former teacher

Kanıt: "send a short video (no longer than two minutes) introducing yourself"  Gerekçe: Başvuru için kendini tanıtan kısa bir video gönderiliyor.

**111. Which person has the best chance of getting the job?**  
`rv1-b1-t06-q3` · B1 · Çıkarım

- A very shy history student
- **✔ A confident speaker of Spanish**
- A teacher who is only free on weekdays
- A person who dislikes big groups

Kanıt: "What you do need is confidence speaking in front of groups"  Gerekçe: Kendine güven şart, İspanyolca da artı; hafta sonu çalışılıyor.

**112. "… would be a big advantage …" "Advantage" means …** ⟨…⟩  
`rv1-b1-t06-q4` · B1 · Bağlamda kelime

- a kind of problem
- a type of extra payment
- a special language test
- **✔ something that helps**

Kanıt: "A second language, especially Spanish or Chinese, would be a big advantage"  Gerekçe: "Advantage" avantaj, işe yarayan şey.

#### Metin `rv1-b1-t07` · article · 134 kelime

> Have you ever met someone at a party and forgotten their name a few seconds later? You are not alone, and it is not a sign of a bad memory. Psychologists say the problem is attention. When we are introduced to someone, we are often busy thinking about what to say next, or how we look, so the name never really gets stored. Faces are different: our brains are very good at remembering them, which is why we often recognise people without knowing who they are. There are simple ways to improve. Repeat the name when you reply, for example "Nice to meet you, Sam." Try to connect it with something you already know, such as a friend with the same name. Using the name once more before you leave also helps it stay.

**113. What is the text mainly about?**  
`rv1-b1-t07-q1` · B1 · -

- How to make friends at parties
- Why some people have bad memories
- How our brains store faces
- **✔ Why names are easy to forget**

Kanıt: "Have you ever met someone at a party and forgotten their name a few seconds later?"  Gerekçe: Metin isimlerin neden çabuk unutulduğunu ve ne yapılabileceğini anlatıyor.

**114. What do psychologists say is the cause of the problem?**  
`rv1-b1-t07-q2` · B1 · Ayrıntı

- **✔ Poor attention**
- Old age
- Too many names
- Tiredness

Kanıt: "Psychologists say the problem is attention."  Gerekçe: Psikologlara göre sorun dikkat.

**115. "… we often recognise people …" "Recognise" means …** ⟨…⟩  
`rv1-b1-t07-q3` · B1 · Bağlamda kelime

- forget their face quickly
- talk to them first
- **✔ know you have seen them before**
- ask them their name once again

Kanıt: "we often recognise people without knowing who they are"  Gerekçe: "Recognise" birini daha önce gördüğünü bilmek, tanımak.

**116. "… also helps it stay." What is "it"?**  
`rv1-b1-t07-q4` · B1 · Bağlaşıklık

- The face
- **✔ The name**
- The party
- The friend

Kanıt: "Using the name once more before you leave also helps it stay."  Gerekçe: "It" ismi gösteriyor.

#### Metin `rv1-b1-t08` · news · 125 kelime

> Three years ago, the only shop in the village of Elsby closed. For older residents without cars, the nearest supermarket was a forty-minute bus ride away, and the bus only ran twice a day. Instead of waiting for someone else to solve the problem, a group of neighbours decided to open their own. They asked every household to invest fifty pounds, and two hundred families agreed. The shop is run mostly by volunteers, with two paid staff. It sells local vegetables, bread from a nearby farm and everyday basics. Profits go back into the village: last year they paid for new lights in the park. "It's more than a shop," says volunteer Mary Cole, 78. "For some people, it's the only conversation they have all day."

**117. What is the text mainly about?**  
`rv1-b1-t08-q1` · B1 · -

- A new supermarket near a village
- A bus service for older people
- **✔ A shop that a village opened itself**
- A farm that sells bread and vegetables

Kanıt: "a group of neighbours decided to open their own"  Gerekçe: Köylüler kendi dükkânlarını açtı.

**118. How much did each family pay?**  
`rv1-b1-t08-q2` · B1 · Ayrıntı

- **✔ Fifty pounds**
- Two hundred pounds
- Forty pounds
- Twenty pounds

Kanıt: "They asked every household to invest fifty pounds"  Gerekçe: Her hane elli pound yatırdı.

**119. What does Mary Cole mean?**  
`rv1-b1-t08-q3` · B1 · Çıkarım

- The shop sells too many things
- The shop needs more volunteers
- The shop should open later in the evening
- **✔ The shop is a place to meet people**

Kanıt: "For some people, it's the only conversation they have all day."  Gerekçe: Dükkân bazıları için günün tek sohbet yeri; buluşma noktası.

**120. "… decided to open their own." Their own what?**  
`rv1-b1-t08-q4` · B1 · Bağlaşıklık

- Bus company
- **✔ Village shop**
- Vegetable farm
- Car park

Kanıt: "the only shop in the village of Elsby closed"  Gerekçe: "Their own" kapanan dükkânın yerine kendi dükkânlarını gösteriyor.

### B2

#### Metin `rv1-b2-t01` · article · 194 kelime

> Most people assume that putting things off is a problem of laziness or poor time management. Recent research suggests something different: procrastination is largely about emotions. When a task makes us feel anxious, bored or insecure, avoiding it gives us immediate relief, even though we know the delay will cost us later. In other words, we are not avoiding the work itself so much as the unpleasant feelings attached to it. This explains why apps and planners often fail. A detailed schedule does nothing to reduce the fear of writing a weak report. What seems to work better is lowering the emotional cost of starting. Psychologists recommend breaking a task into a first step so small that it feels almost silly, such as opening the document and writing one sentence. Another approach is self-compassion. In one study, students who forgave themselves for procrastinating before their first exam procrastinated less before the next one, while those who criticised themselves harshly continued the pattern. Being kind to yourself, it turns out, is not the same as letting yourself off the hook; it removes one of the bad feelings that made you delay in the first place.

**121. What is the main argument of the text?**  
`rv1-b2-t01-q1` · B2 · -

- **✔ Procrastination is mainly an emotional problem**
- Good planning apps can end procrastination
- Students who are lazy usually fail their exams
- Most people manage their time very badly

Kanıt: "procrastination is largely about emotions"  Gerekçe: Ana fikir: erteleme tembellik değil, duygularla ilgili.

**122. Why, according to the text, do planners often fail?**  
`rv1-b2-t01-q2` · B2 · Çıkarım

- They take too much time to set up properly
- **✔ They do not address the feelings involved**
- People forget to look at them
- They make tasks seem too large

Kanıt: "A detailed schedule does nothing to reduce the fear of writing a weak report."  Gerekçe: Plan korkuyu azaltmıyor; sorun duygu olduğu için işe yaramıyor.

**123. "… letting yourself off the hook …" means …** ⟨…⟩  
`rv1-b2-t01-q3` · B2 · Bağlamda kelime

- forcing yourself to work even harder
- asking other people to share the work
- **✔ excusing yourself from responsibility**
- forgetting about the task completely

Kanıt: "is not the same as letting yourself off the hook"  Gerekçe: "Let off the hook" sorumluluktan kurtarmak, kendini aklamak.

**124. What happened to students who criticised themselves harshly?**  
`rv1-b2-t01-q4` · B2 · Ayrıntı

- They studied much harder
- They got better marks
- They forgave themselves the next time
- **✔ They continued to put things off**

Kanıt: "while those who criticised themselves harshly continued the pattern"  Gerekçe: Kendini sert eleştirenler ertelemeye devam etti.

#### Metin `rv1-b2-t02` · review · 181 kelime

> Marta Lind's second novel, The Glass Orchard, arrives with enormous expectations. Her debut sold over a million copies and was translated into thirty languages, so it is perhaps unfair that every page of this new book will be compared with it. Still, the comparison is hard to avoid, because the two novels share so much: a remote northern village, a family secret, and a narrator who reveals the truth only in the final chapter. Where the first book felt fresh, this one occasionally feels like a careful copy. That said, Lind remains a remarkable writer of place. Her descriptions of the frozen lake and the long summer evenings are so precise that you can almost feel the temperature change. The middle section, in which the narrator's grandmother tells her own story, is the strongest writing Lind has produced. The problem is the ending. After three hundred patient pages, the final revelation is delivered in a rush and explained rather than shown. Readers who loved the first novel will find plenty to enjoy here; those hoping for something new may be disappointed.

**125. What is the reviewer's overall opinion of the novel?**  
`rv1-b2-t02-q1` · B2 · Amaç ve ton

- It is far better than her first novel
- It is badly written from start to finish
- It is a far more original story than her debut
- **✔ It has strengths but repeats the first book**

Kanıt: "Where the first book felt fresh, this one occasionally feels like a careful copy. That said, Lind remains a remarkable writer of place."  Gerekçe: Eleştirmen karışık düşünüyor: güçlü yanlar var ama ilk kitabı tekrarlıyor.

**126. Which part of the book does the reviewer praise most?**  
`rv1-b2-t02-q2` · B2 · Ayrıntı

- The final chapter
- **✔ The grandmother's story**
- The family secret
- The way the secret is revealed

Kanıt: "The middle section, in which the narrator's grandmother tells her own story, is the strongest writing"  Gerekçe: En güçlü bölüm büyükannenin anlattığı orta kısım.

**127. What is the reviewer's complaint about the ending?**  
`rv1-b2-t02-q3` · B2 · Çıkarım

- **✔ It happens too quickly**
- It is too sad
- It is too long
- It is too hard to understand

Kanıt: "the final revelation is delivered in a rush"  Gerekçe: "Delivered in a rush" son bölümün aceleyle geçildiğini söylüyor.

**128. "… this one occasionally feels like a careful copy." What does "this one" refer to?**  
`rv1-b2-t02-q4` · B2 · Bağlaşıklık

- The first novel
- The northern village
- **✔ The Glass Orchard**
- The final chapter

Kanıt: "Where the first book felt fresh, this one occasionally feels like a careful copy."  Gerekçe: "This one" ilk kitapla karşılaştırılan yeni roman, The Glass Orchard.

#### Metin `rv1-b2-t03` · email · 190 kelime

> Dear all, Following last month's staff survey, we have made some changes to our hybrid working policy, which will take effect from 1 March. First, the number of required office days will drop from three to two per week. However, everyone will be expected to be in the office on Tuesdays, since this is when most team meetings and training sessions take place. Your second office day can be chosen freely, but please agree it with your line manager so that each team has some cover throughout the week. Second, we are replacing fixed desks with a booking system. Desks can be reserved up to two weeks in advance through the intranet. I realise that some of you are attached to your current desks, and I understand this may take some getting used to. However, with fewer people in the office on any given day, keeping a desk for everyone is no longer practical, and the space we save will become two new meeting rooms. If you have concerns, my door is open, or you can raise them anonymously through the survey link below. Best regards, Helen Ward, Head of Operations

**129. What is the main purpose of Helen's email?**  
`rv1-b2-t03-q1` · B2 · -

- To invite staff to a training day
- **✔ To explain changes to office working**
- To announce new meeting rooms
- To ask staff to complete another survey

Kanıt: "we have made some changes to our hybrid working policy"  Gerekçe: E-posta ofis çalışma düzenindeki değişiklikleri anlatıyor.

**130. Which day must everyone be in the office?**  
`rv1-b2-t03-q2` · B2 · Ayrıntı

- **✔ Tuesday**
- Monday
- Wednesday
- Friday

Kanıt: "everyone will be expected to be in the office on Tuesdays"  Gerekçe: Herkes salı günü ofiste olmalı.

**131. Why is the company introducing a desk booking system?**  
`rv1-b2-t03-q3` · B2 · Çıkarım

- Staff complained about their desks
- The intranet needed a new feature
- **✔ Fewer people are in the office each day**
- Managers want to know who comes in daily

Kanıt: "with fewer people in the office on any given day, keeping a desk for everyone is no longer practical"  Gerekçe: Ofiste her gün daha az kişi olduğu için sabit masa gereksiz.

**132. "… some of you are attached to your current desks …" "Attached to" here means …** ⟨…⟩  
`rv1-b2-t03-q4` · B2 · Bağlamda kelime

- bored with
- far away from
- responsible for
- **✔ fond of**

Kanıt: "I realise that some of you are attached to your current desks"  Gerekçe: Burada "attached to" bağlanmış, sevmek anlamında.

#### Metin `rv1-b2-t04` · article · 189 kelime

> In many hot cities, temperatures in the centre can be several degrees higher than in the surrounding countryside. This is known as the urban heat island effect, and it happens because roads, roofs and buildings absorb heat during the day and release it slowly at night. One surprisingly simple response is to paint roofs white. Dark surfaces can absorb up to ninety percent of sunlight, while a white surface reflects most of it. In New York, volunteers have painted more than ten million square feet of roofs since 2009, and studies suggest that a white roof can be up to thirty degrees cooler than a black one on a summer afternoon. The buildings underneath need less air conditioning, which reduces both energy bills and the demand on the power network during heatwaves. Critics point out that white roofs are less useful in cities with cold winters, where the extra heat from a dark roof might actually be welcome. Others argue that planting trees or creating green roofs offers more benefits, including cleaner air and homes for wildlife. Most experts agree, however, that no single solution is enough on its own.

**133. What is the text mainly about?**  
`rv1-b2-t04-q1` · B2 · -

- **✔ A cheap way to cool down hot cities**
- The history of air conditioning
- Why New York has cold winters
- How volunteers plant trees on city roofs

Kanıt: "One surprisingly simple response is to paint roofs white."  Gerekçe: Metin sıcak şehirleri serinletmenin basit bir yolunu anlatıyor.

**134. How much cooler can a white roof be?**  
`rv1-b2-t04-q2` · B2 · Ayrıntı

- Up to ten degrees
- **✔ Up to thirty degrees**
- Up to ninety degrees
- Several degrees

Kanıt: "a white roof can be up to thirty degrees cooler than a black one"  Gerekçe: Beyaz çatı otuz dereceye kadar daha serin olabilir.

**135. Why might a dark roof be better in some cities?**  
`rv1-b2-t04-q3` · B2 · Çıkarım

- It is much cheaper to paint and repair
- It lasts longer than white
- **✔ It keeps buildings warmer in winter**
- It looks more attractive to most people

Kanıt: "where the extra heat from a dark roof might actually be welcome"  Gerekçe: Soğuk kışlarda koyu çatının fazladan ısısı işe yarar.

**136. "… while a white surface reflects most of it." What does "it" refer to?**  
`rv1-b2-t04-q4` · B2 · Bağlaşıklık

- The roof
- Heat at night
- The city
- **✔ Sunlight**

Kanıt: "Dark surfaces can absorb up to ninety percent of sunlight, while a white surface reflects most of it."  Gerekçe: "It" güneş ışığını gösteriyor.

#### Metin `rv1-b2-t05` · narrative · 184 kelime

> For eleven years, my father ran a small repair shop on Carver Street. He fixed radios, then televisions, and eventually mobile phones, adapting each time the world decided that the old things were no longer worth repairing. I spent most of my teenage Saturdays behind the counter, pretending to be bored while secretly watching how he worked. He never rushed. Customers would arrive impatient, demanding to know how long it would take, and he would simply reply, "As long as it needs." Some of them left and never came back. Most of them returned. When the shop finally closed, it wasn't because of a lack of customers; the building had been sold to a developer who planned to turn the whole street into flats. My father didn't complain. He sold his tools to a young man who was opening a shop in another part of town, and kept only one small screwdriver, which he still carries in his pocket. Last week I broke the screen of my phone. Before I could book a repair, he had already taken it apart on the kitchen table.

**137. What is the writer's attitude towards the father?**  
`rv1-b2-t05-q1` · B2 · Amaç ve ton

- **✔ Respectful and warm**
- Ashamed and embarrassed
- Annoyed and impatient
- Sorry and guilty

Kanıt: "secretly watching how he worked"  Gerekçe: Yazar babasını gizlice izleyip hayranlıkla, sıcaklıkla anlatıyor.

**138. Why did the shop close?**  
`rv1-b2-t05-q2` · B2 · Ayrıntı

- It had too few customers
- **✔ The building was sold**
- The father became ill
- Phones became too cheap

Kanıt: "the building had been sold to a developer"  Gerekçe: Bina bir müteahhide satıldı; müşteri azlığı değil.

**139. What does the father's answer "As long as it needs" show about him?**  
`rv1-b2-t05-q3` · B2 · Çıkarım

- He did not like his customers
- He wanted to charge more money
- **✔ He cared more about quality than speed**
- He was never sure how to fix them well

Kanıt: "He never rushed."  Gerekçe: Acele etmiyor; işi doğru yapmayı hızdan önemli tutuyor.

**140. "… adapting each time the world decided …" "Adapting" means …** ⟨…⟩  
`rv1-b2-t05-q4` · B2 · Bağlamda kelime

- refusing to accept new ideas
- moving to a different town
- complaining about the new technology
- **✔ changing to suit new conditions**

Kanıt: "He fixed radios, then televisions, and eventually mobile phones, adapting each time"  Gerekçe: Radyodan telefona geçerek koşullara uyum sağladı.

#### Metin `rv1-b2-t06` · interview · 186 kelime

> Q: You've spent twenty years studying octopuses. What first got you interested? A: Honestly, it was an accident. I was studying crabs, and an octopus kept stealing them from my traps. I was annoyed at first, but then I noticed it was learning. Every week it got faster at opening the traps. Q: Are octopuses really as intelligent as people say? A: In some ways, yes. They can solve puzzles, use coconut shells as shelters, and recognise individual humans. In one lab, an octopus repeatedly sprayed water at one particular researcher it seemed to dislike. But we should be careful about comparing them with us. Most of an octopus's neurons are in its arms rather than its brain, so its intelligence probably works in a completely different way. Q: What's the biggest challenge in your research? A: Their lifespan. Most species live only one or two years, so you never get to watch an individual develop over a long time. Just as you start to understand one animal, it's gone. That's frustrating, but it also makes me wonder what they could achieve if they lived longer.

**141. What is the interview mainly about?**  
`rv1-b2-t06-q1` · B2 · -

- **✔ The intelligence of octopuses**
- How to catch crabs in traps
- The dangers of working in labs
- Why octopuses dislike humans

Kanıt: "Are octopuses really as intelligent as people say?"  Gerekçe: Söyleşi ahtapotların zekâsı üzerine.

**142. What did the octopus do in the lab?**  
`rv1-b2-t06-q2` · B2 · Ayrıntı

- It stole crabs from a trap
- **✔ It sprayed water at someone**
- It hid inside a coconut
- It escaped from its tank at night

Kanıt: "an octopus repeatedly sprayed water at one particular researcher"  Gerekçe: Laboratuvarda bir araştırmacıya su püskürttü.

**143. Why does the scientist say we should be careful when comparing octopuses with us?**  
`rv1-b2-t06-q3` · B2 · Çıkarım

- They have much larger brains
- They only live for a short time
- **✔ Their minds may work very differently**
- They are much less intelligent than we think

Kanıt: "its intelligence probably works in a completely different way"  Gerekçe: Nöronları kollarında; zekâları bizimkinden çok farklı işliyor olabilir.

**144. "… but then I noticed it was learning." What was learning?**  
`rv1-b2-t06-q4` · B2 · Bağlaşıklık

- The crab
- The trap
- The researcher
- **✔ The octopus**

Kanıt: "an octopus kept stealing them from my traps. I was annoyed at first, but then I noticed it was learning."  Gerekçe: "It" tuzaklardan yengeç çalan ahtapotu gösteriyor.

#### Metin `rv1-b2-t07` · announcement · 175 kelime

> Have your say on the future of Riverside Park. The city council is planning the biggest changes to Riverside Park in fifty years, and we want to hear from the people who use it. Three options are being considered. Option A would keep the park largely as it is, with repairs to paths and the children's playground. Option B would add a café, public toilets and a small outdoor stage for concerts, paid for partly by renting the café to a private business. Option C would turn the northern meadow into a protected wildlife area, which would mean closing it to dogs and organised sports. Each option has costs and benefits, and none of them is the council's preferred choice at this stage. Detailed plans are available in the library and online. You can give your views by completing the online questionnaire or by attending one of two public meetings, on 12 and 19 October at the Town Hall. The consultation closes on 31 October, after which a final proposal will be presented to the council in December.

**145. What is the main purpose of the announcement?**  
`rv1-b2-t07-q1` · B2 · Amaç ve ton

- **✔ To ask the public for their opinions**
- To advertise a new café in the park
- To announce that the park will close
- To explain why the playground is unsafe

Kanıt: "we want to hear from the people who use it"  Gerekçe: Belediye halkın görüşünü istiyor.

**146. Which option includes a stage for concerts?**  
`rv1-b2-t07-q2` · B2 · Ayrıntı

- Option A
- **✔ Option B**
- Option C
- All of them

Kanıt: "Option B would add a café, public toilets and a small outdoor stage for concerts"  Gerekçe: Konser sahnesi B seçeneğinde.

**147. Who would probably be most unhappy with Option C?**  
`rv1-b2-t07-q3` · B2 · Çıkarım

- Children who use the playground
- People who want a café
- **✔ Dog owners who use the meadow**
- Birdwatchers who visit the park

Kanıt: "which would mean closing it to dogs and organised sports"  Gerekçe: C seçeneği çayırı köpeklere kapatıyor.

**148. "… none of them is the council's preferred choice …" This means the council …** ⟨…⟩  
`rv1-b2-t07-q4` · B2 · Bağlamda kelime

- has already chosen Option A
- does not like any option
- wants the public to pay
- **✔ has not chosen one yet**

Kanıt: "none of them is the council's preferred choice at this stage"  Gerekçe: "Preferred choice" yok: belediye henüz birini seçmedi.

#### Metin `rv1-b2-t08` · blog · 182 kelime

> Last January I deleted every social media app from my phone. I wasn't trying to make a statement; I was simply tired of picking up my phone to check the time and putting it down forty minutes later, unable to remember what I had seen. The first week was harder than I expected. I kept reaching for my pocket during any quiet moment: in queues, on the bus, even between sentences of a conversation. By the third week, something had changed. I was reading again, actual books, at a rate I hadn't managed since university. I also noticed I was calmer, although I can't prove that the two things are connected. Not everything was better. I missed several friends' news, including a birthday party I only heard about afterwards, and I realised how much of my social life had quietly moved online. So I haven't become a missionary for digital detox. I've reinstalled one app, only on my laptop, and I check it twice a week. It's a compromise, but it's one I chose rather than one that was chosen for me.

**149. What is the text mainly about?**  
`rv1-b2-t08-q1` · B2 · -

- Why reading real books is better for you
- **✔ The results of giving up social media**
- How to make friends without apps
- The writer's year at university

Kanıt: "Last January I deleted every social media app from my phone."  Gerekçe: Metin sosyal medyayı bırakmanın sonuçlarını anlatıyor.

**150. What negative effect did the writer experience?**  
`rv1-b2-t08-q2` · B2 · Ayrıntı

- **✔ Missing news from friends**
- Feeling less calm than before
- Reading fewer books
- Losing the phone

Kanıt: "I missed several friends' news"  Gerekçe: Arkadaşlarının haberlerini kaçırdı.

**151. "… although I can't prove that the two things are connected." Which two things?**  
`rv1-b2-t08-q3` · B2 · Bağlaşıklık

- Using the bus and reading books
- Queues and quiet moments
- University and books
- **✔ Reading more and feeling calmer**

Kanıt: "although I can't prove that the two things are connected"  Gerekçe: İki şey: daha çok okumak ve daha sakin olmak.

**152. What is the writer's attitude to digital detox at the end?**  
`rv1-b2-t08-q4` · B2 · Amaç ve ton

- **✔ Balanced: it has good and bad sides**
- Very enthusiastic: everyone should try it
- Negative: it was a waste of time
- Angry: friends should have called

Kanıt: "So I haven't become a missionary for digital detox."  Gerekçe: Ne savunucu ne karşıt; iyi ve kötü yanlarını tartıp orta yol bulmuş.

## 3. Sınır adımı: kısa tek sorular

### A1

**153. "My brother is twelve. I am ten." Who is older?**  
`rv1-b-a1-01` · A1 · Ayrıntı

- The writer
- Both are ten
- Both are twelve
- **✔ The brother**

Kanıt: "My brother is twelve. I am ten."  Gerekçe: Kardeş on iki, yazar on yaşında; kardeş büyük.

**154. "The shop is closed. Come back tomorrow." "Closed" means …** ⟨…⟩  
`rv1-b-a1-02` · A1 · Bağlamda kelime

- **✔ not open**
- very big
- very small
- not far

Kanıt: "The shop is closed."  Gerekçe: "Closed" kapalı, açık değil.

**155. "I have a dog and two cats. I don't have a bird." How many animals does the writer have?**  
`rv1-b-a1-03` · A1 · Ayrıntı

- Two
- **✔ Three**
- Seven
- One

Kanıt: "I have a dog and two cats."  Gerekçe: Bir köpek ve iki kedi: üç hayvan.

**156. "Please be quiet. People are reading." Where can you see this?**  
`rv1-b-a1-04` · A1 · -

- At a football game
- In a busy market
- **✔ In a library**
- At a birthday party

Kanıt: "People are reading."  Gerekçe: Sessiz olunması istenen ve insanların okuduğu yer kütüphane.

**157. "Tom and Jo are my friends. They live next to me." Who are "they"?**  
`rv1-b-a1-05` · A1 · Bağlaşıklık

- My parents
- My teachers
- My sisters
- **✔ Tom and Jo**

Kanıt: "Tom and Jo are my friends. They live next to me."  Gerekçe: "They" Tom ile Jo'yu gösteriyor.

**158. "The film starts at seven. Please come at half past six." When must you come?**  
`rv1-b-a1-06` · A1 · Ayrıntı

- **✔ At half past six**
- At ten past seven
- At ten past six
- At half past seven

Kanıt: "Please come at half past six."  Gerekçe: Film yedide başlıyor; altı buçukta gelinmeli.

### A2

**159. "Ben usually walks to work, but today he took the bus because of the rain." Why did Ben take the bus?**  
`rv1-b-a2-01` · A2 · Çıkarım

- He was late for work
- His car was broken
- **✔ The weather was bad**
- He moved house

Kanıt: "today he took the bus because of the rain"  Gerekçe: Yağmur yüzünden otobüse bindi.

**160. "Our shop moved. We are not on High Street any more. Find us at 12 Park Road." Where is the shop now?**  
`rv1-b-a2-02` · A2 · Ayrıntı

- On High Street
- Next to the park
- In the old place
- **✔ At 12 Park Road**

Kanıt: "Find us at 12 Park Road."  Gerekçe: Dükkân artık Park Road 12'de.

**161. "The test was easier than I expected." "Expected" means …** ⟨…⟩  
`rv1-b-a2-03` · A2 · Bağlamda kelime

- **✔ thought before**
- wrote down
- learned at school
- said loudly

Kanıt: "The test was easier than I expected."  Gerekçe: "Expect" önceden düşünmek, beklemek.

**162. "Anna called her brother, but he didn't answer. He was at the gym." Who was at the gym?**  
`rv1-b-a2-04` · A2 · Bağlaşıklık

- Anna herself
- **✔ Anna's brother**
- Anna's mother
- Anna and her brother

Kanıt: "Anna called her brother, but he didn't answer. He was at the gym."  Gerekçe: "He" Anna'nın erkek kardeşini gösteriyor.

**163. "Please don't park here. This space is for delivery vans only, from 6 a.m. to 10 a.m." What is the sign about?**  
`rv1-b-a2-05` · A2 · -

- Where vans can buy fuel
- When the shop opens
- **✔ Who can park in a space**
- How much parking costs

Kanıt: "This space is for delivery vans only"  Gerekçe: Tabela bu alana kimin park edebileceğini söylüyor.

**164. "Tom has a big exam on Monday, so he didn't go to the party on Saturday." What did Tom probably do on Saturday?**  
`rv1-b-a2-06` · A2 · Çıkarım

- He went dancing
- He visited friends
- He went to the beach
- **✔ He studied at home**

Kanıt: "Tom has a big exam on Monday, so he didn't go to the party on Saturday."  Gerekçe: Pazartesi sınavı olduğu için partiye gitmedi; büyük olasılıkla çalıştı.

### B1

**165. "The 8:15 train to Leeds will leave from platform 6 instead of platform 2 today." Where should passengers go?**  
`rv1-b-b1-01` · B1 · Ayrıntı

- Platform 2
- Platform 8
- Platform 15
- **✔ Platform 6**

Kanıt: "will leave from platform 6 instead of platform 2 today"  Gerekçe: Bugün tren 6. perondan kalkıyor.

**166. "Please keep your receipt. Without it, we cannot exchange or refund any item." A "receipt" is …** ⟨…⟩  
`rv1-b-b1-02` · B1 · Bağlamda kelime

- **✔ a paper that shows you paid**
- a bag for your shopping
- a card that gives you discounts
- a list of shop rules

Kanıt: "Without it, we cannot exchange or refund any item."  Gerekçe: "Receipt" fiş, ödediğini gösteren kâğıt.

**167. "Anna checked the weather, put on her boots and took her umbrella before she left." What did Anna think?**  
`rv1-b-b1-03` · B1 · Çıkarım

- It would be hot
- She was late
- **✔ It might rain**
- Her boots were old

Kanıt: "put on her boots and took her umbrella"  Gerekçe: Bot ve şemsiye yağmur beklediğini gösteriyor.

**168. "Our café will close for two weeks in August while we redecorate. We'll reopen on 1 September with a new menu." What is the main message?**  
`rv1-b-b1-04` · B1 · -

- The café is closing for ever
- **✔ The café is closing for a short time**
- The café has new opening hours
- The café is selling its old tables and chairs

Kanıt: "Our café will close for two weeks in August"  Gerekçe: Kafe iki haftalığına kapanıyor, sonra açılacak.

**169. "The teacher asked the students to read the article. Most of them found it difficult." What did most students find difficult?**  
`rv1-b-b1-05` · B1 · Bağlaşıklık

- **✔ The article**
- The teacher
- The students
- The question

Kanıt: "Most of them found it difficult."  Gerekçe: "It" makaleyi gösteriyor.

**170. "Since Mark started cycling to work, he has lost five kilos and saves £80 a month on petrol." How did Mark go to work before?**  
`rv1-b-b1-06` · B1 · Çıkarım

- On foot
- By train
- By bus
- **✔ By car**

Kanıt: "saves £80 a month on petrol"  Gerekçe: Benzinden tasarruf ediyorsa önceden arabayla gidiyordu.

### B2

**171. "Despite months of rehearsal, the opening night was a disaster; the lead actor forgot his lines twice." What can we infer?**  
`rv1-b-b2-01` · B2 · Çıkarım

- The actors had not rehearsed
- **✔ Preparation did not prevent problems**
- The play was a great success
- The audience enjoyed the mistakes very much

Kanıt: "Despite months of rehearsal, the opening night was a disaster"  Gerekçe: Aylarca prova yapıldı ama yine de felaket oldu.

**172. "The evidence was inconclusive, so the investigation was kept open." "Inconclusive" means …** ⟨…⟩  
`rv1-b-b2-02` · B2 · Bağlamda kelime

- completely false and invented
- kept secret by the police
- **✔ not clear enough to decide**
- very easy to find

Kanıt: "so the investigation was kept open"  Gerekçe: Kanıt karar vermeye yetmedi; soruşturma açık kaldı.

**173. "Many critics praised the film's music. Its plot, however, was widely seen as weak." What was seen as weak?**  
`rv1-b-b2-03` · B2 · Bağlaşıklık

- **✔ The film's story**
- The film's music
- The critics
- The actors

Kanıt: "Its plot, however, was widely seen as weak."  Gerekçe: "Its plot" filmin konusu; müzik övüldü.

**174. "We regret to inform you that your application has not been successful on this occasion." What is the tone of this message?**  
`rv1-b-b2-04` · B2 · Amaç ve ton

- Angry and rude
- Warm and casual
- Excited and happy
- **✔ Polite and formal**

Kanıt: "We regret to inform you"  Gerekçe: Kalıp ret dili: kibar ve resmî.

**175. "While remote work saves commuting time, many employees report feeling isolated and find it harder to separate work from home life." What is the main idea?**  
`rv1-b-b2-05` · B2 · -

- Remote work saves companies money
- Most people now prefer working from home
- Commuting is the worst part of work
- **✔ Remote work has benefits and drawbacks**

Kanıt: "While remote work saves commuting time, many employees report feeling isolated"  Gerekçe: Hem kazancı hem bedeli var.

**176. "The museum, which reopened in May after a two-year renovation, now attracts twice as many visitors as before." How long was the museum closed?**  
`rv1-b-b2-06` · B2 · Ayrıntı

- **✔ Two years**
- Two months
- One year
- Since May

Kanıt: "after a two-year renovation"  Gerekçe: Müze iki yıllık yenileme için kapalıydı.

