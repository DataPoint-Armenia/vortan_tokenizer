# [ՀայՆիշ](http://armtreebank.yerevann.com/tokenization/process/)

### Տեքստի հատույթավորում և բառանիշավորում

Բնական լեզվով տեքստերի ավտոմատ մշակման համակարգերի մեծ մասը ենթադրում է, որ տեքստերն ի սկզբանե մասնատված են նախադասությունների և բառերի, այսինքն` դրանք արդեն իսկ հատույթավորված են։ Հատույթավորումն, այսպիսով, տեքստի մշակման առաջնային փուլն է և սկզբունքային՝ այսպիսի համակարգերի առջև դրվող խնդիրները լուծելու համար։ 

Տեքստի հատույթավորումն ապահովվում է գրանշանային վերլուծության միջոցով, որը հիմնվում է տվյալ լեզվին բնորոշ ուղղագրական գրեթե բոլոր առանձնահատկությունները ներառող, շատ թե քիչ մանրամասն ու հստակ կանոնների վրա։ Ենթադրվում է, որ այդպիսի կանոնները հաշվի են առնում ստանդարտ (արդեն իսկ կետադրված) տեքստերում հանդիպող իրական դեպքերը։ Գրանշանային ամենապարզ վերլուծությունը տեքստի՝ բացատներով մասնատումն է՝ բացատները չհամարելով բառանիշներ, և մասնատված հաջորդականությունների խմբավորումը վերջավոր այնպիսի դասերում, որոնք տառեր չեն պարունակելու (կետադրական նշաններ, թվանշաններ և այլն)։ Վիճելի կամ ոչ միանշանակ դեպքերում (մասնավորեցնող կանոններ) այսպիսի համակարգերը միշտ կանգնում են խնդրի առջև՝ հաջորդականությունը գնահատել մե՞կ, թե մի քանի բառանիշ։

Գրանշանային վերլուծությունը «ՀայՇտեմ»-ում ևս ենթադրում է մուտքային տեքստի (որպես UNICODE նշանների հաջորդականություն) մասնատում լեզվաբանական հետագա վերլուծության համար անհրաժեշտ հատույթների՝ նախադասությունների և բառանիշների (Token)։ Բառանիշները, որոնք բառաձևեր (կամ բառաձևերի հաջորդականություններ) են, ենթակա են ձևաբանական պիտակավորման։ Բառաձևեր չգնահատվող բառանիշները պիտակավորվում են որպես համապատասխան էությունների դասեր՝ կետադրական նշաններ, թվանշաններ, տառա-թվանշանային արտահայտություններ, կայքէջերի հասցեներ և այլն։ Նախադասությունները ենթակա են ծանոթագրման շարահյուսական կախվածությունների ծառերի տեսքով։

#### «ՀայՇտեմ»-ի գրանշանային վերլուծության մոդուլը՝ «ՀայՆիշ»-ը, հենվում է հետևյալ կանոնների վրա.

 -  Բացատները միշտ բաժանում են բառանիշներ, ինչը ենթադրում է, որ չեն կարող լինել բացատներ պարունակող բառանիշներ։
 -  Կետադրությունը նույնպես ենթակա է բառանիշավորման։ «Ոչ գծային» կետադրական նշաններ ( ՞ ՜ ՛ ՚ ՟ ) պարունակող հաջորդականությունները մասնատվում են որպես բազմաբառ բառանիշներ (multiword tokens). հմմտ. CoNLL-U ձևաչափում՝
	1-2 ինչո՞ւ
	1 ինչու
	2 ՞
 -  Միմյանց հաջորդող կետադրական նշանները ( ...»,— ) առանձնացվում են որպես անջատ բառանիշներ { ... } { » } { , } { — }։ Միևնույն ժամանակ, կախման կետերը { ... } և բազմակետերը { .... } ներկայացվում են որպես մեկ կետադրական նշան, հետևաբար՝ մեկ բառանիշ, ոչ թե երեք կամ չորս առանձին կետերից բաղկացած արտահայտություն։ Բացառություն են կազմում մի քանի նշաններից բաղկացած emoji և smiley { :) }, { ^_^ } և նման տիպի հաջորդականությունները, որոնք դիտարկվում են որպես մեկ բառանիշ։ Այլալեզու բազմանիշ կետադրական նշանները { ?! } դիտարկվում են որպես մեկ բառանիշ։
 -  Ներքին կետադրություն ունեցող հատուկ անունները համարվում են մեկ առանձին բառանիշ՝ { Սայաթ-Նովա }, { Մելիք-Հակոբյան }։ Այսպիսի անունները կարող են պարունակել բազմաթիվ այլ նշաններ (@, #, $, ...), օր.՝ { Դ!ԵՄ.ԵՄ } { U!com }, և վերլուծության հաջորդ փուլերում դրանք նպատակահարմար է մեկնաբանել ինչպես այս դասին պատկանող մյուս բոլոր անվանումները (քաղաքների, ընկերությունների, բրենդների և այլն անվանումներ)։
 -  Չակերտներում վերցված արտահայտություններին միության գծիկով հաջորդող երկրորդական ձևույթները (թեքույթ) միության գծիկի հետ միասին գնահատվում են որպես մեկ միասնական բառանիշ։ Օր.՝ «Երկիր Նայիրի»-ից, { « } { Երկիր } { Նայիրի } { » } { -ից }։
 -  Հապավական բաղադրությունները (հապավումները, համառոտագրությունները), համարվում են մեկ անջատ բառանիշ՝ { ԵՊՀ }, { ՄԱԿ }, { բուհ }, { ֆր. }, { ռուս. }, { հայ. }, { փխբ. }, { հնց. } { թ. }, { ժ. }, { ևն }, { պրն }։ Համառոտագրվող բաղադրիչներին հաջորդող՝ կրճատման նշան հանդիսացող կետը համարվում է բառանիշ-համառոտագրության մաս և ոչ թե առանձին բառանիշ (եթե չի համընկնում միջակետի հետ, երբ բառանիշավորվում է միջակետը)։ Հապավումներին, համառոտագրություններին միության գծիկով հաջորդող վերջածանցները կամ թեքույթները չեն մասնատվելու և դիտարկվելու են որպես մեկ միասնական բառանիշ, օր.՝ { ՀՀԿ-ականներից }, { թ.-ին }, { թթ.-երին }, { դդ.-ում } և այլն։
 -  Բացատը հապավումները (համառոտագրությունները) բաժանում է երկու կամ ավելի բառանիշների։ Հմմտ. տառա-բառային հապավումները՝ { Հայկական } { ԽՍՀ }, կամ երկբաղադրիչ համառոտագրությունները՝ { Հ. } { Գ. }, { ս. } { թ. }, { Հ. } { Թ. }։
 -  Թվանշա-տառային արտահայտությունները, որոնցում թվանշանին հաջորդում է միության գծիկ (ենթամնա) ու հայերեն տառեր, դիտարկվում են որպես մեկ միասնական բառանիշ, լինեն դրանք թվականներ, ածականներ կամ ցանկացած այլ տիպի արտահայտություն։ Օր.՝ { 1-ին }, { 2-րդ }, { 4-ը }, { 1000-ական }, { 1950-ականներին }, { 20-ամյակ }, { 1700-ամյա }։
 -  Թվանշանները { 265 }, նաև այնպիսիք, որոնք պարունակում են ստորակետ կամ միջակետ՝ որպես ամբողջի և մասի բաժանարար { 2,15 } , { 2.15 }, կոտորակները { 2/3 }, մաթեմատիկական կամ քիմիական բանաձևերը, էլ. փոստի { muster@muster.am }, կայքէջերի հասցեները { https://github.com }, թվիթների տիպի անունները { @gov_am } դիտարկվում են որպես մեկ ամբողջական բառանիշ։ Այսպիսի արտահայտությունների կառուցվածքի վերլուծությունն իմաստ չունի. կարևոր է միայն այս բառանիշների դասը։
 -  Թվանշաններին նախորդող կամ հաջորդող հատուկ նշանները (ներառյալ՝ + կամ -), չափման միավորները, եզրույթներ արտահայտող նշանները (կմ, $, % և այլն) առանձնացվում են որպես անջատ բառանիշներ, եթե անգամ դրանց միջև բացատ չկա։ Օր.՝ €200, 18,25%, +35°С, 135կմ/ժ — { € } { 200 }, { 18,25 } { % }, { + } { 35 } { °С }, { 135 } { կմ/ժ }։
 -  Ժամանակ ցույց տվող թվանշանային արտահայտությունները՝ ժ. 20:55 կամ ժ. 20.55, բաժանվում են առանձին բառանիշերի. այս դեպքում երեք՝ { 20 } { : } { 55 }, { 20 } { . } { 55 }։
 -  Ամիս-ամսաթվեր, տարեթվեր ցույց տվող թվանշանային արտահայտությունները 24.04.1965 նույնպես բաժանվում են առանձին բառանիշների. այս դեպքում հինգ՝ { 24 } { . } { 04 } { . } { 1965 }։
 -  Վերոնշյալ կանոններով չնախատեսվող բոլոր դեպքերը (գծիկով կամ անջատ գրվող վերլուծական բառերը, մասնավորապես՝ հարադրությունները, հարադրական բարդությունները) բառանիշավորվում են «ուղղագրական կանոններին» համաձայն և վերլուծվում են որպես «բազմաբառ արտահայտություններ» (MWe, multiword expressinons), քանի դեռ դրանք, որպես հատուկ դասեր, չեն ընդգրկվել «ՀայՇտեմ»-ի (բացատրական, ուղղագրական) բառարան-տեղեկագրերում։

#### Նախադասությունների սահմանազատում

 -  Նախադասության սահմանն անցնում է նախադասության ավարտը նշող կետադրական տերմինալ նշանից (վերջակետ { ։ }, կախման կետեր { ... }, բազմակետ { .... }) հետո՝ հաջորդող մեծատառից կամ պարբերության ավարտից առաջ։

Ընդ որում, բոլոր այն հաջորդականությունները, որոնք սկսվում են մեծատառով և չեն ավարտվում որպես տերմինալ գնահատված նշաններից ոչ մեկով (վերնագիր, կոչ, պարբերականի, ստեղծագործության անվանում, թվարկումներ և այլն), նույնպես գնահատվում են որպես առանձին նախադասություն. դրանց սահմանը նույնպես անցնում է հաջորդող մեծատառից կամ պարբերության ավարտից առաջ։

 -  Հեղինակային խոսքը, լինի նախադաս, միջադաս, թե հետադաս, չի առանձնացվում ուրիշի ուղղակի, մեջբերվող խոսքից։

Հեղինակային ու մեջբերվող խոսքը վերլուծության հաջորդ փուլերում ծանոթագրվում են շարահյուսական հատուկ տիպի կապի միջոցով (parataxis), որն էլ ապահովում է տեքստի իմաստային ավարտունությունը (| — նշում է նախադասության սահմանը, || — նշում է այդպիսի հատվածների ենթադրյալ սահմանները)։
Օր.՝
— Ի՞նչը՝ ո՞նց թե...| Տնաշեն, ամբողջ աշխարհն է խոսում. Տանուտերանց Գևորգը երկու օր է մեռած, տղերքից ոչ մեկը չկա, որ հորը թաղի։| Շորերը հագցրել, պառկեցրել են դագաղում ու սպասում են...||
Գառնիկի աչքերը սառել էին Վարանցովի բերանին։|
— Մարդ աստծո,— շշնջաց,— բարլուսախառն միանգամից էդքան վատ բան բերանդ ո՞նց զորեց ասել։||

Կամ 

«Վրաս ցեխ ու ճիմ լցրու»,— իր վրա գոռում է։|| Ինքը շշկլած կանգնել է ու չգիտի ի՞նչ անի, ո՞նց վարվի։| Հետո լեզուն բացվեց. «Ախր, այ Գևորգ,— ասաց,— հագինդ նախագահի նվիրած կոստյումն է»։ || «Տո, նախագահի մերն էլ, քո մերն էլ,— համբերությունը հատած գոռաց,— դու ցեխը լցրու, ցեխը...»։||

(Հացի փորձություն: [Պատմվածքներ, վիպակ] / Վ. Զ. Սարգսյան։ Խմբ.՝ Վ. Մ. Մուղնեցյան, Ա. Է. Մորիկյան, նկարիչ՝ Ֆ. Ա. Գուլանյան.— Եր.։ Յավրուհրատ, 2015.— 291 էջ)։

 -  Չակերտներում մեջբերվող ուղղակի խոսքը նախադասությունների սահմանազատվում է ըստ հիմնական կանոնի՝ տերմինալ նշան՝ հաջորդող մեծատառից կամ պարբերության ավարտից առաջ։ Ընդ որում, հնարավոր են դեպքեր, երբ բացող չակերտը մի նախադասության մեջ է, իսկ փակողը հաջորդում։ Այսպիսի սահմանազատումը թույլ է տալիս պահպանել շարահյուսորեն ավարտուն կառույցները։

Օր.՝ Վեպի մասին «Հայ վեպի պատմություն» գրքի հանձնարարականում գրված է, որ «վեպը արվեստի ինտելեկտուալացման ամենաբարձր աստիճանն է։| Վեպը էպիկական ստեղծագործություն է, որի մեջ պատումը կենտրոնացված է առանձին անհատի ճակատագրի վրա, նրա բնավորության և ինքնագիտակցության ձևավորման և զարգացման վրա»։|
(«Վեպ», Վիքիպեդիա, 2017թ. https://hy.wikipedia.org/wiki/%D5%8E%D5%A5%D5%BA )

 -  Եթե չակերտներում մեջբերվում է անվանում (գեղարվեստական կամ գիտական երկերի վերնագրեր, թերթերի անուններ և այլն), որում առկա են տերմինալ նշաններ, ապա անվանման ներսում սահմաններ չեն դրվում։
Օր.՝ Խաչատուր Աբովյանի «Վերք Հայաստանի։ Ողբ հայրենասեր»-ի վեպը հրատարակվել է 1858թ.։|

## Usage
```python
#import Tokenizer
from tokenizer import Tokenizer

#write some text
text = 'Ես սիրում եմ python:'

#tokenization
T = Tokenizer(text)
T.segmentation().tokenization()

#print result
print(T)
```
