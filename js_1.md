---
var:
    header-title: "オンラインテキストテンプレート"
    header-date: "2024/04/23"
---

# JavaScript でゲームを作ろう

## 概要

### 前回の復習

-   JavaScript の書き方について学んだ

### 今回の講義の達成目標

<div class="note type-intro">
**達成目標**

・ゲームに使用している関数などについて学ぼう

</div>

## Document オブジェクト

### Document オブジェクトとは

-   Document オブジェクトは、Web ページ全体を表すオブジェクトであり、HTML 文書全体を操作するためのインターフェースを提供します。JavaScript を使用して、HTML 要素の取得や変更、新しい要素の作成などを行う際に Document オブジェクトが活用されます。

-   今回作成するゲームにて、テキストやボタンの位置、色などの変更はこれらによって指定されています。

-   Document オブジェクトは通常、`document` 変数を介してアクセスされます。

### HTML 要素の取得

-   Document オブジェクトを使用すると、HTML 要素を取得することができます。以下は、要素を取得する例です。

![img](figs/js/document.getElementByID.png)

-   このコードで変数に代入することで、要素に様々なことをすることができるようになるぞ！

```html{caption="index.html"}
<div id="myElement" class="myClass"></div>
<script src="main.js"></script>
```

```javascript{.numberLines caption="main.js"}
// IDを使用して要素を取得
let elementById = document.getElementById("myElement");

// クラス名を使用して要素を取得
let elementsByClass = document.getElementsByClassName("myClass");

// タグ名を使用して要素を取得
let elementsByTag = document.getElementsByTagName("div");
```

-   今回の例だと、全て同じ要素を取得しています。

-   これらを取得することによって、その HTML 要素の文字や色などが JavaScript で変更できるようになります。

### 要素の大きさを取得

-   先程取得したものを使って、要素の大きさを取得することができます。

-   リンクしている HTML ファイルの中に、`content`という名前の ID 属性が付けられているとすると、その要素の大きさを取得するには、`offset`プロパティを使います。

```javascript{.numberLines caption="main.js"}
let elem = document.getElementById("content");

// 幅を取得
let elemWidth = elem.offsetWidth;

// 高さを取得
let elemHeight = elem.offsetHeight;
```

-   では、h1 タグに ID 属性を付けて、それの幅と高さをコンソールに出力してみよう。

```html{.numberLines caption="index.html"}
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>解答</title>
        <link rel="stylesheet" href="style.css" />
    </head>
    <body>
        <h1 id="content">こんにちは！！！！！！</h1>
        <script src="main.js"></script>
    </body>
</html>
```

```css{.numberLines caption="style.css"}
/*色を変えて大きさが分かりやすいようにする*/
#content {
    background-color: chartreuse;
}
```

```javascript{.numberLines caption="main.js"}
let elem = document.getElementById("content");

// 幅を取得
let elemWidth = elem.offsetWidth;
// 高さを取得
let elemHeight = elem.offsetHeight;

console.log(elemWidth);

console.log(elemHeight);
```

-   コンソールに表示されていれば成功です！

![img](figs/js/youso_haba.png)

-   また、左上を原点としてときに要素がどの高さにあるのかを見るには、`offsetTop`を使います。

### ウィンドウの大きさを取得

-   ウィンドウの大きさを取得するには、以下のコードを使います。

```javascript{.numberLines caption="main.js"}
const Width = window.innerWidth;
const Height = window.innerHeight;
```

<div class="note type-quiz">
Q. ウィンドウの幅と高さを取得して、コンソールの出力してみよう。
<div class="quizes">
<div class="options">
  <div class="option correct">答えを見る</div>
</div>
<div class="answercontent">
答えの一例です。

```javascript{.numberLines caption="main.js"}
const Width = window.innerWidth;
const Height = window.innerHeight;

console.log(Width);
console.log(Height);
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/bNberRE?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/bNberRE">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   以下の動画から、幅や高さを変えてからサイトを更新すると、コンソールの中の値が変わっているのが分かります。

![img](figs/js/haba.gif)

</div>
</div>
</div>

-   `offset`と`inner`で違ってくるので注意！

### HTML 要素の変更

-   ひとまず、HTML をこのように書いてみよう。

```html{caption="index.html"}
<p id="myElement"></p>
<script src="main.js"></script>
```

-   Document オブジェクトを使用して、<em>textContent</em>で取得した HTML 要素の内容を変更することができます。以下は、要素の内容を変更する例です。

```javascript{.numberLines caption="main.js"}
let element = document.getElementById("myElement");
element.textContent = "新しいテキスト";
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/NWVNdmK?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/NWVNdmK">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

また、<em>style</em>で css のスタイルを変更することができます。以下は、要素の内容を変更する例です。

```javascript{.numberLines caption="main.js"}
let element = document.getElementById("myElement");
element.textContent = "新しいテキスト";
element.style.color = "red";
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/MWdyJRj?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/MWdyJRj">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

<div class="note type-quiz">
Q. 以下のHTMLのp要素に「こんにちは」という文字を入れ、の背景を青に、横幅を100%にしよう。
```html{caption="index.html"}
<p id="myElement"></p>
<script src="main.js"></script>
```
<div class="quizes">
<div class="options">
  <div class="option correct">答えを見る</div>
</div>
<div class="answercontent">
答えの一例です。
<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/yLWVXjQ?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/yLWVXjQ">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
</div>
</div>
</div>

### 新しい要素の作成

-   JavaScript から新しく要素を作成したい場合、`insertAdjacentHTML`メソッドを使用します。

-   insertAdjacentHTML は、HTML 要素の隣に指定した位置で新しい HTML コードを挿入するためのメソッドです。このメソッドを使うと、既存の要素を操作することなく、効率的に新しい内容を挿入できます。

```javascript{.numberLines caption="main.js"}
element.insertAdjacentHTML(position, htmlString);
```

<div class="note type-tips">
- element: HTML を挿入する対象の要素。
- position: 挿入する位置を指定する文字列（以下の 4 種類から選択）。
- htmlString: 挿入する HTML 文字列。
</div>

-   position は、どこに配置するかで、4 種類から選びます。

| 値             | 意味                                 |
| -------------- | ------------------------------------ |
| "beforebegin": | 要素の直前（要素の外側）             |
| "afterbegin" : | 要素の最初の子要素の前（要素の内側） |
| "beforeend" :  | 要素の最後の子要素の後（要素の内側） |
| "afterend" :   | 要素の直後（要素の外側）             |

-   以下の CodePen からそれぞれの position でどこに追加されるか確認してみよう！

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/dPbXzpg?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/dPbXzpg">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## WebKitCSSMatrix

-   WebKitCSSMatrix は、CSS で使われる「変形（Transform）」の値を読み取ったり操作したりするための JavaScript オブジェクトです。
    主に 回転（rotate）、拡大縮小（scale）、移動（translate） などの値を取得したいときに使います。

```javascript{.numberLines caption="main.js"}
let target_element = document.getElementById("target");

// m41プロパティだとその要素のx座標
console.log(new WebKitCSSMatrix(target_element.style.transform).m41);
// m41プロパティだとその要素のy座標
console.log(new WebKitCSSMatrix(target_element.style.transform).m42);

```

-   今回のゲームでは、移動のみ使います。

## イベントハンドリング

-   イベントハンドリングは、ユーザーからの入力やアクションに応じてプログラムが反応する方法です JavaScript を使用すると、Web ページ上のイベントを捕捉し、特定の処理を実行することができます。

```javascript{.numberLines caption="main.js"}
document.addEventListener(イベント, function() {
  // イベントが行われたときに実行されるところ
  console.log("イベントが発生しました。");
});
```

-   イベントハンドリングはこのようにして追加することができます。（イベントについては後ほど解説します）

-   addEventListener の前の document について、`document`だと Web 全体でイベントを監視していて、特定の要素内でイベントを監視したいときには、Document オブジェクトを書いてあげることで実現できます。

-   また、イベントで行われる関数には、引数を設定することができ、この引数を使って様々なことができます。

```javascript{.numberLines caption="main.js"}
document.addEventListener("wheel", function(event) {
  // イベントが行われたときに実行されるところ

  event.preventDefault();
  console.log("イベントが発生しました。");

}, { passive: false });
```

-   例えば、ホイールでスクロールさせようとしたときに発生するイベントですが、上から下へホイールを動かした際に、ページが上にスクロールしてしまいます。

-   このようなデフォルトの動作を無効にするために、`preventDefault();`というものがあり、これを書くことで無効にできます。

-   また、詳しい解説は省きますが、`preventDefault();`を使用した際には、`addEventListener`の第二引数に passive を false にすることを宣言しておく必要があります。これをしておかないと、`preventDefault();`がブラウザによって機能しない可能性があります。

### イベントリスナーの追加

-   イベントリスナーは、例えば、ボタンをクリックしたとき、マウスを動かしたとき、文字を入力したとき...など、様々なイベントが発生したときに呼び出されます。

-   これを個別で追加することによって、ユーザーが行ったことを検知することができます。

-   以下は、ボタンクリックイベントにリスナーを追加する例です。

```html{caption="index.html"}
<button id="myButton">Click me!</button>
<script src="main.js"></script>
```

```javascript{.numberLines caption="main.js"}
let button = document.getElementById("myButton");

button.addEventListener('click', function() {

  alert('Button was clicked!');

});
```

-   この例では、ID が `myButton` のボタンにクリックイベントリスナーを追加しています。ボタンがクリックされると、アラートが表示されます。

<iframe height="300" style="width: 100%;" scrolling="no" title="btnclick" src="https://codepen.io/YasaiRa-men/embed/vYqapZW?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/vYqapZW">
  btnclick</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   他にも、キーを押したときの`keydown`、画面をタッチ操作で動かしたときの`touchmove`,
    マウスを動かしたときの`mousemove`などもあります。

-   以下の例では、マウスまたは画面を指でスライドしたときに黒丸がその場所に移動するサンプルコードです。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/abgKZOr?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/abgKZOr">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   この丸を主人公に当てはめることで、常にマウスについてくるようになります。

### イベントリスナーの削除

-   イベントリスナーを追加しすぎると、アプリケーションに負荷を与えてしまいます。そのため、不要なイベントリスナーは積極的に削除しましょう。
-   イベントリスナーを削除するには、<em>removeEventListener</em> メソッドを使います。

```javascript{.numberLines caption="main.js"}
element.removeEventListener(eventType, listenerFunction);
```

<div class="note type-intro">
- element: イベントを設定した要素。
- eventType: イベントの種類（例: "click"、"keydown" など）。
- listenerFunction: 削除したいイベントリスナーとして指定した関数。
</div>

<div class="note type-quiz">
Q. 以下のHTMLとJavaScriptがあったとき、JavaScriptを書き加えてスタートボタンが押されたらスコアの増加が0から始まってストップボタンが押されたらスコアの増加が止まるコードを書いてみよう。
ヒント：スコアの増加は<u>setInterval</u>で行います。
```html{caption="index.html"}
<h2 id="Score">0</h2>
<button id="startButton">スタート</button>
<button id="stopButton">ストップ</button>
<script src="main.js"></script>
```

```javascript{caption="main.js"}
const scoreElement = document.getElementById("Score");
const startButton = document.getElementById("startButton");
const stopButton = document.getElementById("stopButton");

let score = 0; // スコアの初期値
let scoreInterval; // スコアを増加させるためのタイマー ID

// スタートボタンのクリックイベント
startButton.addEventListener("click", () => {
// ここに処理を書く
});

// ストップボタンのクリックイベント
stopButton.addEventListener("click", () => {
// ここに処理を書く
});

```

<div class="quizes">
<div class="options">
  <div class="option correct">答えを見る</div>
</div>
<div class="answercontent">
答えの一例です。

```javascript{caption="main.js"}
const scoreElement = document.getElementById("Score");
const startButton = document.getElementById("startButton");
const stopButton = document.getElementById("stopButton");

let score = 0; // スコアの初期値
let scoreInterval; // スコアを増加させるためのタイマー ID

// スタートボタンのクリックイベント
startButton.addEventListener("click", () => {
  // スコアを初期化
  score = 0;
  // スコア増加を開始
  scoreInterval = setInterval(() => {
    score++;
    scoreElement.textContent = score;
  }, 10); // 10ms ごとにスコアを 1 増加
});

// ストップボタンのクリックイベント
stopButton.addEventListener("click", () => {
  // スコア増加を停止
  clearInterval(scoreInterval);
});

```

<iframe height="300" style="width: 100%;" scrolling="no" title="timer" src="https://codepen.io/YasaiRa-men/embed/ByBzwjW?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/ByBzwjW">
  timer</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
</div>
</div>
</div>

## 距離計算

-   障害物に当たるとゲームオーバーになるようにするには、障害物との距離を計算する必要があります。

-   そこで、それぞれの X 座標と Y 座標は分かっているので、三平方の定理を利用することで距離を求めることができます。

![img](figs/js/kyori.png)

<iframe height="300" style="width: 100%;" scrolling="no" title="kyori2" src="https://codepen.io/YasaiRa-men/embed/poXKbpq?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/poXKbpq">
  kyori2</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   `getBoundingClientRect()`はターゲット要素をの位置をブラウザの表示領域の左上を(0, 0)として、そこからの相対位置で示されています。これによって自分、または障害物がどこにあるのかを調べることができます。

![img](figs/js/zahyou.png)

```javascript{.numberLines caption="script.js"}
// 自分の位置を取得
const circleRect = circle.getBoundingClientRect();
// 障害物の位置を取得
const obstacleRect = obstacle.getBoundingClientRect();
```

-   距離計算の関数について解説します。

-   距離は、このように計算することで求めることができます。

$$距離=\sqrt{縦^{2} + 横^{2}}$$

-   この式を JavaScript で書いてみよう！

```javascript{.numberLines caption="script.js"}
// 三平方の定理で距離を計算
const distance = Math.sqrt(Math.pow(circleX - obstacleX, 2) + Math.pow(circleY - obstacleY, 2));
```

-   `Math.pow()`は、累乗を計算できるもので、第一引数には累乗させたい数、第二引数には指数を書きます。上記の例だとそれぞれ自分の位置から障害物までの位置の差を取って、2 乗していることが分かります。

-   `Math.sqrt()`は、平方根を表します。

-   これらによって、`distance`に計算された距離を代入されていることが分かりますね！

-   テキストについての処理はここで行われています。

```javascript{.numberLines caption="script.js"}
// 距離をテキストで表示
distanceText.textContent = 'Distance: ' + Math.round(distance) + 'px';

// 衝突判定 (2つの半径の和より距離が小さい場合)
const radiusSum = circleRect.width / 2 + obstacleRect.width / 2;

if (distance <= radiusSum) {
    collisionText.textContent = '当たり判定：障害物に当たっています！';
} else {
    collisionText.textContent = '当たり判定：障害物に当たっていません';
}
```

-   Math.round()は小数点以下を四捨五入できるものとなってます。試しに`Math.round(distance)`のところを`distance`に変更
    してみるとどんな変化があるのか試してみよう！

-   下の条件分岐では、計算された距離が自分と障害物の丸の半径の合計より小さい場合、つまり当たっている場合で表示するテキストを変えています。

## まとめ

-   このセクションでは、JavaScript を使って、避けゲーの基盤となる部分を作成しました。

---

次回はこれらを組み合わせて実際にゲーム作りにとりかかりましょう！
