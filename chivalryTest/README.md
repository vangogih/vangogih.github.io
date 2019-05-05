# Некоторые допущения.

Не много предисловия. Ввиду того что я использую для погрузки моделей Asset Bundles (бандлы), а потом этом самые бандлы связываю на клиенте с маркерами, есть несколько правил, чтобы на клиенте ничего не сломалось. Да я понимаю что это не самое лучшее решение, которое можно реализовать, но к сожалению пока только так. К счастью правила не такие жесткие и соблюсти их довольно легко т.к. касаются они только имен и структур папок.

Правила длинно и формально:
- Имена при создании бандла в unity должны быть в формате name/ab (где ab - это сокращение от Asset Bundle, а name - имя модели). Например: модель cowboy (имя префаба в unity), соответственно Asset Bundle - cowboy/ab.
	
- Уникальные названия должны иметь только дирректории. Т.е. если мы грузим модель шарика (ball), то структура должна выглядеть так: ball/as
	
- На клиенте идет подгрузка двух файлов ab.manifest и ab. Наличие обоих обязательно в папке, путь до которой указан в JSON  файле. НО! путь до .manifest писать не нужно. Я его сам скачаю. Почему так? да потому что unity генерирует 2 файла, один без второго ничто, а перегружать логику JSON не хочу.
	
- Имена моделей должны сопадать с именами маркеров. Т.е. зашли на сайт вуфории, там начали загружать в database маркеры. Так вот имена маркеров должны соответствовать именам моделей, а в данных реалиях именам папок (т.к. все бандлы имеют имена ab). Загружаем cube, маркер должен иметь имя cube. Грузим 3 модели cube, ball, torus? - Марверы должны иметь именя cube, ball, torus. Все просто!

Правила коротко и быстро:
- Имя префаба == папке бандла
- Все файлы бандла == ab
- Имя марки для модели == имени префаба
- В папке с именем префаба должно лежать два файла: ab и ab.manifest

--

Для самых маленьких и глупых (только не показывайте это менеджерам) просто приложу скриншоты того, как это должно выглядеть.

У меня есть 2 модели:

1. gunfire
2. knight

[gunfire](\chivalryTest\_images\gunfire.png)

[knight](\chivalryTest\_images\knight.png)

Не забывайте! Имена бандлов соответствуют именам префабов.

Вот так в итоге выглядит конечный каталог. Можно посмотреть [ТУТ]

[dirStructure](\chivalryTest\_images\dirStructure.png)

Вот так должен выглядель database на сайте вуфории.

[vuforiaDatabase](\chivalryTest\_images\vuforiaDatabase.png)


[ТУТ]:/chivalryTest/3dmodels