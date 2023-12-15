---
layout: post
title: TypeScript tsconfig.json (пишем свою игру)
feature-img: "assets/img/typescript/typescript-tsconfig-json/typescript-tsconfig-json-title.jpg"
thumbnail: "assets/img/thumbnails/typescript/typescript-tsconfig-json/typescript-tsconfig-json-title.jpg"
tags: [TypeScript, Game, Colorballs]
categories: Colorballs
---

Наших знаний уже должно быть достаточно для небольшого проекта. 
Просто учить язык скучно. Напишем игру. Простенькую логическую игру с шариками. 
Игра будет называться `tscolorballs`.   
Сначала создадим файл HTML для нашей игры. Дадим ему имя `tscolorballs.html`. Вставим туда следующее содержимое: 

{% highlight html linenos %}
<!DOCTYPE html>
<html>
  <head><title>TypeScript Color Balls</title></head>
  <body>
    <script src="tscolorballs.js"></script>
  </body>
</html>
{% endhighlight %}

У нас проект будет состоять из нескольких файлов. Будем делать всё по-научному. Для организации проектов в TypeScript 
создают файл `tsconfig.json`. Этот файл описывает структуру проекта. В `tsconfig.json` впишем следующее содержимое: 

{% highlight json linenos %}
{
  "compilerOptions": {
    "outFile": "tscolorballs.js"
  },
  "include": [
    "src/**/*"
  ]
}
{% endhighlight %}

Что мы здесь описали? В принципе всё просто: 

- **_include_** - указывает, какие файлы нужно включать в проект. Можно использовать маски, где `**/` - это рекурсивный поиск 
по всем подкаталогам, а `*` - это любой файл, `?` - это любой символ. 
- **_compilerOptions_** - здесь в **_outFile_** мы указываем конечный файл, куда будет собираться весь обработанный компилятором код. 

Теперь создайте каталог `src`, а в нём подкаталог `core`. В `core` создайте файл `Engine.ts` со следующим содержимым: 

{% highlight typescript linenos %}
class Engine {
}
{% endhighlight %}

Структура файлов на текущем этапе должна получиться примерно такая: 

- src/core/Engine.ts
- tscolorballs.html
- tsconfig.json

![Содержимое папки проекта ColorBalls]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-tsconfig-json/typescript-tsconfig-json-contains_dir.jpg "Содержимое папки проекта ColorBalls")

Если мы сейчас вызовем компилятор TypeScript из каталога, в котором содержится файл `tsconfig.json` без параметров, то 
он будет использовать содержимое файла `tsconfig.json`: 

![Вызываем компилятор TypeScript (tsc)]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-tsconfig-json/typescript-tsconfig-json-run_tsc.jpg "Вызываем компилятор TypeScript (tsc)")

В результате компиляции в корневой папке проекта появится файл `tscolorballs.js`. 

![Содержимое папки проекта ColorBalls]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-tsconfig-json/typescript-tsconfig-json-contains_dir-1.jpg "Содержимое папки проекта ColorBalls")

Выведем содержимое папки проекта командой `dir`: 

![Содержимое папки проекта ColorBalls]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-tsconfig-json/typescript-tsconfig-json-contains_dir-2.jpg "Содержимое папки проекта ColorBalls")

В `tsconfig.json` могут указываться дополнительные опции компиляции, а также **_exclude_**, но на начальном этапе нам хватит того, что 
мы описали здесь.

[_Вторая часть проекта - "TypeScript - скелет игры"_]({{ site.url }}{{ site.baseurl }}{% post_url 2023-11-30-typescript-plan-game %})   
[_Оригинал статьи_.](https://urvanov.ru/2019/05/23/typescript-tsconfig-json-%d0%bf%d0%b8%d1%88%d0%b5%d0%bc-%d1%81%d0%b2%d0%be%d1%8e-%d0%b8%d0%b3%d1%80%d1%83/)
