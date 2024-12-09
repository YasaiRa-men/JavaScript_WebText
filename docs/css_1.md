# JavaScript でゲームを作ろう

## 前回の復習

-   CSS の記述の仕方を学んだ

## 今回の講義の達成目標

<div class="note type-intro">
達成目標

ゲームに使用する CSS の装飾を学ぼう

</div>

## はじめに

-   css で色んな装飾を学んでいこう

## 色（背景も）

background-color:

-   <em>background-color</em>プロパティは、要素の背景色を設定するために使用されます。

-   background-color プロパティは、要素の背景に色を適用します。色は名前、HEX コード、RGB 値、または HSL 値で指定できます。

<iframe height="300" style="width: 100%;" scrolling="no" title="bgcolor" src="https://codepen.io/YasaiRa-men/embed/poXKbmm?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/poXKbmm">
  bgcolor</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 大きさ

width:
height:

-   <em>width</em>と<em>height</em>プロパティは、要素の幅と高さを設定します。

-   width と height は要素の幅と高さを指定します。これらはピクセル(px)、パーセンテージ(%)、ビュー幅(vw)などの単位で指定できます。

<iframe height="300" style="width: 100%;" scrolling="no" title="w,h" src="https://codepen.io/YasaiRa-men/embed/JjQZKQR?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/JjQZKQR">
  w,h</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 縦横比

aspect-ratio:

-   <em>aspect-ratio</em>プロパティは、要素の幅と高さの比率を設定します。

-   aspect-ratio プロパティは、要素の幅と高さの比率を制御するのに使います。たとえば、aspect-ratio: 16 / 9; と指定すると、16:9 の比率が適用されます。

<iframe height="300" style="width: 100%;" scrolling="no" title="aspect" src="https://codepen.io/YasaiRa-men/embed/bGPKePm?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/bGPKePm">
  aspect</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 形

border-radius:

-   <em>border-radius</em>プロパティは、要素の角の丸みを設定します。

-   border-radius プロパティは、要素の角を丸くするのに使用されます。値はピクセル(px)またはパーセンテージ(%)で指定できます。

<iframe height="300" style="width: 100%;" scrolling="no" title="radius" src="https://codepen.io/YasaiRa-men/embed/KKjeMjY?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/KKjeMjY">
  radius</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 場所

transform: translateX()

-   <em>transform</em>プロパティの<em>translateX()</em>関数は、要素を水平方向に移動させます。

-   transform: translateX() 関数は、要素を X 軸（横方向）に平行移動させます。ピクセル(px)やパーセンテージ(%)などの単位で移動量を指定します。

<iframe height="300" style="width: 100%;" scrolling="no" title="transformX" src="https://codepen.io/YasaiRa-men/embed/ExBRyqK?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/ExBRyqK">
  transformX</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   なお、これらは<em>translate()</em>というものもあり、これは横、縦の 2 つを指定することができます。

## 余白

margin:
padding:

-   <em>margin</em>プロパティは要素の外側に、<em>padding</em>は要素の内側に余白を設けます。

![img](figs/css/margin-padding.jpg)

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/VYZaggb?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/VYZaggb">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
