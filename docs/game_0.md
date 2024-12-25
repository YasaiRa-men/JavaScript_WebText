---
var:
    header-title: "オンラインテキストテンプレート"
    header-date: "2024/04/23"
---

# JavaScript でゲームを作ろう

## まずはステージを作成しよう

-   これからゲームを作っていきますが、まだ紹介していない HTML タグや CSS タグがありますが、それらは出てきたときに軽く解説します。

### 枠の作成

-   まずは、HTML と CSS を使って簡単なステージを作ってみよう。

-   始めに、新しくフォルダを作りましょう。

-   そのフォルダ内に`index.html`という HTML ファイルを作成します。

-   `!`を書いて、HTML の雛形を書こう！

```html{.numberLines caption="index.html"}
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>避けプル</title>
</head>
<body>
</body>
</html>
```

-   ここからはゲームのサイズや配置を決めます。

![img](figs/game/game1.png)

-   ただし、ブラウザは見る端末によって大きさ・縦横比が変わってきます。

![img](figs/game/terminals.jpeg)

-   今回は、スマホをメインにすることから縦長にします。

-   `main`というタグを使っていますが、意味合い的には`div`と同じです。

<div class="note type-tips">

-   内部では主要部分として扱われ、`main`は 1 つの HTML に基本 1 つまでですが、それ例外の扱いは`div`と同じです。

</div>

```html{.numberLines caption="index.html"}
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>避けプル</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main>
        <!--ゲーム画面の大きさ-->
        <div id="mainWindow">

            <!--主人公の移動領域-->
            <div id="targetField"></div>

            <!--ゲームタイトル-->
            <div id="gameTitle">
                <div>避けプル</div>
                <button id="startButton">スタート</button>
            </div>

        </div>
    </main>
</body>
</html>
```

-   前回の CSS では、主要なものを紹介しましたが、あまり使わないものもあります。

-   ここでは、それらについて軽く触れておきます ���

position: absolute;

-   `position`プロパティでは、配置をどのようにするかを決めるものです。

-   `absolute`だと、その要素を現在の位置から<u>好きな場所に配置すること</u>ができるようになります。

<div class="note type-tips">

-   top : 要素が起点の上からどれだけ離れているかを示します
-   bottom : 要素が起点の下からどれだけ離れているかを示します
-   left : 要素が起点の左からどれだけ離れているかを示します
-   right : 要素が起点の右からどれだけ離れているかを示します

</div>

```css{.numberLines caption="style.css"}
html,
body {
    height: 100%;
}

body {
    margin: 0px;
}

main {
    transform: translateX(50%); /*メインの位置を50%右にずらす*/
    width: 100%;
    height: 100%;
}

#mainWindow {
    background-color: rgb(3, 50, 151);
    height: 100%;
    aspect-ratio: 9 / 16;
    transform: translateX(-50%); /*ステージ枠を50%左にずらす*/
}

#gameTitle {
    position: absolute; /*相対位置にする*/
    color: white;
    top: 50%; /*上から50%の位置に*/
    left: 50%; /*左から50%の位置に*/
    transform: translate(-50%, -50%);
}

#targetField {
    background-color: rgb(85, 131, 233);
    position: absolute;
    width: 100%;
    height: 18%;
    bottom: 18%; /*下から18%の位置に*/
    z-index: -1; /*レイヤーを最背面に*/
}
```

-   この 2 つを実行すると、以下のようになります。

<iframe height="300" style="width: 100%; height: 600px;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/oNOKKry?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/oNOKKry">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   スタートボタンがありますが、まだ何も起きません。

### 主人公の作成

-   次に、ボタンが押されたら主人公が出現するようにしよう。
-   主人公は、のちに JavaScript で操作できるように、"target"という id 属性をつけます。

<div class="note type-tips">

-   js ファイルを作ったら、HTML に`script`タグを追加するのを忘れずに！

</div>

```html{.numberLines caption="index.html"}
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>避けプル</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main>
        <div id="mainWindow">

            <div id="targetField"></div>
            <!-- ここに主人公にするdivを配置 -->
            <div id="target"></div>

            <div id="gameTitle">
                <div>避けゲー</div>
                <button id="startButton">スタート</button>
            </div>

        </div>
    </main>
</body>
</html>
```

-   また、主人公には分かりやすいように色を茶色の丸にしておきます。

```css{.numberLines caption="style.css"}

/*既存のコード*/

/*主人公*/
#target {
    width: 30px;
    height: 30px;
    margin: 0px;
    position: absolute;
    background-color: brown;
    border-radius: 50%;
}

```

-   これによって、このようになりました。

<iframe height="300" style="width: 100%; height: 600px;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/pomzzoE?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/pomzzoE">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   分かりやすく主人公が出てきましたが、左上にいます。
-   これらも自分で設定していかなければなりません。

### 主人公の位置を中央に

-   スタートボタンが押されたら主人公が移動範囲内の中心に出現するようにしたいが、それには少し計算が必要です。

-   要素の基準点は、基本<u>左上</u>にあるため、それに合わせる必要があります。

-   主人公の要素を`target`、主人公の移動する領域の要素を`targetField`とすると、

```javascript{.numberLines caption="main.js"}
// 中心のX座標
// 移動領域の横幅の半分 - 主人公の横幅の半分
let CenterX = targetField.offsetWidth / 2 - targetelem.offsetWidth / 2;

// 中心のY座標
// 移動領域までの高さ + 移動領域の縦幅の半分 - 主人公の縦幅の半分
let CenterY = targetField.offsetTop + targetField.offsetHeight / 2 - targetelem.offsetHeight / 2;
```

-   となることが分かる。

![img](figs/js/center.png)

-   中心に配置するために ainme.js を用います。

```html{.numberLines caption="index.html"}
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>避けプル</title>
</head>
<body>
    <main>
        <div id="mainWindow">

            <div id="targetField"></div>
            <!-- ここに主人公にするdivを配置 -->
            <div id="target"></div>

            <div id="gameTitle">
                <div>避けゲー</div>
                <button id="startButton">スタート</button>
            </div>

        </div>
    </main>
    <!--anime.jsを使用-->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
    <script src="main.js"></script>
</body>
</html>
```

```javascript{.numberLines caption="main.js"}
const targetelem = document.getElementById("target");
const startButton = document.getElementById("startButton");
const gameTitle = document.getElementById("gameTitle");

// 主人公を非表示にする
targetelem.style.display = "none";

// スタートボタンのクリックイベント
startButton.addEventListener("click", function () {
    // ゲームタイトルとスタートボタンを非表示にする
    gameTitle.style.display = "none";

    // target を表示する
    targetelem.style.display = "block";

    // 主人公を移動領域の中心に
    anime({
        targets: "#target",
        translateX: targetField.offsetWidth / 2 - targetelem.offsetWidth / 2,
        translateY: targetField.offsetTop + targetField.offsetHeight / 2 - targetelem.offsetHeight / 2,
        duration: 0,
        easing: "linear",
    });

});
```

<iframe height="300" style="width: 100%; height: 600px;" scrolling="no" title="Example_01" src="https://codepen.io/YasaiRa-men/embed/XWQvLRQ?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/XWQvLRQ">
  Example_01</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 主人公を動かしてみよう

-   主人公の移動において、移動する範囲を決めた場合、条件分岐を使って主人公が範囲から出ないようにしなければなりません。

<iframe height="300" style="width: 100%; height: 600px;" scrolling="no" title="Example_02" src="https://codepen.io/YasaiRa-men/embed/QWPeXMx?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/QWPeXMx">
  Example_02</a> by バナナフラ�� (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 障害物を降らせよう

-   今までのものを組み合わせて、ゲームを組み立てるとこのようになります。

<iframe height="300" style="width: 100%; height: 600px;" scrolling="no" title="Game" src="https://codepen.io/YasaiRa-men/embed/YzMmoKX?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/YzMmoKX">
  Game</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

-   画像のリンクは[こちら](https://github.com/YasaiRa-men/Sakepuru_png)から

-   `Code`から`Download ZIP`で画像をダウンロードできます。

-   target の div を img に変えることで、好きな画像に変更できます。

![img](figs/game/download.png)

## GitHub にゲームを公開する手順

### 1. GitHub アカウントを作成する

-   GitHub の公式サイト（https://github.com）にアクセスし、アカウントを作成します。

### 2. 新しいリポジトリを作成する

-   GitHub にログイン後、右上の「+」アイコンをクリックし、「New repository」を選択します。
-   リポジトリ名を入力し、必要に応じて説明を追加します。
-   「Public」を選択し、「Create repository」をクリックします。

### 3. Git をインストールする

-   Git がインストールされていない場合は、公式サイト（https://git-scm.com）からダウンロードしてインストールします。

### 4. プロジェクトフォルダを Git リポジトリにする

-   ターミナル（またはコマンドプロンプト）を開き、プロジェクトのフォルダに移動します。

```bash
cd /path/to/your/project
```

-   Git リポジトリを初期化します。

```bash
git init
```

### 5. ファイルを追加してコミットする

-   すべてのファイルをステージングエリアに追加します。

```bash
git add .
```

-   変更をコミットします。

```bash
git commit -m "初回コミット"
```

### 6. リモートリポジトリを追加する

-   GitHub で作成したリポジトリの URL をコピーし、以下のコマンドでリモートリポジトリを追加します。

```bash
git remote add origin https://github.com/username/repository.git
```

（`username`と`repository`は自分の GitHub アカウント名とリポジトリ名に置き換えてください。）

### 7. リモートリポジトリにプッシュする

-   最後に、ローカルの変更を GitHub にプッシュします。

```bash
git push -u origin master
```

### 8. GitHub Pages で公開する（オプション）

-   GitHub リポジトリの「Settings」タブに移動し、「Pages」セクションを見つけます。
-   「Source」ドロップダウンメニューから「master branch」を選択し、「Save」をクリックします。
-   数分後、指定した URL でゲームが公開されます。

これで、あなたのゲームが GitHub に公開されました！他の人と共有して楽しんでください。
