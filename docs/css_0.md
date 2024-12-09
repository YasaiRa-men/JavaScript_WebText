## 概要

### 前回の復習

-   HTML のタグについて学んだ

### 今回の講義の達成目標

<div class="note type-intro">
達成目標

CSS の基本的な記述方法を学ぼう。

CSS を使って HTML のスタイルを変更しよう。

セレクタの使い方を理解しよう。

レイアウトの基本を学ぼう。

</div>

## はじめに

-   今回は、CSS の基礎について学ぶ。
-   CSS は、HTML の要素を装飾し、レイアウトを整えるためのスタイルシート言語である。
-   ひとまず、CSS を使って基本的なスタイルを設定してみよう。

## CSS の基本

### CSS とは

-   CSS（Cascading Style Sheets）は、HTML 要素のスタイルを定義するための言語である。色、フォント、レイアウトなどを指定できる。

![img](figs/css/1.png)

-   このようにページを装飾することができる。

-   他にも、形の変更や大きさ、配置する場所も決められる。

![img](figs/css/2.png)

-   制作するゲーム画面でもこのような感じで使われている。

## CSS の記述方法

-   CSS の記述方法には主に 3 つの方法がある。

1. インラインスタイル
2. 内部スタイルシート
3. 外部スタイルシート

-   今回はこの 3 つの方法で p タグに色を指定しました。

### インラインスタイル

-   インラインスタイルは、HTML タグの style 属性に直接 CSS を記述する方法。

```html{.numberLines caption="example.html"}
<p style="color: red;">これは赤いテキストです。</p>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css0" src="https://codepen.io/YasaiRa-men/embed/XWwvXLQ?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/XWwvXLQ">
  css0</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 内部スタイルシート

-   内部スタイルシートは、HTML ファイルの`<head>`セクション内に`<style>`タグを使って CSS を記述する方法。

```html{.numberLines caption="example.html"}
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: blue;
    }
  </style>
</head>
<body>
  <p>これは青いテキストです。</p>
</body>
</html>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css1" src="https://codepen.io/YasaiRa-men/embed/abredge?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/abredge">
  css1</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 外部スタイルシート

-   外部スタイルシートは、別の CSS ファイルを作成し、それを HTML ファイルにリンクする方法。

-   まず、styles.css という名前のファイルを作成する。

```css{.numberLines caption="style.css"}
/* styles.css */
p {
  color: green;
}
```

-   次に、HTML ファイルでその CSS ファイルをリンクする。

```html{.numberLines caption="example.html"}
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
  <p>これは緑のテキストです。</p>
</body>
</html>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css3" src="https://codepen.io/YasaiRa-men/embed/JjqgGgj?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/JjqgGgj">
  css3</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## セレクタ

-   セレクタは、どの HTML 要素にスタイルを適用するかを指定するためのもの。

### タイプセレクタ

-   要素の種類を指定するセレクタ。
-   今回の例だと p 要素を指定している。

```html{.numberLines caption="example.html"}
<style>
p {
  color: purple;
}
</style>

<p>むらさき！！！<p>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css4" src="https://codepen.io/YasaiRa-men/embed/oNRKbKj?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/oNRKbKj">
  css4</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### クラスセレクタ

-   クラス属性を持つ要素を指定するセレクタ。クラス名はピリオド（.）を使って指定する。

```html{.numberLines caption="example.html"}
<style>
.text-red {
  color: red;
}
</style>

<p class="text-red">これは赤いテキストです。</p>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css5" src="https://codepen.io/YasaiRa-men/embed/YzbmwmW?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/YzbmwmW">
  css5</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### ID セレクタ

-   ID 属性を持つ要素を指定するセレクタ。ID 名はハッシュ記号（#）を使って指定する。

```html{.numberLines caption="example.html"}
<style>
#main-heading {
  color: blue;
}
</style>

<h1 id="main-heading">これは青い見出しです。</h1>
```

<iframe height="300" style="width: 100%;" scrolling="no" title="css6" src="https://codepen.io/YasaiRa-men/embed/GRaVoVW?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/GRaVoVW">
  css6</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

-   これで、CSS の基本についての講義資料は完成です。さらに詳細なスタイルの指定やレイアウトの技法については、次回の講義で取り上げます。
