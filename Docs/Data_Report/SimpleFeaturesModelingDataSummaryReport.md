# General summary of the data

A dataset for modeling the clickbait classification problem, where the news articles are represented using simple features.<br>

## Modeling

The most important part of the news article for the clickbait classification problem is the headline of the article. In this dataset each headline is represented by a vector of variables that indicate simple features of the headline.

### Features set

The set of features that were taken into consideration:<br>
1. Presence/Number of some punctuation marks.
2. Presence/Number of numbers in the title.
3. Whether the title contains a number.
4. Presence/Number of question words.
5. Presence/Number of commonly used phrases in the clickbait headlines.
6. Presence/Number of emotional words in the title.
7. Presence/Number of forward-reference: Demonstratives pronouns, third person personal pronouns, ...

## Relationship between explanatory variables and target variable

### Common words & phrases

It’s obvious that there are many words and phrases commonlyused in a clickbait headline e.g. :<br>
<br>
**"أسباب"**<br>
7 _اسباب_ هامه للقيام بالتمارين الرياضية اثناء فتره الحمل<br>
6 _اسباب_ تجعل من جزيرة ميكونوس في اليونان وجهتك الافضل لقضاء عطله عيد فطر صيفيه مميزه<br>
العمل من المنزل مفيد لصحتك.. اليك _الأسباب_<br>
**"شاهد"**<br>
_شاهد_ ماذا يأكل البشر كل يوم حول  العالم!<br>
_شاهد_ ماذا فعل اعضاء المنتخب الجزائري عقب فوزهم بكاس الامم الأفريقية.. «صوره مؤثره تشعل مواقع التواصل الاجتماعي<br>
عاجل... مفاجأة صادمه للجميع.. هذا ما حدث قبل قليل في السعودية بشأن الداعية سلمان العودة.. (_شاهد_ الصورة)<br>
<br>
**Common words/phrases determination**:<br>
<br>
We’ll use our training dataset to discover these words and phrases. Following are word-couldsvisualizethe densitiesof frequent words (1-gram) and phrases (2 -gram, 3-gram, 4-gram) in our clickbait headlines in the training dataset.<br>
**Frequent 1-gram**:
<br>
![](img/modeling/simple/comm_1_gram.png)
<br>
**Frequent 2-gram**:
<br>
![](img/modeling/simple/comm_2_gram.png)
<br>
**Frequent 3-gram**:
<br>
![](img/modeling/simple/comm_3_gram.png)
<br>
**Frequent 4-gram**:
<br>
![](img/modeling/simple/comm_4_gram.png)
<br>
We are not going to use common words from the non-clickbait headlines as features, because this type of headlines has unlimited variations which are so hard to be covered in the training dataset, so using this kind of features may cause problems in the generalization on the real-world examples. However, we’re going to show the frequent words in the non-clickbait headlines as a part of the data exploration process. Following is a word-could visualizes the densities of the frequent words (1-gram) in our non-clickbait headlines in the training dataset.
<br>
**Frequent 1-gram**:
<br>
![](img/modeling/simple/uncomm_1_gram.png)
<br>

### Number Usage
It’s common to usenumbers in the clickbait headlines especiallyas the first word e.g. :<br>
<br>
_12_ فيلما يجب ان تشاهدهم للممثل... دانييل داي لويس <br>
_10_ افلام سينمائية عن ثورات الشعوب تستحق المشاهدة<br>
اكتشف _27_ بديلا في مشاهد الخطر لأكبر نجوم هوليوود<br>
<br>
The following graphconfirmsthe effectivenessof this featuresaccording to our training dataset, where we’re taking both the numericand textual numbers into account:
<br>
![](img/modeling/simple/num_usage.png)
<br>
According to the previous graph:<br>
<br>
The average of numbers in a clickbait headline ~ 0.25, while the average of numbers in a non-clickbait headline ~ 0.07, because of this large difference we can consider “the count of the numbers in the headline” as an informative feature to differentiate between clickbait and non-clickbait headlines.<br>
<br>
The percent of the clickbait headlines that contain numbers and one of them is mentioned in the beginning of the headline 31%, while this percent is only 15% for the non-clickbait headlines, so the “the presence of a number in the beginning of the headline” can be considered as an informative feature to differentiate between clickbait and non-clickbait headlines too.<br>

### Punctuation Usage

It’s very common to over-formatting the clickbait headlines by using a lot of punctuation, for especially specific types like exclamation mark, question mark, full-stops, quotations... e.g. :<br>
<br>
مشاجرة عنيفة وتبادل مباشر للاتهامات والفاظ نابيه بين __”__اصاله__”__ و __”__احلام__”..__ والأخيرة تنهار على الهواء وتشتم الجميع__...__ شاهد<br>
تعرفوا على يونا المغنية المسلمة المحجبة التي حققت نجاحا عالميا في الموسيقى والموضة__..__ شاهدوا الصور والفيديو__!__<br>
بالفيديو __:__ موقف محرج على الهواء__،__ شاهد ماذا فعل الكلب ليفسد النشرة الجوية __!!__<br>
<br>
The following graphs show statistics related to the punctuation marks in the headlines in our training dataset:
<br>
![](img/modeling/simple/punc_usage.png)
<br>
As the average of the punctuation marks per clickbait headline is ~ 2.09 and the percent of the clickbait headlines contain punctuation marks is ~ 62%, while the average of the punctuation marks per the non-clickbait headline is ~ 0.56 and the percent of the non-clickbait headlines contain punctuation marks is 2%, “the number/presence of punctuation in the headline” can be considered an informative feature to differentiate between clickbait and non-clickbait headlines.
<br>
![](img/modeling/simple/punc_usage2.png)
<br>
The previous graph shows the percent of the usage of each punctuation marks type in the both types of headlines. Where the punctuation marks were normalized i.e. (‘, “,’...) were normalized to “, (?, ‫)؟‬ were normalized to ? and so on..<br>
<br>
The graph proves that the type of the used punctuation marks plays a role in differentiating between the two headline types and that according to our dataset, exclamation mark and full-stops play the biggest role in distinguishing the clickbait headlines, while the quotation marks seem to be effective in distinguishing the non-clickbait headlines!<br>
<br>

### The Presence of a Question

Question is a commonly used pattern in the clickbait headlines e.g. :
<br><br>
_كيف_ تحب الدراسة وتنمي شغف التعلم بداخلك؟ 5 خطوات تساعدك على فعل ذلك
فقالوا...انا مثقف!-_كيف_ تحكم على ثقافه أحدهم؟
قمر اوروبا... _هل_ يحقق حلم الحياة الاخرى في النظام الشمسي لدرب التبانة؟
<br>
The following graphs show statistics related to the question words present in the headlines:
<br>
![](img/simple/q_words_usage.png)
<br>
<br>
![](img/modeling/simple/q_words_usage2.png)
<br>
According to these graphs the presence of question words in the headline doesn’t seem to be an informative feature. However, the types of the used question words seem to be able to differentiate between the headline types. Where ( ‫ماذا‬ ، ‫هل‬ ) play the biggest role in distinguishing the clickbait headlines, while (‫أين‬ ،‫)كيف‬ seem to be effective in distinguishing the non-clickbait headlines.<br>

### Pronouns

Clickbait headlines usually use pronouns to refer to objects, persons and events.

### Demonstrative Pronouns

e.g. :<br>
<br>
انتبه... _هذا_ ما تفعله الوجبات السريعة في جسمك<br>
عائض القرني يعاود الظهور ويفجر مفاجأة: _هذا_ ما وعدنا به الملك سلمان<br>
انواع الطلاب في الجامعة، اي نوع من _هؤلاء_ انت؟<br>
<br>
The following graphs show statistics related to the demonstrative pronouns present in the headlines, where the affixes were segmented from the pronouns.<br>
<br>
![](img/modeling/simple/demon_usage.png)
<br>
<br>
![](img/modeling/simple/demon_usage2.png)
<br>
According to the previous graphs seems that the presence of a demonstrative pronoun can be considered as a good feature where the percent of the clickbait headlines that contain demonstrative pronouns is 9% while the percent of the non-clickbait headlines that contain demonstrative pronouns is just 1%. The types of the used demonstrative pronouns in the headlines are shown to have an effect in distinguishing between the types of the headlines too.<br>

### Relative Pronouns

هل تستطيع حل هذا اللغز _الذي_ فشل فيه 20الف شخص؟<br>
اليزابيث هولمز... الشقراء _التي_ جمعت المليارات من وخز الابر<br>
<br>
The following graphs show statistics related to the relative pronouns present in the headlines, where the affixes were segmented from the pronouns.<br>
<br>
![](img/modeling/simple/rel_usage.png)
<br>
<br>
![](img/modeling/simple/rel_usage2.png)
<br>
We can consider “the presence of a relative pronoun” as a good feature since the percent on clickbait headlines contain relative pronoun is 5% while the  percent of the non-clickbait ones contain relative pronouns is only 1%. However, the types of the relative pronouns that present in the headline don’t seem to play any role in distinguishing between the two types of the headlines.<br>

### Personal Pronouns

**Second-Person Pronouns**<br>
<br>
It’s common in the clickbait headlines to talk directly to the user. However, second-person pronouns are rarely used in Arabic.<br>
<br>
The following graph shows statistics related to the second-person pronouns present in the headlines, where the affixes were segmented from the pronouns.<br>
<br>
![](img/modeling/simple/sec_pron_usage.png)
<br>
Both of the percent is low; thus, I don’t consider the presence of a second-person pronoun as an informative feature.<br>
<br>
**First and Third Person Pronouns**<br>
<br>
The following graph shows statistics related to the first and third pronouns present in the headlines, where the affixes were segmented from the pronouns.<br>
<br>
![](img/modeling/simple/first_third_pron_usage.png)
<br>

### Negation Formula

Negative words are often used in the clickbait headlineslike (لا، لم، لن) e.g. : <br><br>
افكار _لا تخطر_ على بالك عن استخدام البلالين<br>
ساحة جامع الفنا جمال مغربي _لا يقاوم_!<br>
نصائح للشباب في مقتبل عمرهم ... _لا تفوتها_!<br>
 "_لن تصدق_ مدى الشبه " شاهد شبيهه الفنانة اليمنية بلقيس<br>
جنون "عيد الحب " كما _لم تعرفه_ من قبل!<br>
<br>
The following graphs show statistics related to the negationwordspresent in theheadlines, where the affixes were segmented from the words.<br><br>
<br>
![](img/modeling/simple/neg_usage.png)
<br>
<br>
![](img/modeling/simple/neg_usage2.png)
<br>
The percent of the clickbait headlines that contain negation pattern is ~ 8%, while the percent of the non-clickbait headlines that contain negation pattern is only ~ 3%, then we can consider the presence of a negation pattern as a good feature. However, the types of the presented negation words don’t seem to have any effect on the classification process.<br>

### Time Adverbs

Clickbait headlines usually contain time adverbs like ( ...،‫مع‬ ،‫حين‬ ،‫وقد‬ ،‫ما‬ ‫عند‬ ،‫عند‬ ) e.g. : <br>
<br>
فيديو.. لن تصدق ماذا فعل هذا الكلب _عند_ رؤية قطه<br>
صور استعمالات منزليه غريبه لم تعلم بها من _قبل_ للمايونيز... ستدهشك<br>
فيديو مرعب: _لحظه_ قتل رجل لزوجته في مراب تحت الأرض<br>
<br>
<br>
![](img/modeling/simple/adv_usage.png)
<br>
The percent of the clickbait headlines that contain time adverbs is~11%, while the percent of the non-clickbait headlines that contain time adverbs is only ~ 6%, then we can consider the presence of a time adverbsas a good feature.<br>

### Speaking toThe Reader

It’s commonly used in the clickbait headlines, and can be captured by the presence of many words like (عليك، إليك، إياك...) e.g. : <br>
<br>
لكل من يعاني من الم الظهر... _عليك_ باليوغا<br>
تعلم لغة اجنبيه مع العائلة والاصدقاء ... متعه وافاده _اليك_ كيف تستغلها<br>
الاماكن الاكثر سريه على سطح الارض.  .اياكوالاقتراب منه<br>
<br>
<br>
![](img/modeling/simple/speak_usage.png)
<br>
The percent of the clickbait headlines that contain those words is ~ 6%, while the percent of the non-clickbait headlines that contain those words is only ~ 1%, then we can consider this as a good feature.<br>

### Other Stopwords

Many other stopwords are commonly used in clickbait titles like ( ... ، ‫كل‬ ،‫فقط‬ ،‫قد‬ ) e.g. : <br>
<br>
اربعه اشياء _قد_ لا تعرفها عن التسويق عبر لينكدان!<br>
ما هي عمله ايوتا ... _كل_ ما تودون معرفته عنعمله ايوتا IOTAالمشفرة<br>
اقوى 20لعبه رعب على جميع المنصات لأصحاب القلوب القاسية والاحاسيس الميتة _فقط_!<br>
<br>
![](img/modeling/simple/stop_usage.png)
<br>
So, this feature doesn’t seem to be effective.<br>

### Emotional Words

Clickbait headlines often use emotional words.<br>
<br>
The following graphs show statistics related to the emotional words present in the headlines
<br>
![](img/modeling/simple/emotion_usage.png)
<br>
<br>
![](img/modeling/simple/emotion_usage.png)
<br>
Obviously, the clickbait headlines contain more emotional words and the “surprise” emotion plays the biggest role in distinguishing the clickbait type.
<br>
<br>
The lexicon that was used to find the emotional words id downloadable from [here](https://github.com/motazsaad/emotion-lexicon/tree/master/arb).



