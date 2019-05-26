# Некоторые допущения 

Не много предисловия. Ввиду того что я использую для погрузки моделей Asset Bundles (бандлы), а потом эти самые бандлы связываю на клиенте с маркерами, есть несколько правил, чтобы на клиенте ничего не сломалось. Да я понимаю, что это не самое лучшее решение, которое можно реализовать, но к сожалению, пока только так. К счастью правила не такие жесткие и соблюсти их довольно легко т.к. касаются они только имен и структур папок.

Правила, длинно и формально:
- Имена при создании бандла в unity должны быть в формате name/ab (где ab - это сокращение от Asset Bundle, а name - имя модели). Например: модель cowboy (имя префаба в unity), соответственно Asset Bundle - cowboy/ab.
	
- Уникальные названия должны иметь только дирректории. Т.е. если мы грузим модель шарика (ball), то структура должна выглядеть так: ball/ab
	
- На клиенте идет подгрузка двух файлов ab.manifest и ab. Наличие обоих обязательно в папке, путь до которой указан в JSON файле. НО! путь до .manifest писать не нужно. Я его сам скачаю. Почему так? да потому что unity генерирует 2 файла, один без второго ничто, а перегружать логику JSON не хочу.
	
- Имена моделей должны совпадать с именами маркеров. Т.е. зашли на сайт вуфории, там начали загружать в database маркеры. Так вот имена маркеров должны соответствовать именам моделей, а в данных реалиях именам папок (т.к. все бандлы имеют имена ab). Загружаем cube, маркер должен иметь имя cube. Грузим 3 модели cube, ball, torus? - Марверы должны иметь имя cube, ball, torus. Все просто!

Правила, коротко и быстро:
- Имя префаба == папке бандла
- Все файлы бандла == ab
- Имя марки для модели == имени префаба
- В папке с именем префаба должно лежать два файла: ab и ab.manifest

JSON (Vuforia) выглядит так:

```
{
"models" : ["3dmodels/gunfire/ab","3dmodels/knight/ab"],
"markers" : {"xml": "markers/knight.xml", "dat" : "markers/knight.dat"}
}
```

JSON (Maxst) выглядит так, разница лишь в том, что в этом фреймворке конечные маркеры выглядят как файлы с расширением .2dmap. Соответственно качать нужно их все:

```
{
"models" : ["3dmodels/heart/ab","3dmodels/lantern/ab","3dmodels/fontain/ab","3dmodels/icecream/ab","3dmodels/flower/ab","3dmodels/music/ab","3dmodels/hellicopter/ab","3dmodels/harp/ab","3dmodels/butterfly/ab","3dmodels/horse_knight/ab"],
"markers" : ["markers/butterfly.2dmap","markers/flower.2dmap","markers/fontain.2dmap","markers/harp.2dmap","markers/heart.2dmap","markers/hellicopter.2dmap","markers/horse_knight.2dmap","markers/icecream.2dmap", "markers/lantern.2dmap", "markers/music.2dmap"]
}
```
_ _ _


Для самых маленьких и глупых (только не показывайте это менеджерам) просто приложу скриншоты того, как это должно выглядеть.

У меня есть 2 модели:

1. gunfire
2. knight

![gunfire](/chivalryTest/images/gunfire.png)

![knight](/chivalryTest/images/knight.png)

Не забывайте! Имена бандлов соответствуют именам префабов.

Вот так в итоге выглядит конечный каталог. Можно посмотреть [ТУТ]

![dirStructure](/chivalryTest/images/dirStructure.png)

Вот так должен выглядель database на сайте вуфории.

![vuforiaDatabase](/chivalryTest/images/vuforiaDatabase.png)


[ТУТ]:/chivalryTest/3dmodels
