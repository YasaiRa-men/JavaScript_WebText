---
var:
    header-title: "オンラインテキストテンプレート"
    header-date: "2024/04/23"
---

# JavaScript でゲームを作ろう

## 概要

### 前回の復習

-   ゲームに使用する JavaScript のコードを学んだ

### 今回の講義の達成目標

<div class="note type-intro">
**達成目標**
・Anime.jsについて学ぼう
</div>

## Anime.js を使用したアニメーションの作成

-   Anime.js は、軽量で柔軟な JavaScript アニメーションライブラリです。CSS プロパティ、SVG、DOM 属性、そして JavaScript オブジェクトをアニメーション化することができます。このライブラリを使用すると、複雑なアニメーションを簡単に作成でき、Web ページに動的な視覚効果を加えることが可能です。

### Anime.js の基本

-   Anime.js を使用するには、まずライブラリをページに含める必要があります。以下のスクリプトタグを HTML に追加して、Anime.js を読み込みます。

```html{.numberLines caption="index.html"}
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
```

-   基本的なアニメーションの設定は非常にシンプルです。以下の例では、CSS セレクタを指定して、特定の要素をアニメーション化します。

```javascript{.numberLines caption="main.js"}
anime({
  targets: '.box',
  translateX: 250,
  rotate: '1turn',
  duration: 2000,
  loop: true
});
```

-   このコードは、クラス名`box`の要素を右に 250 ピクセル移動させ、1 回転させるアニメーションを作成します。アニメーションの期間は 2000 ミリ秒で、これが無限に繰り返されます。

<iframe height="300" style="width: 100%;" scrolling="no" title="anime1" src="https://codepen.io/YasaiRa-men/embed/dyBjJKV?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/dyBjJKV">
  anime1</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### Anime.js のイージング

-   Anime.js は、様々なイージング（動き方）を用意してくれています。

-   [こちら](https://animejs.com/documentation/#pennerFunctions)から様々なイージングを見ることができるので、以下のコードの`easing`に色々なものを入れて試してみましょう。

```javascript{.numberLines caption="main.js"}
anime({
  targets: '.box',
  translateX: 250,
  rotate: '1turn',
  duration: 2000,
  easing: "easeInOutSine",
  loop: true
});
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/ExBpopN?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/ExBpopN">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 移動のイージング

-   先程作ったマウスや指についてくる丸にもこの anime.js を用いることで、主人公を緩やかな動きに変えることができます。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/GgKZaOE?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/GgKZaOE">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 障害物の落下

-   これまでの知識を活かすと、このように上から 1 秒ごとに鼠色の背景の範囲内でランダムな X 座標から障害物(黒い丸)を落下させることができます。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/PoraGZd?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/PoraGZd">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## まとめ

-   Anime.js のライブラリを使用することで、Web ページにスムーズで魅力的なアニメーションを簡単に追加できます。
