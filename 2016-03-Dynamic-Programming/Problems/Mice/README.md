# Задачата за МИШЛЕТАТА

## Условие

След настъпилия **Апокалипсис** в следствие на избухването на **Голямата Ядрена Война** през 5826г.
на Земята са оцелели **само една малка колония Мишки**. Основната цел на тази колония е да се
размножи до **определената от Големия Компютър степен** и да оцелее в така неприятно стеклите
се обстоятелства.

Колонията се състои от **N на брой женски мишки и M на брой мъжки мишки**.

Мишките пътуват по **Пътят** и посещават различни **бункери**, в които има храна и други полезни за
тях блага. Проблемът е, че **не всички бункери са безопасни**. Част от тях са **облъчени с големи
количества радиация**. Попадайки в такъв бункер **половината мъжки мишки в Kолонията** са
обречени на **моментална и безвъзвратна смърт**. (Закръглява се надолу: ако има 15 мъжки мишки умират 7, 8 оцеляват)

**Размножителния период** настъпва при посещение на **всеки трети бункер**, като **двойките** се
състоят от **една мъжка и една женска мишка**. На **всяка двойка** ѝ се раждат **общо две** малки
мишленца. От **общия брой** новородени мишки **25% са от мъжки пол**, а останалите **75% от женски
пол**. (мъжките мишки се закръгляват надолу, а женските - нагоре)

Размножаване **не се осъществява** когато мишките са попаднали в **радиационно убежище**, т.е.
**този цикъл на увеличение на популацията е безвъзвратно загубен за колонията**.

**Всички** мишки се движат **заедно**, като **задължително стартират от първото убежище**. Колонията
има право **да пропуска 0, 1 или 2 убежища на ход**.
Вашата цел е да помогнете на мишките като им покажете най-оптималния **Път** за достигане на
**желаната популация** (т.е. с възможно **най-малък брой** посетени убежища). За да е още по-трудно
**Големият Компютър** поставя и още едно условие – **да бъдат посетени поне половината убежища
от Пътят**. (Закръглява се надолу: ако **Пътят** е дълъг **15 убежища** мишките трябва да посетят **поне 7 от тях**). Популацията,
която достигне Колонията Мишки **трябва да бъде по-голяма или равна на зададената** от **Големия
Компютър**, но никога по-малка.

## Вход
Входните данни ще бъдат дадени на конзолата.

На първият ред ще бъде дадено числото **N** – **броят женски мишки в колонията**.
На вторият ред ще бъде дадено числото **M** – **броят мъжки мишки в колонията**.
На третия ред ще бъде дадено числото **P** – **очакваният брой мишки зададена от Големия Компютър**.
На четвъртия ред ще бъде даден **Пътят** със отбелязани съответните бункери. С '\*' са отбелязани
безопасните убежища, а с '@' – убежищата облъчени с радиация.

## Изход
Изходните данни ще се извеждат на конзолата.
На единствения ред на стандартния изход **изкарайте минималният брой посетени убежища до
достигане на желаната популация**.

## Ограничения
- **N** и **M** ще бъдат цели числа между **1** и **1000**, включително.
- **P** ще бъде цяло число от **минимум началния брой на мишките до 10 000 000**.
- Пътят ще включва само символите **@** и **&#42;** и винаги ще бъде с достатъчна дължина и съдържание за да се постигне посочената популация.
- Позволено време за работа на програмата: **0.3 секунди**. 
- Позволена памет: **16 MiB**.

## Примери

### Вход
```
2
3
17
*@***@*@***@*
```

### Изход
```
6
```

### Обяснение
```
Желаната популация се достига при 6-тото посещение на убежище.
```

### Вход
```
4
4
28
******@@@@@@***
```

### Изход
```
9
```

### Обяснение
```
В този случай желаната популация 28 се достига още на 6-тото
Посещение на убежище, но дължината на пътя е 15 убежища
т.е. мишките трябва да посетят поне 15/2 = 7 убежища. Те
имат право да пропускат 0, 1 или 2 убежища, но пак не могат
да избегнат облъчените с радиация убежища и популацията
им поне на два пъти се намалява. След първото посещение на
радиационно убежище колонията, която до този момент е
достигнала 28 (19 женски и 9 мъжки) мишки намалява на 24
мишки (19 женски и 5 мъжки), а след второто - 22 мишки (19
		женски и 3 мъжки) . След второто радиационно убежище
мишките вече са посетили общо 8 убежища (в най-
		оптималния случай, т.е. с прескачане) и на 9-тото посещение
са в размножителен период и колонията става общо 28
мишки (24 женски и 4 мъжки), което е желаната популация.
```

### Вход
```
2
3
17
*@***@@@@@***@*
```

### Изход
```
9
```
