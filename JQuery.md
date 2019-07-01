# JQuery メモ
## JQuery の操作
以下の２つが基本となる
1. JQueryオブジェクトを作成
2. そのオブジェクトに対してメソッドを呼び出す

- JQueryはJavaScriptなので、文末に **セミコロン** が必要
- コメントアウトもJavaScriptと同様に //

```
$ ('セレクタ').メソッド(引数);

// ('セレクタ') JQueryオブジェクト
// メソッド(引数) メソッドの呼び出し
```

- セレクタはhtmlの **タグ名** や **class名**  CSSのセレクタと同じ
- それに合致した要素がJQueryのオブジェクトになる

```
$( funciton(){
    $('h1').hide();
} )

```


#### html上でのJavaScriptの読み込み
- html上に以下を記入
- htmlは上から実行されるので、表示を誤らせないように、JavaScriptの読み込みは **</body>の直下** に記入

```
<!-- script.jsの読み込み -->
<script src="script.js"></script>

</body>
</html>
```


### classとidをセレクタに指定する
- htmlタグに名前をつける方法として、classと同様にidがある
- id はclassと同じように用いるが、**一つのページ内で、同じidは一度しか使えない**

```
<ul id = "list >
  <li class="item"> リスト1 </li>
  <li class="item"> リスト2 </li>
</ul>
```

- classとidのセレクタの指定。
  - cssのセレクタと同様に、 **class名の前には . (ドット）**, **idの前には # （シャープ）を用いる**
  - idは同一ページに一度しか用いられないので、JQueryの処理が高速化する。なのでなるべくJQueryのオブジェクトセレクタには、**id** を用いる。

```
[cssのセレクタ]
- idセレクタには #
# list {
  margin: 10px;
}

- classセレクタには .
.list-item {
  color: blue;
}

[JQueryのセレクタ]
$ ('#list').css('margin', '20px'); // idセレクタ

$('.list-item').css('color', 'red'); // classセレクタ
```

### displayプロパティ 隠すと表示
-  css において、**display: none;** とすると要素を隠す
- 隠れた要素を表示するメソッドとして、 **show** メソッドがある
- hideとセットで覚える

```
[.css]
img {
  diplay: none;
}

[.js(JQuery)]
$('img').show)();
```

- アニメーションつきで隠れた要素を表示する
  - fadeOut - fadeIn
  - slideUp - slideOut

```
[js]
$('セレクタ').fadeIn(); // 要素を標示するさいに、徐々に標示するアニメーションを追加
$('セレクタ').fadeOut('slow'); // 引数でアニメーションの表示速度を指定

$('セレクタ').slideDown(); // 要素を表示するさいに、上から下にスライドするアニメーションを追加
$('セレクタ').slideDown('slow')

```

## イベント
- 処理を行うタイミングを設定できる。ユーザーによってクリックなどの操作が行なわれたときの、予約したイベント内の処理を実行する
- **$('セレクタ').イベント名(funciton(){});**

```
$('セレクタ').イベント名(funciton(){
  // イベント発生時に実行したい処理
  });
```

### clickイベント

- セレクタがクリックされたときの処理を設定できる

```
[index.html]
<div id="hide-text">說明を隠す</div>
<p id = "text"> ボタンをクリックすると文章が隠れる</p>

[script.js]
$('#hide-tecxt').click(function(){
  $('#text').hide();
  })
```

### cssメソッド
- CSSを変更できるメソッド。
- １つ目の引数にCSSの **プロパティ** を、2つ目の引数にプロパティの　- **値** を入れる

```
[script.js]
$('セレクタ').css('プロパティ名', '値');

[css]
p {
  color: bule;
}
img {
  display: none;
}
[js]
$('p').css('color', 'red');

$('h1').css('display', 'none'); // h1を隠す
$('img').css('display', 'block') // デフォルトで非表示のimg要素を表示
```

### htmlを変更する
#### textメソッド
- htmlそのものを変更できる
- $('セレクタ').text('書き換える文字列') のように指定する

```
[index.html]
<p> こんにちは</p>

[script.js]
$('p').text('こんばんは');
```

#### htmlメソッド
- 要素の中身のhtmlを書き換える
- 引数が、単なる文字列ではなく、htmlなのが、textメソッドとの違い

```
[index.html]
<p>こんにちは</p>

[script.js]
$('p').html('<span>こんばんは</span>');
// <p><span>こんばんは</span></p>
// p要素のなかにhtmlが追加される
```

## this
- **$(this)** はイベントの中で、そのイベントが起こった要素を取得できる
- $()のなかでthisはクオートでは囲まない
- this はイベントが設定されたさいに、そのイベントが起こった要素だけに処理を行いたい場合に設定する
  - 下の例では、リストの中でも **クリック** されたものだけが、色が赤色になる

```
[index.html]
<ul>
  <li>リスト1 </li>
  <li>リスト2</li>
  <li>リスト3</li>
</ul>

[script.js]
$('li').click(function(){
  $this.css('color', 'red');
}
```

## 変数とメソッドチェーン
- 同じJQueryオブジェクトを複数回使用するときは、変数にする
- JQueryの処理も高速化される
- JavaScriptと同様に、変数の宣言には **var** を用いる
- JQueryオブジェクトを格納するときには、わかりやすいように、変数の頭に **$** をつける

```
var $div = $('div');

$div.css('color', 'red');
$div.html('JQuery');
$div.fadeOut();
```

- 同じJQueryを複数回使用する際には、メソッドチェーンをつかい処理を高速化する
- 一つのJQueryオブジェクトに連続してメソッドが利用できる構文
- **$('セレクタ').メソッド().メソッド().....**

```
$('div').css('color', 'red').html('JQuery');
```

## 子要素を取得する find children
- すべての子要素から、指定したセレクタをもつ要素を取得する
  - 下の例では、<div id="wrapper"> から </div>の中にあるすべての<a>要素を取得できる

```
[index.html]
<div id="wrapper">
  <a href="#">リンク1</a>
  <p>
    <a href="#">リンク2</a>
  </p>
</div>

[script.js]
$('#wrapper').find('a').css('color', 'red');
```

- childrenメソッドは、指定したセレクタが持つ子要素を **（一階層だけ下）** の中から、否定したセレクタに合致した要素を取得する
  - 舌の例では、<div id="wrapper">の子要素は、<a>タグと<p>タグで１つずつなので、<a>タグが取得される


```
[index.html]
<div id="wrapper">
  <a href="#">リンク1</a>
  <p>
    <a href="#">リンク2</a>
  </p>
</div>

[script.js]
$('#wrapper').children('a').css('color', 'red');
// リンク1だけ赤くなる
```

## hoverイベント マウスが乗った時、外れたときに指定の処理
- 要素にマウスが乗ったときに、外れたときに指定した処理を行うイベント
- **$('セレクタ').hover(マウスがのったときの処理, マウスを外したときの処理);**
- 引数は2つ

```
$('div').hover(
  function(){
    //マウスを載せたときの処理
  }, //functionの間にはコンマ
  function(){
    //マウスを蓮したときの処理
  }
);
```


## JQueryの読み込み
- JQueryライブラリの読み込み
  - html内に、JQueryライブラリを読み込むのが一般的。ライブラリはインターネット経由で読み込むのが一般的。head-タグの中に、<script>タグで指定するのが一般的
- JQueryファイルの読み込み
  - .js形式のファイルを読み込むことが一般的。
  - htmlファイルで、<script src="ファイルのURL"></script> と各
  - </body>の直前に書く
```
[index.html]
<head>
  <script src="https://...jquery.min.js"></script>
</head>

<body>

<script src="script.js"></script>
</body>
```

- JQueryの型
  - JQueryは、HTMLの中身を操作するために、HTMLの読み込みが完了してからJQueryによる操作を開始する
  - そのためには、readyイベントを使用する。$(document).ready();の中身にJQueryの処理を記述する
  - 省略形も用意されており、**$(function(){   });** とも×

```
[script.js]
$(document).ready(function(){
    //処理を記述
  });

or

$(function(){
    //処理を記述
  });
```


### モーダルの表示
1. モーダルをcssで非表示にする
2. ログインボタンにclickイベントを設定
3. clickイベントでモーダルを表示

```
[stylesheet.scc]
.login-modal-wrapper{
  display: none;
}
[script.js]
$('#login-show').click(function(){
    $('#login-show').fadeIn();
  });
```
