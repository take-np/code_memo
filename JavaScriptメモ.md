## プログラムの実行
- cosole.log() ;
  - ()内の文字を出力する。文字列の出力は **"" ''** で囲む
  - 文末には **;** をつける

- //はコメントアウト
```
  [script.js]
  console.log("Hello World");
  // 実行結果 Hello World
```
- 文字列の連結も可能 ("a" + "a");
## 記法一覧
### ブロック
- 0個以上の文をグループにするもの
```
{
  var x = 3;
  var y = 4;
  console.log(x+y);
}
```
### コメントアウト
```
一行 ： //
複数行 ： /* ~~~ */
```

### アラート
```
 aloert("hello world")
 // ポプアップで表示される
```

htmlとして出力
```
<script>document.body.innerText = "Hellor World"
</script>
<body></body>タグの中に出力される
```
## 変数 var と let の違い

1. 重複を許容しないlet

```
var hensuu = "変数1";
var hensuu = "変数2";

console.log(hensuu); // 変数2と表示　最初の宣言は上書きされる

let hennsuu = "へんすう";
let hennsuu = "へんすう２";
console.log(hennsuu); // Idemtifer 'hennsuu' has already been declardとエラーになる
　　　　　　　　　　　 // 変数'hennsuu'はすでに宣言済みです
```
2. ブロックスコープを認識するlet

```
[var]
if (true) {
    var i = 1;
}

console.log(i); // 1と出力

[let]
if (true) {
    let i = 2;
}

console.log(i); // 変数iはスコープ外なのでエラーとなる

```

#### const

- 再代入不可能な変数を作る (つまり定数にできる)
- 再代入しようとするとエラーになる
- letと同じブロックスコープ
- 巻き上げは起きる
- **ほとんどは再代入は不要なのでconstを使う**
- constを使っておけば値が変わることが無いので、値が変わるかも?という懸念が無くてコードが読みやすい
- forのイテレータのような再代入が必要な所のみletを使う

## 変数の宣言 let
  ```
  let name = "John"
  console.log(name); //John
  ```
- 変数の宣言として **let**
- 変数に文字列や数値が代入されている場合には、計算や文字列の連結が可能になる
  ```
  let name = "鈴木";
  console.log(name + "さん"); //鈴木さん

  let number = 11;
  console.log(number + 5); // 16
  ```
### 変数の上書き let はつけない
  ```
  let name = "John";
  console.log(name); //John
  name = "Kate";
  console.log(name); //Kate
  ```
### 変数自身の更新
  ```
  let number  = 2;
  console.log(number); // 2
  number = number + 3;
  console.log(number); // 5
  ```
#### 省略形

  x = x + 10 → x += 10
  x = x - 10 → x -= 10
  x = x * 10 → x *= 10
  x = x / 10 → x /= 10
  x = x % 10 → x %= 10


## 定数 const
- 定数の宣言 const
- 定数は一度代入した値を **更新できない** 。変数の場合には更新できる
- コードを実行した場合にはエラーがでる
- 開発段階においては定数を用いることで、勝手な変数の変更を防止できる
  - Progateにおいてはこれから定数を使用するみたいだが、なぜだろうか
  ```
  const name = "John";
  ```

## 文字列の連結 テンプレートリテラル
- 文字列や定数の連結には + 以外にもテンプレートリテラルが使える
- 文字列のなかに、定数（変数）を埋め込むことが出来る
- 文字列のなかに **${}** とすることで文字列のなかに埋め込める
- 埋め込む文字列全体は、**``（バッククォート）** で囲む

  ```
  const name = "lalala";
  console.log(`こんにちは、${name}さん`); // こんにちは、lalalaさん
  const age = 14;
  console.log(`${name}は${age}歳です`); // lalalaは14歳です
  ```


## 条件分岐 if
条件式の描き方

  ```
  if (条件式){
    処理 // 条件式が成立すれば、時刻される
  } // セミコロンは不要

  const number = 12;
  if (number > 10){
    console.log("number は 10より大きい")
  }

  [参考]
  const number = 12;
  console.log(number > 10);
  // true
  ```

### 比較演算子
- 以上-以下、 より大きい（小さい）は他の言語とほぼ同じ
- ただし、等しいかを比べるときには＝が一つ多い
- このイコールの記号は、文字列同士の比較にも使える

  aとbが等しい a **===** b
  aとbが等しくない a **!==** b

### JavaScriptの書き方 第一級関数としての特徴を反映して
- 他の値と同様に名前無しで扱える
- 変数に代入できる
- 配列に格納できる
- オブジェクトのプロパティにできる
- 関数の引数にできる
- 関数の返り値にできる
- プロパティが持てる


- JavaScriptの関数は、他の数値や文字列と同じように扱うことができます（一種のオブジェクト）。つまり名前がなくても関数を作れるということです。

```
[関数の名前を宣言していない]
var inc = function (x) {
  return x + 1;
};

inc(3); // => 4

[変数に代入せずに使う]
(function(x) { return x + 1; })(1); // => 2
```
### 条件が成立しない場合 else、if else
- Javaと同じ

```
  if (条件式){
    条件がtrue
  }else {
    条件がfalse
  }
  const number = 7;
  if (number > 10){
    console.log("10より大きい");
  }else{
    console.log("10より小さい");
  }

  if  (number > 10) {
    条件式1
  } else if (number > 5) {
    条件式2
  } else {
    条件式上記以外
  }

```

### 条件の組み合わせ
- かつ ** && **
- または ** || **  ex. x < 10 || x > 30

### switch文 case default
- **ある値によって処理を分岐する** 場合には、switch文を用いる
- 下記の場合には、定数colorが赤のときに、ストップという文字が表示される
- **break** が重要。breakがないと、合致したcaseの処理を実行したあとに、その次のcase文も実行してしまう。
- caseの条件指定は、セミコロンではなく、**:** コロン
- 条件の値にどれも一致しないときには、**default** のブロックが実行される

```
switch (条件の値){

} //セミコロンは不要

const color = "赤";
switch (color){

}

const color = "赤"
switch (color){
  case "赤": // コロン
    console.log("ストップ");
    break;  // 定数color の値が "赤" のときに実行される
  case "黄": //コロン
    console.log("要注意");
    break; //定数colorの値が "黄" のときに実行される
  default:
    console.log("colorの値が正しくありません");
    break;
}
```

## 繰り返し処理 while for
- 条件式がtureの間、{}内の処理を繰り返す
- {} のあとにセミコロンは不要
- while 文の条件がfalseにならないと、処理が無限に続く無限ループに陥るので、注意する
```
  while(条件式){
    処理
  } // セミコロンは不要
```

```
let number = 1;
while(number <= 100) {
  console.log(number);
  number += 1;
}
```

### for
- for 文のほうが、while文よりシンプルに記述できる
- 条件式のなかは、** ; ** で区切る]
```
for (変数の定義; 条件式; 変数の更新){
  処理
} //セミコロンは不要
```

```
for (let number = 1; number <= 100; number += 1){
  console.log(number);
}
```

- 計算式の省略
- number += 1 → **nummber ++**
- number -= 1 → **number --**

## 配列
- 複数の値をまとめて監理する **配列**
- [1, 2, 3]のように作成。
- 配列にはいっているそれぞれの値のことを **要素** とよぶ
- 配列も一つの値なので低ぐうに代入できる（変数にも代入はできるよな）
- 定数に代入するときには 慣例として定数名が複数形になる

```
const fruits = ["apple", "banana", "orange"];
console.log(fruits); // ["apple", "banana", "orange"];
```
- 配列にはそれぞれの要素に、**インデックス番号** がふられている
- インデックス番号は 0 から始まる

```
console.log(fruits[0]); // apple
console.log(fruits[1]); //  orange
```
### 配列の要素の更新
```
fruits[0] =  "grape";
console.log(fruits[0]); // grape
```

### 配列の要素を繰り返し処理で取得する for文の利用
- for文で、配列のインデックス番号に対応する繰り返し閭里を実行する
- そのときの変数の値は ** 0 ** から始まることに注意する

```
const fruits = ["apple", "banana", "orange"];
for (let i = 0; I < 3; i++){
  console.log(fruits[i]);
}
```
### 配列の要素数の取得 lengthの利用
- lengthを用いると、配列の要素数を取得できる
- またその取得数を利用して、for文の条件式の書き換えが可能に

```
const fruits = ["apple", "banana", "orange"];
console.log(fruits.length); // 3

for (let i = 0; i < fruits.length; i++){
  console.log(fruitis[i]);
}
```

## オブジェクト
- オブジェクトは、配列と同様に複数のデータをまとめて監理するために用いられる
- - 配列は複数の値を並べて監理するのに対して、オブジェクトは、それぞれの値に **プロパティ** と呼ばれる名前をつけて監理する
- 配列は[]で囲むが、オブジェクトは{}で囲む
- プロパティと値の間は **:** で区切る,配列と同じく要素の間は、,(コンマ)で区切る
- オブジェクトも定数に代入可能
- オブジェクトの値を取り出すには **オブジェクト名.プロパティ名** と記述する
```
//配列
[1,2,3]
//オブジェクト
{プロパティ1: 値1, プロパティ2: 値2, プロパティ3: 値3}
```

```
const item = {name:"手裏剣", price:300};
console.log(item); //{name:"手裏剣", price:300};
console.log(item.name); // 手裏剣
```

オブジェクトの値を更新する

```
const item = {name: "手裏剣", price:300};
item.price = 500;
cosole.log(item.price); // 500
```

#### 複雑なオブジェクトを扱う
- オブジェクトの値の部分には、文字列や数値だけでなく、**オブジェクト** をもちいることもできる

```
const character = {
  name:"ねこ",
  age: 14,
  favorite:{
    food:"ラーメン",
    sports: "サッカー",
    color: "青",
  },
  // favoriteプロパティの値が、オブジェクトになっている
}
```

### オブジェクトを配列にもつ配列
- 配列の要素には、文字列や数字だけでなく、オブジェクトも使うことができる

```
[{プロパティ1: 値1, ...}, //オブジェクト
{プロパティ2: 値2, ...}, ... //オブジェクト
]

const items =[
  {name:"手裏剣", price: 300},
  {name:"刀", price:1200 },
] ; //セミコロンを忘れない

// 配列[インデックス番号]で取り出し
console.log(items[1]); // {name:"刀", price:1200}

// 配列[インデックス番号].プロパティ名 で取り出し
console.log(items[1].name); // 1200
```

```
[ 応用例 ]
const characters = [
  {name: "aaa", age: 1},
  {name: "bbb", age: 2}.
  {name: "ccc", age: 3},
];

for (let i = 0; i < characters.length; i++){
  const character = characters[i];
  console.log(`名前は${character.name}です`);
  console.log(`年齢は${character.age}歳です`);
}
```

- 配列に対して、存在しないインデックス番号の要素や、オブジェクトの存在しないプロパティの要素を取得しようとすると **undefined** と出力される
- undefinedは特別な値で、値が定義されていないことを意味する

```
const animals = ["dog", "cat", "shieep"];
console.log(animals[5]);  //undefined

const character = {name: "aaa", age: 14};
console.log(character.email); //undefined
```
### undefinedの表示のときの対処法 if elseで対処する
```
const characters = [...];
for (let i = 0; i < characters.length; i++){
  const character = characters[i];
  if (character.age === undefined){
    // ageの値が、undefinedのときの処理
  } else {
    // ageの値が、定義されているときの処理
  }
}
```

## 少し入り組んだ処理
- オブジェクトの値の部分には、文字列や数値だけでなく、**オブジェクト** をもちいることもできる
- また同様に、**配列** も用いることができる

```
const character = {
  name:"ねこ",
  age: 14,
  favorite:{
    sports: "サッカー",
    color: "青",
  },
  // favoriteプロパティの値が、オブジェクトになっている
  food:["ラーメン", "うどん", "やきそば"]
  // foodの値が配列になっている


}
```

- 呼び出すさいには **オブジェクト名.プロパティ.プロパティ** で呼び出す

```
console.log(character.favorite);
//  favorite:{sports: "サッカー", color: "青",}
console.log(character.favorite.food);
// ラーメン
```

## 関数
- 関数はいくつかの処理をまとめたもの
- **functioin()** とその後ろの **{}** のなかにまとめたい処理を書くことで関数を用意することができる
- 関数を定義する、という

### 関数の定義方法
1. 関数宣言
2. 関数式
3. コンストラクタ

https://www.sejuku.net/blog/31671

[関数宣言]
- 関数をそのまま宣言することで、プログラム内で利用することができる
- 関数名は **sample**
```
[関数宣言]
// sampleは 関数名
function sample() {
  //処理を記入
}
```
[関数式（関数リテラル）]
- 関数を宣言するさいに **関数名を記述しなくてもよい**
- そのため、**無名関数** や **匿名関数** ともよばれる
- 関数名を指定せずに、そのまま変数へ式を代入している
- JavaScriptの関数は、文字列や数値と同じく **データの値** として存在しているから、このような変数へ直接記入する書き方が許容される


```
[関数式（関数リテラル]
var sample = function() {
  // 処理を記入
}
```

[コンストラクタで書く]
- functionオブジェクトのコンストラクタを利用して関数を提議する
- 第一引数に引数名として textを指名、第二引数に、処理の内容を記述
```
var sample = new Function('text', 'console.log(text)');
```

```
const introduce = function(){
  console.log("Hello");
  console.log("I am from America");
}; //セミコロンを忘れない
```
- 定数の呼び出しをすることで、関数の中の処理を実行できる introduce();
- これを **関数を呼び出す** と呼ぶ

- 他の関数の定義の方法
- functionが関数を宣言するときにキーワード。
- function直後が関数名

```
function sum(n) {

  var sum = 0;
  for (var i = 0; i <= n; i++){
    sum += i;
  }
  return sum;
}

sum(3); => 6

```

```
[配列に格納]
var funcList = [
  function() { return 1; },
  function() { return 2; },
  function() { return 3; }
];

funcList[1](); // => 2

[オブジェクトのプロパティにする]
// オブジェクトのプロパティに設定
var obj = {
  func: function() { return 1; }
};

obj.func(); // => 1

```

- 関数の引数として使う

```
function func(callback) {
  return callback();
}

func(function (){ return 1; }); // => 1
```

- 関数を他の関数の返り値として使う

```
// 関数を返り値として使う
function func() {
  return function() { return 1; };
}

func()(); // => 1
```

- 関数はオブジェクトとして扱えるので、プロパティを持たせられる


```
// 関数にプロパティを持たせる
var func = function() { return 1; };
func.retType = "number";

```

### オブジェクト指向

```
var Human = function(speed) { // オブジェクトの設計
  this.pos = 0; // 位置
  this.speed = speed; // 走る速度
};
Human.prototype.run = function() { this.pos += this.speed; return this.pos; }; // 走るという機能の定義

var kindergartener = new Human(1); // 幼稚園児オブジェクトを作る
var highSchoolStudent = new Human(10); // 高校生オブジェクトを作る
var hero = new Human(100); // ヒーローオブジェクトを作る

kindergartener.run(); // => 1
highSchoolStudent.run(); // => 10
hero.run(); // => 100
```

- オブジェクトの設計のところでは、無名関数のような書き方をします。
- ここでいうthisは、この設計から実際にオブジェクトを作ったときの、自分自身にあたるものです。
- prototypeというのは共通の機能（値）を定義するためのもの。runは、走る能力に関わらず、行う内容は共通しているので、prototypeとして定義する。
- http://www.ituore.com/entry/javascript-basic#f-1a980aea





### アロー関数
- ES6から新しく導入された書き方。特別にアロー関数と呼ぶ
- function() の部分を **() =>** とする
- 呼び出し方は functionの定義の場合と変わらない

```
const introduce = ()=> {
  console.log("...");
  console.log("...");
};
```

### 引数
- 関数に与える追加の情報
- 関数を呼び出すときに、値を渡すことで、関数のなかでその値を利用できる

```
const 定数名 = (引数名)=> {
  処理
};

const introduce = (name)=>{
  console.log("こんにちは");
  console.log(`私は${name}です`);
};
introduce("にんじゃわんこ"); // 私はにんじゃわんこです
introduce("ひつじ"); // 私はひつじです
```

- 複数の引数を受け取る

```
const 定数名 = (第一引数, 第二引数, ...)=>{
  //処理
};
const introduce = (name,age) => {
  //処理
};
const introduce = (name, age) => {
  console.log(`私は${name}です`);
  console.log(`私は${age}歳です`);
};

introduce("わんこ", 14);
// 私はわんこです
// 私は14歳です
```

### 戻り値
- 関数の処理結果を、呼び出し元で受け取る処理。
- その結果を **戻り値** とよび、この挙動を **関数が戻り値を返す** という
- 関数のなかで **return** を使うと、呼び出し元で値を受け取れるようになる
- **return 値** と書くことで、関数はその値を戻り値として返す
- 呼び出した関数に戻り値がある場合には、関数の呼び出し部分がそのまま戻り値に置き換わる
  - 関数の呼び出し部分を、定数に代入も出来る
```
const add = (a, b) => {
  return a+ b;
};
const sum = add(1, 3);
console.log(sum); // 4
```
- 戻り値も引数と同様に、様々な値をもちいることができる

```
const check = (number) => {
  return number % 2 === 0;
};
console.log(check(6)); // true
console.log(check(7)); // false
```
#### returnによる処理の終了
- returnは戻り値を返すだけではなく、関数の処理を終了させる。そのため、returnのあとにある関数内の処理は実行されない

```
const add = (a, b) => {
  return a + b;
   console.log("計算しました"); // 実行されない
};
```

### スコープ 関数内で定義した定数が使える範囲
- 関数の引数や、関数内で定義した定数は、その関数の中でしか使うことができない
- 一方で関数の外で定義した関数は、関数の中でも外でも使うことが出来る
```
const introduce = () => {
  const name = "わんこ";
  // 定数nameが使える範囲
};
// 定数name は使えない範囲

const name = "わんこ";
const introduce = ()=> {
  // 定数 name が使える
};
 // こちらでも定数nameは使える
```

## クラス
- ES6 から　新しく導入された文法。
- JavaScriptのライブラリ（Vue.js React）を学習するうえでは必須の知識になっている

- オブジェクト
  - 複数の値をプロパティという名前をつけて管理できるもの
```
const user = { name: "にんじゃわんこ", age: 14};
console.log(user.age); // 14
```

- オブジェクトの「値」の部分には、関数を用いることもできる
- プロパティの　値として関数を記述する
- その関数を呼び出すには、**定数名.プロパティ名()** とする

```
const 定数名 = {
  プロパティ名 : () =>{
    処理
  };
};

//呼び出すとき
定数名.プロパティ名() ; // 関数の呼び出し
// 最後の () を忘れないようにする


const user = {
  name = "わんこ";
  greet : () =>{
    console.log("こんにちは");
  };
};

user.greet() ; // 関数の呼び出し
```
## オブジェクトを量産する クラス
- 似たようなデータを大量に生産する。
- ウェブサービスでは、オブジェクトを大量に生産している。
  - 例えばユーザーに関するデータなど

- 効率よくオブジェクトを生産するためには最初に設計図を用意すればよい。その設計図のことを **クラス** とよぶ
- 下のように定義することで、新しくクラスを用意できる

```
class User { // User はクラス名

}
```
### インスタンスの生成
- クラスからオブジェクトを生成するためには、**new クラス名()** とする
- クラスから生成したオブジェクトは **インスタンス** とよぶ
  - Animalクラスからのインスタンスを 、**Animalインスタンス** と呼ぶ

```
class Animal {

}
const animal = new Animal(); // Animalインスタンス

```

### クラスの中身を生成する コンストラクタ
- インスタンスを生成するときに実行したい処理や設定を追加するための機能を **コンストラクタ** と呼ぶ
- クラスの中括弧{} 内に **constructor() {}** と記述する
- コンストラクタの中に記述した処理は、**インスタンスが生成された直後に実行される**
- インスタンスが生成されたごとに毎回実施される。

```
class Animal {
  constructor() {
      console.log("こんにちは！"); //インスタンスが生成された直後に実行される
  }
}

const animal1 = new Animal(); // こんにちは！
const animal2 = new Animal(); // こんにちは！

```

### プロパティと値を追加する
- コンストラクタのなかで、生成したインスタンスに関する情報を追加する
- コンストラクタの中で **this.プロパティ名** とすることで、生成されたインスタンスにプロパティと値を追加することができる
- コンストラクタのなかで追加した値は、 **インスタンス.プロパティ** とすることで、クラスの外で実行できる
```
class Animal {
  constructor() {
    this.name = "レオ"; // this. プロパティ名 =  値 ;
  }
}

const animal = new Animal();
console.log(animal.name): // レオ
```

### インスタンスごとに値を変える
- 上記のような設定では、生成されるインスタンスはすべて、「レオ」「3」のように同じ値になってしまう
- コンストラクタは、関数と同様に引数を受け取ることが出来る
- constructor の直後の() 内に引数名を記述することで、引数をコンストラクタの処理内で実行できる
- コンストラクタに引数として値を渡すには、**new クラス名()** の **()** 内に値を追加する
```
class Animal {
  constructor(name, age){ //引数を受け取る
    this.name = name;
    this.age = age;
  }
}

const animal = new Animal("レオ", 3);
```

### メソッド
- インスタンスの動作のようなもの
- プロパティで追加した情報に対して、メソッドは処理のまとまりを示す
- メソッドはクラスのなかで定義する。 **メソッド名(){}** とすることで定義できる。メソッドは関数と似たようなもので、中括弧{} のなかにメソッドで行いたい処理を記述する
- メソッドを呼び出すときには、 **インスタンス.メソッド名()** とすることで、メソッドを呼び出し、処理を実行できる
- メソッド内でインスタンスの値を使用するには、**this** を用いる。**this.プロパティ名** とする。
```
class クラス名{
  constructor(){

  }
  メソッド名(){
    //行いたい処理
  }
}

class Animal {
  constructor (name, age){

  }
  greet(){
    console.log("こんにちは");
  }
  info(){
    console.log(`名前は${this.name}です`); //インスタンスのnameプロパティの値になる
  }
}
const animal = new Animal ("レオ", 3);
animal.greet(); //メソッドの呼び出し
// こんにちは
animal.info();
// 名前はレオです
```

### メソッド内でメソッドを使用する
- メソッド内では、他のメソッドを呼び出すことも可能
- メソッド内で、**this.メソッド名** とすることで、同じクラスの他のメソッドを使うことが出来る

```
class Animal {
  greet(){
    console.log("こんにちは");
  }
  info(){
    this.greet(); // 同じクラスのメソッドを実行する
  }
}
```

### ファイルの分割 コードの量が増えるので、クラスを記述したファイルは別にする
- クラスを記述したファイルでの処理
- クラスを記述したファイルのクラスを、他のファイルでも使用できるようにする。
- クラスの定義のあとで、 **export default クラス名** とすることで、そのクラスを他のファイルでも使用できるようになる
   - この他のファイルでも使用できるようにする範囲は、どの程度か？ 同じディレクトリ。その下位のぢレクトリだけか。それ以上のディレクトリのファイルでも利用できるのか
```
class Animal{
  ...
}
export default Animal:
// Animalクラスを他のファイルでも使用できるようにする設定
```

- クラスを使用するファイルでの記述
- 使用するファイルの先頭で、**import クラス名 from "./ファイル名"** とする
- 拡張子の js は省略も可能

```
[script.js]
import Animal from "./animal.js"

```

### クラスの継承 効率よくクラスを作成する
- 新しく作成するクラスが、既存のクラスの一種である場合 **継承** を利用することで、効率よく作業を進められる
- 継承したクラスは、親クラスのすべての機能を引き継げる
- 継承を用いて、クラスを作成するには **extends** を用いる

```
import Animal from "./animal.js";
class Dog extends Animal{ // Animalクラスを継承
}
```
- 例えば上記のDogクラス内には、何もメソッドが定義されていないが、Animalクラスのすべての機能を引き継いでいるために、Animalクラスで定義されている「infoメソッド」などを使用できる

```
[animal.js]
class Animal{
  info(){
    this.greet():
    console.log("...");
    console.log("....");
  }
}
[dog.js]
class Dog extends Animal{

}
[script.js]
const dog = new Dog("レオ", 4);
dog.info(); //Animalクラスに定義されているメソッドを使用できる
```

- 継承して作成したクラスにもメソッドを追加できる
- メソッドでも、関数と同様に **戻り値** を使える
- ただし、子クラスで定義した独自のメソッドは、親クラスで呼び出すことはできない
```
[dog.js]
class Dog extends Animal{
  getHumanAge(){
    return this.age * 7; // メソッドでも戻り値は使える
  }
}
[script.js]
const dog = new Dog("レオ", 4);
const humanAge = dog.getHumanAge();
console.log(humanAge); // 28
```
#### 親クラスと子クラスで同名のメソッドが定義されている場合 - 子クラスのメソッドが優先して使用される
- 親クラスと子クラスで、同名のメソッドが定義されている場合には、子クラスのメソッドが優先して呼び出される
- これは、子クラスのメソッドが親クラスのメソッドを上書きしているから
- これは **オーバーライド** と呼ばれる

```
class Dog extends Animal {
  info(){
    this.greet();
    console.log(`名前は${this.name}です`);
    console.log(`${this.age}歳です`);
    const humanAge = this.getHumanAge();
    console.log(`人間年齢で${humanAge}歳です`);
  }
}
```

### コンストラクタのオーバーライド
- メソッドと同様に、コンストラクタもオーバーライドする
- 子クラスにプロパティを追加したい場合に用いる
- ただし、コンストラクタをオーバライド刷る場合には、 コンストラクタ内の1行目に、 **super()** と記述する
- 子クラスのコンストラクタ内での **super()** では、その部分でおやく明日のコンストラクタを呼び出している。
- そのため、親クラスのコンストラクタが、引数を受取る場合には、supreの後ろの丸かっこ() に引数を渡す必要がある。

```
[aniamal.js]
class Animal{
  constructor(name,age){ //(1)親クラスのコンストラクタ実行
    this.name = name;
    this.age = age;
  }
}
[dog.js]
class Dog extends Animal {
  constructor (name, age, breed){
    super (name, age);
    this.breed = breed; //(2).子クラス独自の処理を実行
  }
}
```

### HTMLとの実装
- onclick()属性をリイ要して、指定した要素がクリックされたさに、functionを動作させる

```
<button onclick="sample()"> ボタン </button>
```

## documentオブジェクト
- http://itref.fc2web.com/javascript/document.html


## ES5 ProgateのES5より配列の操作 push
-
