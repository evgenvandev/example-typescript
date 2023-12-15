---
layout: post
title: TypeScript - скелет игры
feature-img: "assets/img/typescript/typescript-plan-game/typescript-plan-game-title.jpg"
thumbnail: "assets/img/thumbnails/typescript/typescript-plan-game/typescript-plan-game-title.jpg"
tags: [TypeScript, Game, Colorballs]
categories: Colorballs
---

Пишем скелет игры. Для начала определим класс доски. Вся игра происходит на поле, поделённое на квадраты. 
Это поле и будет представлять собой наш класс `Board`: 

{% highlight typescript linenos %}
class Board {
  private static TILE_TYPES_COUNT: number = 4;
  private tiles: TileState[][];
  private width: number;
  private height: number;
  
  public constructor(width: number, height: number) {
    this.width = width;
    this.height = height;
    this.tiles = Array<Array<TileState>>();
    for (let n: number = 0; n < width; n++) {
      this.tiles[n] = new Array<TilesState>(height);
      for (let m: number = 0; m < height; m++) {
        this.tiles[n][m] = this.randomInteger(1, Board.TILE_TYPES_COUNT);
      }
    }
  }
  
  private randomInteger(min: number, max: number) {
    let rand = min + Math.random() * (max + 1 - min);
    rand = Math.floor(rand);
    return rand;
  }
}
{% endhighlight %}

Тут ничего сложного. Мы просто создаём класс `Board` с конструктором. Внутри класса у нас массив состояний каждой клетки, 
который мы инициализируем в конструкторе. 

`TileState` - это перечисление, которое описывает возможные состояния клеток: 

{% highlight typescript linenos %}
enum TileState {
  EMPTY,
  RED,
  GREEN,
  BLUE,
  YELLOW
}
{% endhighlight %}

Есть ещё одна маленькая деталь: нам нужно добавить `canvas` в HTML. В предыдущей статье мы забыли это сделать. 
Файл `tscolorballs.html` станет таким: 

{% highlight html linenos %}
<!DOCTYPE html>
<html>
  <head><title>TypeScript Color Balls</title></head>
  <body>
    <script src="tscolorballs.js"></script>
    <canvas id="tscolorballscanvas" width="320" height="384">
    </canvas>
  </body>
</html>
{% endhighlight %}

Пора писать сам движок. В классе `Engine` мы будем обрабатывать основную логику. 

{% highlight typescript linenos %}
class Engine {
  ...
  public constructor() {
    this.board = new Board(Engine.BOARD_WIDTH, Engine.BOARD_HEIGHT);
    let engine = this;
    setTimeout(function() {engine.onStep();}, 
                  Engine.TICK_MILLISECONDS);
  }
  ...
}
{% endhighlight %}

Обратите внимание, что внутри обработчика 

[_Первая часть проекта - "TypeScript tsconfig.json (пишем свою игру)"_]({{ site.url }}{{ site.baseurl }}{% post_url 2023-11-28-typescript-tsconfig-json %})   
[_Оригинал статьи_.](https://urvanov.ru/2019/05/31/typescript-%d1%81%d0%ba%d0%b5%d0%bb%d0%b5%d1%82-%d0%b8%d0%b3%d1%80%d1%8b/) 
