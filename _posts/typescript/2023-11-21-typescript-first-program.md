---
layout: post
title: TypeScript - первая программа
feature-img: "assets/img/typescript/typescript-first-program/typescript-first-program-title.jpg"
thumbnail: "assets/img/thumbnails/typescript/typescript-first-program/typescript-first-program-title.jpg"
tags: [TypeScript]
categories: TypeScript
---

Создадим первое приложение на TypeScript.   
Для начала создадим каталог приложения. В данном случае это будет папка `c:\progTypeScript\S_saita_metanit_com\Example-1\`. 
В этот каталог добавим файл `index.html`. Откроем этот файл в любом текстовом редакторе и напишем в нём следующий код: 

_Файл index.html_
{% highlight html linenos %}
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Metanit.com</title>
</head>
<body>
  <h2 id="header"></h2>
  <script src="app.js"></script>
</body>
</html>
{% endhighlight %}

Это обычный файл `.html`, в котором определён пустой заголовок - элемент `<h2></h2>` - в него будем выводить некоторое содержимое. 
И также на веб-странице подключается файл `app.js`.   
На данный момент содержимое рабочего каталога: 

![Содержимое папки проекта First application]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-first-program/typescript-first-program-directory-1.jpg "Содержимое папки проекта First application")

Теперь в том же каталоге создадим файл `app.ts`. Причём именно `app.ts`, а не `app.js`, то есть файл кода TypeScript. Это 
также обычный текстовый файл, который имеет расширение `.ts`. И в `app.ts` напишем следующий код: 

_Файл app.ts_
{% highlight typescript linenos %}
class User {
  name: string;
  
  constructor(_name: string) {
    this.name = _name;
  }
}

const tom: User = new User("Том");
const header = this.document.getElementById("header");
header.innerHTML = "Привет " + tom.name;
{% endhighlight %}

Что здесь происходит? Сначала определяем класс `User` - это шаблон данных, которые будут использоваться на веб-странице. 
Этот класс имеет поле `name`, которое представляет тип `string`, то есть строку. Для передачи данных этому полю определён 
специальный метод - `constructor`, который принимает через параметр `_name` некоторую строку и передаёт её в поле `name`: 

{% highlight typescript %}
class User {
  name: string;
  
  constructor(_name: string) {
    this.name = _name;
  }
}
{% endhighlight %}

Далее создаём константу `tom`, которая представляет этот класс: 

{% highlight typescript %}
const tom: User = new User("Том");
{% endhighlight %}

Иначе говоря, константа `tom` представляет некоторого пользователя, у которого имя "Tom".   
Затем получаем элемент с `id` равным `header` на веб-странице, в одноимённую константу `header`: 

{% highlight typescript %}
const header = this.document.getElementById("header");
{% endhighlight %}

То есть этот элемент будет представлять определённый на веб-странице `index.html` заголовок `<h2></h2>`.   
Далее с помощью свойства `innerHTML` меняем содержимое элемента: 

{% highlight typescript %}
header.innerHTML = "Привет " + tom.name;
{% endhighlight %}

В данном случае свойству `innerHTML` передаётся строка, к которой добавляется значение свойства `tom.name`. 
То есть мы ожидаем, что в заголовок `<h2></h2>` на веб-странице будет выводиться создаваемая здесь строка. 

Сохраним и скомпилируем этот файл. Для этого в командной строке с помощью команды `cd` перейдём к каталогу, где 
расположен файл `app.ts`. И для компиляции выполним следующую команду: 

{% highlight console %}
tsc app.ts
{% endhighlight %}

![Команда tsc app.ts]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-first-program/typescript-first-program-comand-tsc-app-ts.jpg "Команда tsc app.ts")

После компиляции в каталоге проекта создаётся файл JavaScript `app.js`: 

![Создаётся файл app.js]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-first-program/typescript-first-program-create-app-js.jpg "Создаётся файл app.js")

Данный файл будет выглядеть, следующим образом: 

{% highlight typescript linenos %}
var User = /** @class */ (function () {
    function User(_name) {
        this.name = _name;
    }
    return User;
}());
var tom = new User("Том");
var header = this.document.getElementById("header");
header.innerHTML = "Привет " + tom.name;
{% endhighlight %}

Теперь можем открыть веб-страницу `index.html` в браузере и увидеть результат работы файла JavaScript `app.js`, подключённого 
в файле `index.html`

![Результат работы в браузере]({{ site.url }}{{ site.baseurl }}/assets/img/typescript/typescript-first-program/typescript-first-program-result-work.jpg "Результат работы в браузере")

[_Оригинал статьи_.](https://metanit.com/web/typescript/1.2.php)
