```
class Java{
  public static void maind(String[] args){
    System.out.println("Hello World");
  }
}
// コメント

int number;
number = 3;
String number;
number = "3";

class Java {
  public static void main(String[] args){
    System.out.println(number);
  }
}
```

### 変数の初期化
- 変数定義と同時に変数の値を代入すること

```
int number = 3;
String text = "Hello World";
```

### 変数の更新
- 同じ処理内で、同一名の変数を定義できない
- なので、上書きをするさいには、データ型の指定をつけないようにする

```
// こちらエラーになる
int number = 3;
int nubmer = 5;
//こちらは大丈夫
int number = 3;
number = 5;
```

### 自己代入
```
x += 1:
x -= 1:
x *= 1:
x /= 1:
x %= 1:
```

値が1のときの更に省略
```
x++;
x==;
```

## 記法
Javaは基本的にキャメルケース
```
Yes: userName
No : user_name
```

## 変数の型
|  |  |
|:------------ |:------------|
|int  | 整数 |
|double | 少数 |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |

### 型変換
- 自動で型を変換してくれる
- String + int + String → String
- int / int = int

```
System.out.println( 5 / 2 ); // 2

double / double = double
System.out.println( 5.0 / 2.0); // 2.5

double / int = double
System.out.println(5.0 / 2); // 2.5
```

- int 同士の割り算で、小数点以下まで算出する場合
- どちらか1つをキャストする

```
int number1 = 13;
int number2 = 4;
System.out.prinln((double)number1 / number2); // 3.25
```

## boolean
- true
- false

```
boolean bool = true;
```
```
System.out.println(true);
System.out.println(6 + 2 == 5);
System.out.println(6+2 != 5);
```

### 論理演算子
```
&& //かつ
|| //または
!(x >= 30) // xが20のとき、true
```

## 条件式

```
if (条件式) {
  処理;
}

if (条件式)[
  処理:
} else {
  処理;
}

if (条件式) {
  処理;
} else if ( 条件式 ) {
  処理;
} else {
  処理;
}
```

```
Switch(条件の値){
  case 1:
    処理;
    break;
  case 2:
    処理:
    break;
  case 3;
    処理;
    break;
}
```
`break` がないと、下の処理まで実行される

### default
- switch文においてどの処理とも一致しなかったときに実行する処理を `default` に指定

```
switch ( rank) {
  case1:
   処理;
   break;
  case2:
    処理;
    break;
  case3:
    処理;
    break;
  default:
    処理;
    break;
  
}
```

## 繰り返し処理
### while 

```
while (条件)[
  繰り返す処理;
]
```

### for
```
for (初期化; 条件; 変数の更新) {
  処理;
}

for (int i = 5; i <= 5; i++){
  System.out.println(i);
}
```

### 繰り返し処理の操作
- break
  - 終了
  - 以降の処理が停止される

```
for (int i=1; i <=10; i++){
  if ( i > 5){
    break:
  }
  System.out.println(i);
}
```

- continue 
  - 当該の処理をスキップ

```
for (int i = 1; i <=10; i++){
  if(i % 3 ==0 ){
    continue;
  }
  system.out.println(i);
}

//処理結果 1,2,4,5,7,8,10
```

## 配列
- ※[]の間にスペースを設けない
  
```
int[]
int[] numbers = {4, 4 ,3};
```

```
String[]
String[] names = {"johen", "lala", "nnn"}
```

### 配列の要素の上書き
```
names[0] = "Willaiam";
No: names[3] = "julia"; // 存在しない要素には値を代入できない
```

### 配列と繰り返し
```
String[] names = {"John", "Kate", "Bob"};
for (int i = 0; i < 3; i++){
  System.out.println("Hello" + names[i]);
}

```

#### lengthメソッド
```
String[] names = {"John", "Kate", "Bob"};
for (int i = 0; i <names.length; i++){
  System.out.println("Hello" + names[i]);
}
```

### 拡張用のfor文
- 配列の各要素の値を順に代入する変数を用意する

```
for (Data型 変数名: 配列名) {
  繰り返す処理;
}

String[] names = {"John", "Kate", "Bob"};
for (String name: names) {
  System.out.println(name);
}
```

# メソッドとクラス
- `public static void`
- メソッドはクラスの中に定義する。クラスのなかに定義しないとエラーになる

```
public static void メソッド名(データ型 変数名1, データ型 変数名2){
  実行する処理;
}
[Main.java]
public static void hello(){
  System.out.println("Hello World);
}
```

## 戻り値
- メソッドの処理結果を、メソッドの呼び出し元で使用する場合に`戻り値`を返すようにする
- 戻りがある場合、メソッドの呼び出し部分が、そのまま値に変わる。なので変数に代入できる
- **void** は **戻り値がない** という意味
  - voidは「空隙」という意味  
  - System.out.printlnは、戻り値を返さずに、**出力** をするだけ

```
public static **戻り値のデータ型** メソッド名 (引数) {
  return 戻り値;
}

public static **int** add (int a, int b){
  return a + b; //戻り値のデータ型は int
}

public static void main(String[] args) {
  int total = add(7,5);
  System.out.println(total);
}
public static int add( int a, int b){
  return a + b;
}

// void
// 出力するだけで、戻り値を返さない
public static void hello(){
  System.out.println("こんにちは");
}
```
- 同じ名前の変数は使用できない
  - ただし、引数の型や、個数が違う場合には使用できる

```
// メソッドを組み合わせる
[Main.java]
public static void main(String[] args){
  System.out.println(average(3,8));

  public static double average(int a, int b){
    int total = add(a, b):
    return (double)total / 2;
  }

  public static int add(int a, int b){
    return a + b;
  }
}
```

### 真偽値を返す
```
public static void main(String[] args){
  int number = 9;
  if (isEven(number)){
    System.out.prinln(number + "は偶数です");
  } else {
    System.out.prinln(number + "は奇数です");
  }

  public static boolean isEven(int a){
    return a % 2 ==0;
  }
}

```

# クラス
- クラスの定義 `class クラス名`
- クラス名の最初の文字は  **大文字**
- ファイル名は  **クラス名.java**  
- 呼び出すときには、 **クラス名.メソッド名** 

## mainメソッド
- java はファイルではなく、 **クラス** を実行する
- 実行時には、mainメソッドが呼ばれるが、 **正確には、mainメソッドを持つクラスしか実行できない**
-  **mainメソッドのないクラスは、他クラスから呼び出して使う**
-   **クラス名に関係なく、実行時には、mainメソッドが呼ばれる**
    - Mainクラスから、mainメソッドが呼ばれる、というわけではない   

```
[Main.java]
class Main {
  public static void main(String[] args)
  Person.hello();
}

[Person.java]
class Person{
  public static void hello() {
    System.out.println("Hello World");
  }
}
```


## 外部ライブラリ
- javaでは他人が作ったクラスを利用できる。このようなクラスを **外部ライブラリ** と呼ぶ
- 外部ライブラリの読み込み 
  - `import java.lang.Math`
- `java.lang.~~`となるライブラリは、importせずとも利用可能。

```
[Main.java]
import java.lang.Math

class Main{
  public static void main(String[] args){
    int max = Math.max(3,8);
    System.out.println(max);
  }
}
```

# オブジェクト指向
- **情報**と **ふるまい** をもつ
  - 情報：**インスタンスフィールド**
  - ふるまい：**インスタンスメソッド**
- クラスとインスタンス。インスタンスはオブジェクトの別名。クラスはインスタンスの設計図
- クラスからインスタンスを生成するには `new クラス名()`
- インスタンスは変数に代入して利用する。
- 変数への代入は、`クラス型 変数名 = new クラス名();`とする
- クラス名がそのまま**クラス型**になる

```
[Main.java]
class Main{
  public static void main(String[] args){
    Person person = new Person();
  }
}

[Person.java]
class Person{

}
```

## インスタンスメソッド
- インスタンスフィールドの定義 `public 戻り値の型 メソッド名()`
  - ※staticがない
- インスタンスメソッドはクラスで定義されているが、あくまで**各インスタンスに属する**
- そのため、メソッドを呼び出すさいも、各インスタンスにたいして呼び出すようになる 

```
[Main.java]
Person person1 = new Person();
Person person2 = new Person();

person1.hello();
person2.hello();

[Person.java]
class Person{
  public void hello(){
    System.out.println("こんにちは");
  }
}
```

## インスタンスフィールド
- インスタンスフィールドは、情報を格納しておく変数
- その変数はクラスの一番上に定義する
- 変数定義の前に  **public** をつける `public データ型 変数名`

```
[Person.java]
class Person{
  public String name;
}

[Main.java]
Person person1 = new Person();
person1.name = "Suzuki";

System.out.println(person1.name);
```

### クラスのなかで、インスタンスを扱う
- インスタンスフィールドで定義した値を、メソッドで用いる
- メソッド内で、インスタンスフィールドにアクセスするめには  **this**  という特殊な変数を用いる
-  **this** はクラス内のメソッドの定義でのみ使用できる
-  thisはメソッドが呼ばれたさいに、そのメソッドを呼び出しているインスタンスに置き換えられる 

```
[Person.java]
class Person{
  public String name;
  public void hello(){
    System.out.println(this.name);
  }
}

[Main.java]
Person person1 = new Person();
person.name = "Suzuki";
person.hello(); .// このときに、[this]がインスタンスに置き換えられている
```

## コンストラクタ
- new を使って、インスタンスの生成時に自動で実行されるメソッド
- コンストラクタ名は、**クラス名と同じにする。**
- **戻り値を書かない。voidも書かない**

```
[Main.java]
class クラス名 {
  クラス名(){
    // インスタンス生成時に行いたい処理
  }
}

[Main.java]
Person person = new Person();

[Person.java]
class Person{
  public String name;
  Person(){
    System.out.println("インスタンスが生成されました"):
  }
}
```

- インスタンス生成時に、コンストラクタを生成すれば、インスタンスフィールドの定義が簡単になる
- インスタンス生成時に、コンストラクタの中で、各フィールドに値を設定すれば簡単になる
- newインスタンスを生成時に、`new クラス名()` の()には引数を渡せる
- thisをコンストラクタでも用いることで、インスタンスを利用できる

```
[Main.java]
Person person = new Person("Suzuki");

System.out.println(person.name);

[Person.java]
class Person{
  public String name;
  Person (String name){
    this.name = name;
  }
}
```

### インスタンスメソッドを定義する
- インスタンスメソッドは、**this** を使用し、自分のインスタンスフィールドを取得できるから、メソッドの引数に値を渡す必要なし
- また他のメソッドを参照するさいにも、インスタンスを指す **this** を指定すれば、 他のインスタンスメソッドを参照できる

```
[比較例]
class Person { 
  public static String fullName(String firstName, ){
    return firstName+ ;
  }
}

class Person{
  public String firstName;

  public String fullName(){
    return this.firstname+ ;
  }
}
```

```
[比較例]
public static void printData(..., double height, double weight){
  double bmi = bmi(height,weight);
}

public static double bmi(double height, double weight){
  return weight / height / height;
}

public void printData(){
  double bmi = this.bmi()
}

public double bmi(){
  return this.weight /this.height / this.height;
}
```
## クラスフィールド--static
- クラスに属するクラスフィールドも存在。インスタンスには属さない
- `public static データ型 変数名` で定義
- 例えば、**インスタンスの生成回数を数える場合に、クラスフィールドを用いる** → クラスに属する場合に
- クラスフィールドには、`クラス名.クラフフィールド名` でアクセス

```
[Person.java]

class Person {
  public static データ型 変数名;
}

class person {
  public static int count; //クラスフィールド
  public String firstName; //インスタンスフィールド
  public String lastName; //インスタンスフィールド
}

class Person {
  public static int count = 0; //初期値を入れて追くことができる
}
```

```
[Main.java]
class Main{
  public static void main(String[] args){
    System.out.println(Person.count); //クラスフィールドを呼び出している
    Person person1 = new Person();
    System.out.println(Person.count); //クラスフィールドを呼び出している
  }
}

[Person.java]
class Person{
  public static int count = 0;

  Person(String firstName){
    Person.count ++; //インスタンス生成のたびに、countに1が追加されていく
  }
}
```
## クラスメソッド--static
- クラスに属するメソッドのこと
- クラスメソッドには **static** をつける
- `public static 戻り値の型 メソッド名()`
- **クラス名.メソッド名** で呼び出す。クラスメソッドが、クラスに属しているため
- **static** がついているメソッドは、すべてクラスメソッド

```
[Person.java]
class Person{
  public static 戻り値の型 メソッド名(){

  }
}

[Main.java]
class Main{
  public static void main(String[] args){
    Person.printCount(); // 0
    Person.person1 = new Person();
    Person.printCount(); // 1
  }
}

[Person.java]
class Person{
  public static int count = 0;

  public static void printCount(){
    System.out.println(Person.count);
  }
}
```

## コンストラクタのオーバーロード
- オーバーロード
  - 引数の型や数が違えば、同名のメソッドを定義できる仕組み

- 例. ミドルネームをもつ人、もたいない人で、2つのコンストラクタ（引数の数が違う）を定義すれば、渡された引数の数に合わせて、適切なコンストラクタを自動で呼び出す

```
[Main.java]
class Main{
  public static void main(String[] args){
    Person person1 = new Person(); // 引数5個
    Person person2 = new Person(); // 引数6個
  }
}

[Person.java]
class Person{
  public String middleName;

  Person(String firstName, String lastName,..){
    // 引数5個
  }

  Person(String firtsName, String middleName, String lastName){
    // 引数6個
  }
}
```

### 他のコンストラクタを呼び出す
- `this()`とすると、コンストラクタから他のコンストラクタを呼び出せる
- `this()`は特別なメソッド。()に引数を渡すことも可能
- コンストラクタをオーバーロードするときに使用
```
[Person.java]
class Person {
  Person(String firsname, ---, double weight){
    Person.count++;
    this.firstName = firstName;
    this.weight = weight;
  }
}

  Person(String firstname, String middleName, ---, double weight){
    this(firstName, lastName, ---, weight)
    this.middleName = middleName;
}
```

### null なにもない
- 値がセットされていないmiddleNameフィールドには、`null` が入っている。文字列ではない。
- 変数の定義時に値を代入しなかったときの初期値

|データ型  | 既定値 |
|:------------ |:------------|
|String  | null |
|int  | 0 |
|double  |0.0  |
|boolean  |false  |

- nullを用いた切り替え

```
[Person.java]
class Person{

  public String fullName(){
    if(this.middleName == null){
      return this.firstName + "" + this.lastName;
    } else {
      return this.firstName + this.middleName + this.lastName;
    }
  }
}
```
## カプセル化― public private
- カプセル化の定石
  - フィールドはprivate
  - メソッドはpublicに
- フィールドとメソッドへのアクセスを制限すること
- クラスの場合には使ってほしくない機能を隠すこと
- クラスの外部からアクセスできるもの  → **public** 
- アクセス出来ないようにすること → **private** 
- ただし、クラス内からは、アクセスできる


```
[Main.java]
class Main{
  public static void main(String[] args){
    Person person = new Person("Suzuki", 24);
    System.out.println(person.name); // Suzuki
    System.out.println(person.age);  // エラー発生
  }
}

[Person.java]
class Person{
  public String name;
  private int age;
  Person(String name, int age){
    this.name = name;
    this.age = age;
  }
}
```


```
[Person.java]
class Person{
  private String middleName;

  public String fullName(){
    if (this.middleName == null){ // アクセスできる

    }
  }
}
```

## ゲッター
- フィールドをprivateにした上で、クラス外から安全にフィールドの値を取得するために、フィールドの値だけ返すメソッド
- `get フィールド名`

```
[Main.java]
class Main{
  public static void main(String[] args){
    Person person = new Person("John", "AAA", "bbb",){
      System.out.println(person.getMiddleName()); // ゲッターを使っているのでアクセスできる
    }
  }
}

[Person.java]
class Person{
  private String middleName;

  public String getMiddleName(){ // publicをつけているので、クラス外からアクセス可能
    return this.middleName; // フィールドの値を返す
  }
}
```

## セッター
- privateにしたフィールドの値を変更するメソッドのこと
- `setフィールド名` のように命名する
- フィールドのアクセス権を、privateにすると、フィールドの値をクラスの外からは変更できない

```
[Main.java]
class Main{
  public static void main(Strin[] args){
    Person person = new Person("AAA", "bbb", );
    person.setMiddleName("CCC");
    System.out.println(person.getMiddleName());
  }
}

[Person.java]
class Person{
  private String middleName;

  public void setMiddleName(String middleName){ // 返り値がないから「void
    this.middleName = middleName;
  }
}
```

# 継承--extends
- 共通する機能をまとめる
- **継承**
  - 既存クラスのフィールドやメソッドを別のクラスに引き継ぐ機能のこと
- **スーパークラス**
  - 継承されるクラスのこと
- **サブクラス**
  - 継承されてできる新しいクラスのこと
- 継承には `extends`を使う


```
[スーパークラス]
class スーパークラス {

}

[サブクラス]
class サブクラス *extends* スーパークラス { // スーパークラスを継承

}

```

## スーパークラスのメソッドを呼び出す
- サブクラスのインスタンスに対して、スーパークラスのインスタンスメソッドを呼び出すことが可能

```
[Vehicle.java]
class Vehicle {
  public void setName(String name){

  }

  public void setColor(String color){
  }
}

[Car.java]
class Car extends Vehicle { 

}

[Main.java]
class Main {
  public static void main(String[] argas){
    Car car = new Car();
    car.setName("ferrari"); // スーパークラスから、インスタンスメソッドを呼び出す
    car.setColor("green");
  }
}
```

### サブクラスのフィールドとメソッド
- サブクラスでは、スーパークラスにはない独自のフィールドやメソッドを追加できる。
- 継承は一方的なので、スーパークラスがサブクラスのメソッドを見つけることはできない

### メソッドのオーバーライド
- オーバーライド
  - スーパークラスから継承したメソッドと同名のメソッドをサブクラスに定義することで、スーパークラスのメソッドの内容を上書きできる、こと
  - オーバーライドするさいには、カプセル化されていないか確認する。
  - スーパークラスでカプセル化されているフィールドは、外部クラスから直接アクセスできない。そのため、getterを利用する
  - サブクラスで、スーパークラスのメソッドを呼び出すときには、this.getter()を利用する → **this**

## スーパークラスのメソッドを呼ぶ
- **super**
- `super.メソッド名()`
  - 上記のようにすることで、サブクラスのインスタンスメソッドから、スーパークラスのインスタンスメソッドを呼び出すことが出来る

## サブクラスでのコンストラクタ
- サブクラスでコンストラクタを定義するときの決まり
- コンストラクタの先頭で、*スーパークラスのコンストラクタを呼び出す* こと
- スーパークラスのコンストラクタを呼び出すには、**super()** を利用

```
[Vehicle.java]
class Vehicle {
  Vehicle(){
  System.out.println("スーパークラスのコンストラクタ");
}

[Car.java]
class Car extends Vehicle {
  Car(){
    super(); // *必須* superClassのコンストラクタを呼び出す
    System.out.println("サブクラスのコンストラクタ");
}

[Main.java]
class Main {
  public static void main(String[] argas){
    Car car = new Car(); 
    // [コンソール] スーパークラスのコンストラクタ
    // [コンソール] サブクラスのコンストラクタ
  }
}

```

### スーパークラスに定義されたフィールドに、値をセットする
- スーパークラスとサブクラスの両方で、コンストラクタを定義する
- サブクラスのコンストラクタ内で、`super()`に引数を渡し、スーパークラスのコンストラクタを呼び出す

```
[Vehicle.java]
class Vehicle {
  private String name;
  private Stging color;

  Vehicle (String name, String color){
    this.name = name;
    this.color = color,
  }
}

[Car.java]
class Car extends Vehicle {
  Car(String name, String color){
    super(name, color); // スーパークラスクラスのコンストラクタにname, colorを渡す

  }
}
```

## protected
- `protected`
- クラス内と、サブクラスからのみアクセスするフィールドを作成できる

|アクセス権  |public  |protected |private  |
|:------------ |:------------|:------------|:------------|
|クラス内  | OK |OK  | OK |
|サブクラス内  |OK  | OK | NG |
|クラス、サブクラスの外  |OK  |NG  |NG  |


```
[Vehicle.java]
class Vehicle {
  protected int distance = 0;
}

[Car.java]
class Car extends Vehicle {
  public void run(int distance){
    this.distance += distance; // スーパークラスの、distanceにアクセスできるように。
    // スーパークラスが、`private` であったときには、エラーがでていた。アクセスできないので、
  }
}
```

## 詳細未定のメソッド -- abstract
- 処理が未定のメソッドを定義する方法
- メソッドの先頭に `abstaract` をつけることで、**抽象メソッド** を定義できる
  - 抽象メソッドには、中身の処理は書かない
  - 抽象メソッドは、**サブクラスがそのメソッドをオーバーライドしていないとエラーになる**
  - そのため、**サブクラスがそのメソッドをオーバーライドし、処理内容を定義することを強制できる**
- 抽象メソッドをひとつでも持つクラスは、**抽象クラス** と呼ばれる
- 抽象クラスは、クラス名の前に、`abstract` をつける 
- 抽象クラスは、**インスタンスを生成できない**
  - 抽象メソッドという未完成のメソッドを持つクラスからは、インスタンスを生成できないということ

```
[Vehicle.java]
abstract class Vehicle { 
  asbtract public void run(int distance); // 処理内容は書かない
}

[Car.java]
class Car extends Vehicle {
  public void run(int distance){
    this.distance += distance; //オーバーライドして、処理の内容を定義する
  }
}
```

## インスタンス型のフィールド
- インスタンスフィールドにクラス型の変数を定義することで、フィールドにインスタンスをもつことが可能
- ゲッターとセッターも同様に定義する。戻り値の型と、セッターの仮引数の型が、クラス型になる

```
[Person.java]
class Person {
  public static int count = 0;
  public String firsName;
  public string middleName;
  public string lastName;
}

[Vehicle.java]
abstract class Vehicle{
  public String name;
  public String color;
  private int distance = 0;
  private Person owner; // Person型のownerフィールドを追加


  public Person getOwner(){ // 戻り値がPerson型
  
  }

  public void setOwner(Person owner){ // Person型の引数を受け取る

  }
}
```
- Carクラスのインスタンスやbicycleクラスのインスタンスに対して、getOwner()メソッドを呼び出すと、戻り値は、ownerフィールドの値
- すなわち、*Personクラスのインスタンスとなっている*
- ex. Person → Vechicle → Car

```
[Main.java]
class main {
  public static void main(String[] args){
    Person person = new Person("Kate", "Jones", 22...);
    Car car = new Car("ferrari");

    car.setOwner(person);
    car.getowner().printData(); // Personクラスの、printDataメソッドを呼び出せる
  }
}

[Vehicle.java]
abstract class Vehicle {
  private Person owner;
  public Person getowner(){
    return this.owner; // Personクラスのインスタンス
  }
}
```

### メソッド
- 入り組んでいるようなメソッド
- 引数で、どちらの型のインスタンスも受け取る可能性があるので、オーバーロードが必要（下のコード）
  - buyメソッドのなかで、引数に受け取ったインスタンスのセッターを用いて、所有者を変更する

```
[Person.java]
class Person {
  public void buy(Car car){
    car.setOwner(this); // このthisは、*buyメソッドを呼び出しているPerson クラスのインスタンス* を指す
  }
  public void buy(Bicycle bicycle){
    bicycle.setOwner(this); // このthisは、*buyメソッドを呼び出しているPerson クラスのインスタンス* を指す

  }
}

[Vehicle.java]

abstract class Vehicle {
  public void setOwner(Person owner){
    this.owner = owner; // 上記のsetOwnerで、こちらが呼び出されている
  }
}



 

```

## 多態性
- 先程作成した、`buy` メソッドは、内容がほぼ同じ。
- buyメソッドは、引数として、Vehicle型の、インスタンスを受け取るようにすると、インスタンスを受け取れるようになる
- 引数に、スーパークラスの型にできる理由は、サブクラスは、サブクラスのインスタンスである前に、**スーパークラスのインスタンス** であるから。
- 上記のような関係にあるときに、サブクラスのインスタンスを、スーパークラスのクラス型変数に代入が可能になる
- 上記のような特徴を **多態性** という

**多態性の例**

```
Vehicle vehicle1 = new Car("ferrari", "red");
Vehicle vehicle2 = nwe Bicycle("bianki", "green");
```

```
[Person.java]
class Person {
  public void buy(Vehicle vehicle){ // Vehicle型の引数を受け取れるようにする。
    vehicle.setOwner(this);   
  }
  
}

[Main.java]
class Main {
  public static void main(String[] args){
    Person person1 = new Person("Kate", "Spade", ...);
    Car car = new Car("ferrari"); // 上記のPersonで定義されていた。buyを受け取れるようになる
    person1.buy(car);
    
    Person person2 = new Person("Lozario", "Sonic", ...);
    Bicycle bicycle = new Bicycle("bianki"); // 上記のPersonで定義されていた。buyを受け取れるようになる
    person2.buy(bicycle);

  }

}

```
# Java漫画 
Javaの目的
- Write once, run anywhere.

プログラムは、言語というよりは設計図に近い
それぞれの言語によって得意分野がある
windowsで使う実行ファイルは、拡張子が.exe ファイルはwindowsでしか動作しない


- Javaでプログラムを書いて実行するまでの流れ

1. 人間がテキストファイルとしてプログラムを書く。拡張子 .java
2. *コンパイル* 「Javaコンパイラ」が、テキストファイルをJava用のファイルに変換する 拡張子.class 
3. *中間ファイル* 人間には読めないJava用のファイルができる
4. 「Java仮想マシン」というアプリケーションが、Java用のファイルを読み取る。
5. プログラムとして動作

- JDK Java Development Kit
  - Javaコンパイラ：Java用のファイルにプログラムを変換する
  - Java仮想マシン：Java用のファイルを読み取り実行する


## 環境変数PATH
- 環境変数
  - ユーザーのデータフォルダの位置、OSのバージョンなど、情報を記載している
- 環境変数PATH
  - 環境変数にPATHというものが存在
  - PATHに登録したFolderにある実行ファイル（EXEファイル）は、コマンドプロンプトでファイル名を入力するだけで実行できる。
  - 上記の状態にあることを *「~~フォルダ名 にパスが通っている* という。

## PATHとURL
- URI
  - Uniform Resource Identifier :統一資源識別子
  - / スラッシュ でFolder階層を示す
  - URI形式 : file:///c:/document/hoge.txt
  - Webページを示すURLは、URIの特殊なもの。

# Eclipse
## JavaのProject
- JavaのProjectは、複数のプログラムファイルを1つにまとめたもの
- 多くの場合、作成したApplicationは、複数のプログラムファイルや、Resources（画像や音声などのプログラム以外のファイル）で構成されている
- Projectはそうした様々なファイルを1箇所にまとめたもの
- Projectは、Folderによる階層構造になっている。プログラムのソースコードは`src`Folderに作成する

- Projectの作成
  - Eclipseにて
  -  `[ファイル]→[新規]→[Project] `
  -  `[新規Project]→[JavaProject]→[次へ]→[Project名]を記入して完了`

## ソースコードを書く
- Eclipse上で以下の操作を行う
  - `Projectを展開→[src]で右クリック→`
  - `[新規]→[クラス]→[パッケージ]を[sampleに`
  - `→[名前]を[Hello]に→[新規Javaクラスダイアログを埋める]`
  - `→[public static void main(String[] args)]にチェック→[完了]`
- プログラムの実行
  - `メニューの[実行]→[実行構成]→実行構成ダイアログの[JavaApplication]で右クリック→[新規]→[名前]に好きな名前を入力`

- Javaではパッケージ名は名は **小文字で**。 クラス名は **大文字** で書き始める 

### 作成したアプリの出力の仕方
- Javaではプログラムの拡張子を **.java** のファイルに書く。Javaコンパイラを利用して拡張子`.class` の中間ファイルを作成する。
- JARファイルは、中間ファイルやResourcesをひとつにまとめて、実行可能にしたファイル。拡張子は`.jar`となる
- JARファイルは、zip形式の拡張ファイル。解凍すると、以下のようなFolderとFileが出力される
- `cui\sample\Cui.class`は中間ファイル
- `cui\META-INF\MANIFEST.MF` は  **マニフェストファイル** と呼ばれるもの。このファイルにはApplicationの各種情報が記入されている

```
== cui
- == META - INF
 - ~~ MANIFEST.MF
- == sample
  - ~~ Cui.class
```

- `Projectを右クリック→[エクスポート]を選択→[エクスポートダイアログ]で[Java][実行可能JARファイル]を選択→[次へ]ボタン`
- `[実行可能JARファイル・エクスポート]ダイアログで[起動構成]から[Cui-Cui]を選択→[参照]ボタンを押して[エクスポート先]に「デスクトップのパス-\cui.jarを入力→[完了]`
- デスクトプに[cui.jar]が出力される
- この拡張子  **.jar** のファイルがJavaの実行ファイルになる
- デスクトップで`[shift]+[右クリック]→[コマンドウィンドウを個々で開く]を選択`
- `java -jar cui.jar`と入力して、[Enter]

### Projectの作成
1. Eclipseのメニュー[ファイル] から[Javaプロジェクト]を選択
2. [新規Javaプロジェクト]ダイアログを開く 
3. プロジェクト名に[Cui] と入力。
4. 完了

### CUIクラスの作成
1. Eclpseプロジェクトの中の[src]Folderを右クリック
2. メニューから[新規][クラス]
3. [新規Javaプロジェクトダイアログ]
  1. [パッケージ名]を[sample]に
  2. [public static void main(String[] args)にチェック
  3. 完了
4. 作成された[sample\Cui.java]にソースコードをk丹生

### 実行構成を作成
1. 「Eclipse」のメニューの［実行］から［実行構成］を選択。
2. 「実行構成」ダイアログが開く。 
  1. ［Javaアプリケーション］を右クリックして、メニューから［新規］を選ぶ。
  2. ［プロジェクト］の［参照］ボタンを押し、「Cui」プロジェクトを選ぶ。
  3. ［名前］に「Cui」と入力する。 . ［実行］ボタンを押す。
- 起動構成は  **Cui-Cui** を選ぶ。忘れやいので注意する

### JARファイルを出力
1. 「Eclipse」のプロジェクトを右クリックして［エクスポート］を選択。
2. 「エクスポート」ダイアログが開く。
  1. 左側のリストから、［Java］［実行可能JARファイル］を選択。
  2. ［次へ］ボタンを押す。
3. 「実行可能JARファイル・エクスポート」ダイアログが開く。
  1. ［起動構成］で、対象となる実行構成を選ぶ。
  2. ［エクスポート先］の［参照ボタン］を押して「デスクトップ」を選ぶ。そして、ファイル名を「ファイル名.jar」と入力する。
  3. ［完了］ボタンを押す。
4. デスクトップに「ファイル名.jar」が作成される。

### 出力したJARファイルをCUIアプリとして実行
1. コマンド ウィンドウを開く。
  1. 「cui.jar」を出力した場所（デスクトップ）で［Shift］＋［右クリック］でメニューを表示。
  2. ［コマンド ウィンドウをここで開く］を選択。
2. 出力したJARファイルを実行する。
  1. 「java -jar cui.jar」と入力して［Enter］キーを押す。
  2. 「Please input your name」と出るので、「yuu」と入力して［Enter］キーを押す。
  3. 「Hello yuu!」と表示される。

#### memo文字コード
- 英数字は1byte = 256(0~255)で表現される
- 日本語（全角文字）は、2byte(256 * 256 = 0~65535)以上の数字で表される

### GUIApplicationの作成
```
package sample;

import java.awt.event.*;
import javax.swing.*; 

public class Gui extends JFramse {
	// window本体
	public Gui() {
		setDefaultCloseOperatioin(JFrame.EXIT_ON_CLOSE); //windowのとじ方
		setBoundes(100, 100, 640, 480); //位置とサイズ
		
		JButton btn1 = new JButton("ボタン１"); //ボタン作成
	  add(btn1); //ボタン追加	

    btn1.addActionListener(
      new ActionListener() { //クリック時の処理
      @Override
      public void actionPerformed(ActionEvent e) {
        System.out.println("クリック");
      }
    }
    );
	}

	public static void main(String[] args) {
    Gui frm = new Gui(); //window作成
    frm.setVisible(true); //表示
	}

}
```

###  ワークスペースの作成
- 増加するプロジェクトを区切る役割
- メニュー→ファイル→ワークスペースの切り替え→その他
- ワークスペースランチャーダイアログで、「参照」ボタンを押してFolderを選択→OK
  - 新規に作成したいばいいには、入力欄に新しいパスを自分で記入
- ワークスペースの切り替え
  - メニュー「ファイル」→「ワークスペースの切り替え」


#### プロジェクトの読み込み
1. 「Eclipse」の［パッケージ・エクスプローラー］で右クリック。
2. メニューから［インポート］を選択。
3. 「インポート」ダイアログを開く。
  1. ［一般］を開き、［既存プロジェクトをワークスペースへ］を選択。
  2. ［次へ］ボタンを押す。
4. 「プロジェクトのインポート」ページに遷移する。
  1. ［ルート・ディレクトリーの選択］の［参照］ボタンを押し、読み込みたいプロジェクトのフォルダを選択。
  2. ［プロジェクト］に読み込まれるフォルダが表示されるので、チェックが入っていない場合はチェックを入れる。
  3. プロジェクトをワークスペースのフォルダ内にコピーしたい場合は「プロジェクトをワークスペースにコピー」にチェックを入れる。
  4. ［完了］ボタンを押す。

#### ライブラリの読み込み方
1. 「Eclipse」の［パッケージ・エクスプローラー］で、ライブラリを利用したいプロジェクトを右クリックする。
2. メニューの［ビルド・パス］－［ビルド・パスの構成］を選ぶ。
3. 「～のプロパティ」ダイアログ（～にはプロジェクト名が入る）の、「Javaのビルド・パス」ページが表示される。
  1. ［ライブラリ］タブを選び、［外部JARの追加］ボタンを押す。
  2. ライブラリとして配布されているJARファイルを選択する。
  3. ［OK］ボタンを押す。

#### Javaでよく利用されるライブラリ  
- Apache Commons
  - http://commons.apache.org/

- Apache Commons Lang（java.langパッケージを拡張するライブラリ）
  - http://commons.apache.org/lang/

- Apache Commons Math（数学と統計学のライブラリ）
  - http://commons.apache.org/math/

- Apache Commons IO（java.ioパッケージを拡張するライブラリ）
  - http://commons.apache.org/io/

## Javaプログラムの処理の流れ
- 左から右に、上から下に処理が進む
- プログラムの処理はセミコロン; で区切る

## コメントアウト
```
// 単数行
/* */ 複数行
```

## エラー
- エラーが発生した場合には、Eclipseのエラーの詳細が確認できる。マウスを重ねる。またそのときに [F2] を押すと、内容がコピペできる
- Javaのエラーは2行目がエラーが起きた場所。3行目は、エラーを呼び出した場所
## 2進数
- PCは0-1の2進数で動いている
- メモリはまさにこの凸凹スイッチオンオフのかたまり
- 上の凸凹のかたまりをイメージしているとJavaは理解しやすいみたい

- CPU
  - Central Processing Unit 中央演算装置
  - メモリの装置に読み込まれたデータを計算する
- メモリ
  - コンピュータが計算などを行う際に、一時的に情報を記録する場所
  - ハードディスクと同様に情報を格納する場所だが、ハードディスクよりも高速
  - プログラムの基本的な動作は、このメモリ上の情報をCPUで計算して、再びメモリに書き込むというもの 
## 16進数
- 16進数の表し方 0-F
- A: 10, B: 11, C: 12, D:13. E: 14. F:15
- 2進数10進数は桁が頻繁に上がるので、確認しずらい

|2  |10  |16  |
|:------------ |:------------|:------------|
| 1001 |9  | 9 |
| 1100011 | 99 |63  |
| 1111100111 | 999 | 3E7 |
|  1111   |          | F           |
|1111 1111     |          | FF           |
|1111 1111 1111     |          |FFF           |

- 2進数と16進数は相性が良い
- 2進数の一桁分は、スイッチのオンオフ
- 16進数の一桁分は、スイッチのオンオフ4つで表現できる
- 8進数よりも16進数が採用されているのは、8（3bitで桁が上がる）よりも16（4bitで桁が上がる）ほうがコンピュータには使いやすいから
- コンピュータの世界では「byte」という単位がよく出てきます。
- プログラムを書く場合、byteは8bit（2進数で8桁の値、2の8乗＝256）になります。
- 1byteで表現可能な数値を10進数で表すと「0～255」になります。
- 1byteで表現可能な数値を2進数で表すと「0～11111111」になります。
- 1byteで表現可能な数値を16進数で表すと「0～FF」になります。
- 通常、1byteは2桁の16進数で表現されます（例：3F、FF）。

## 変数
- 代入する前に、型を指定することで、プログラムの入れ間違いを防げる
- プログラムの実行前にミスがわかる  
- 変数の初期化は最初にまとめてやってもよい

```
int result,
int price, discount
float f = 1.23f;
double d = 123.0;
```

|変数の型 | 扱える数字の範囲（個数） |（個数を 16進数で表現 |
|:------------ |:------------|:------------|
|byte  |-128-127  |8bit(1byte)  |
|short  |-32768-32767  |16bit(2byte)  |
|int  |-2147483648 - 2147483647(4294967296)  |32bit(4byte)  |
|long  |923372036854775808-92233720636854775807|64bit(8byte)  |
|float |+- 3.4028235E38 ~ +-1.4#-45 |32bit | 
|double|+- 1.7976931348623157E308 ~ +-4.9E-324 |64bit |
|boolean|ture or false| | 

- Eは10の何乗かを表す。E38 -> 10の38乗、E-45 -> 10の-45乗
- 1.23E3 = 1.23*10 **3 -> 1230 
- 1.23E-2 1.23*10 **-2 -> 0.0123
- 数字が溢れた場合には、１周する
  - 例えば、2147483647に1を足すと、-2147483648になる
- プログラムでは、0と1で値を表すため、少数は表現できない
  - そこで、少数を特殊な方法で近似して表現している。この数を「浮動小数点数」と呼ぶ
- この差があるために、大小は比較できるが、２つの値が同じかどうかは確認できない

### キャスト
- 型を変更する

```
short s = 1000;
byte b = s ; // エラー

byte b = 100;
short s = b; //問題なし  小さな型の値を大きな型の値に代入しているから

short s = 1000;
byte b = (byte)s; //エラーにならない
```

- ただし表現できない桁の情報は失われる
- 10進数の1000
  - 2進数（short 16bit）では0000 0011 1110 1000
  - byteは8bitなので、末尾８bitだけコピーする→ XXXX XXXX 1110 1000
  - 1110 1000はbyteでは「-24」

- 小数点→整数のキャストでは小数点以下が切り捨てられる

```
float i = 3.1415f;
int i = (int)f; //変数iには3が入る
```

### 演算子
- ++ -> デクリメント変数の値を1増やす
- -- -> インクリメント変数の値を1減らす
- a++  
  - 計算に利用したあと、変数aの値を1ｈやす  
- a--
  - 計算に利用したあと、変数aの値を1減らす
- ++a
  - 変数aの値を1増やしたあと、に計算に利用
- --a
  - 変数aの値を1減らしたあとに、計算に利用

```
int a = 2;
int b = 3;
int c = a++ * ++b;
// a 計算に使ったあとに変数aを1増やすので、計算の時点では2のまま
// B ます変数Bを1増やす。なので、変数Bは計算の時点で4
```
優先順位	演算子	意味

[配列添字]
```
.
x++　x--	メソッドの引数
配列の添字
オブジェクトの階層の区切り
算術演算子
++x　--x
+x　-x
~
!	算術演算子
単項演算子（正負の符号）
ビット演算子
論理演算子
new 型 x
(型)	オブジェクト生成
キャスト
*　/　%	算術演算子
+　-	算術演算子
<<　>>　>>>	シフト演算子
<　>　<=　>=
instanceof	比較演算子
==　!=	比較演算子
&	ビット演算子かつ論理演算子
^	ビット演算子かつ論理演算子
|	ビット演算子かつ論理演算子
&&	論理演算子
||	論理演算子
? :	条件演算子
代入演算子
=　+=　-=
*=　/=　%=
&=　|=　^=
<<=　>>=　>>>=	
```

### 比較演算子
- &
  - and
  - aもbもtrueならtrue, 違うならfalse
- |
  - or 
  - aかbのいずれかがtrue
- ^
  - XOR
  - aかbの一方のみがtrueならtrue。違うならfalse
- !
  - NOT
  - aがfalseならtrue、trueならfalse

#### ショートサーキット演算子  
- &&
  - aもbもtrueならtrue。違うならfalse。
  - ただし、aがfalseなら、bは評価しない。aがfalseなら、false
- || 
  - aかbがtrueならtrue。違うならfalse
  - ただし、aがtrueなら、bは評価しない  aがtrueなら、true

## ifの条件分岐
- {} 内の処理が1行のときには、{}を省略できる

```
if () discount = 0.2

if (price >= 1000){
    discout = 0.2;
  } else {
    discount = 0.1;
  }

if (price >= 1000) discount = 0.2;
else discount = 0.1;
```

### 条件演算子
- if文が条件に応じて処理を変えるように、条件に応じて取得する値を変える演算子のこと
- `?:` で表す 
- `条件? trueの場合の値 : falseの場合の値`

```
int price = 1000;
double discount = price >= 1000 ? 0.2 : 0.1 ;
```

## Switch
- 条件に **一致した** 処理を行う

```
int i = 1;
switch (i) {
  case 0:
    ~~;
  case 1:
    ==;
  case 2:
    ^^;
}
```

- switch文では値に対応したcaseやdefaultの場所に処理が飛ぶ
- そしてbreakの場所に来るか、switch文の末尾に来ると{}の処理をぬける
- なので、breakを書かないことで、複数の値の処理をまとめて書くことが出来る

```
int i -1;
switch (i) {
  case 0:
  case 1:
  case 2:
    System.out.println("This is 0, 1, 2");
  default:
    System.out.println("This is other");
}
```
### ループ処理とbreak
- ループ処理は `break` が来ると必ず終了する
- なので繰り返し処理と合わせて、実行することで特定の条件のときに処理を終了させられる

```
for (int i = 1; i <= 100; i++) {
  a += i;
  if ( a >= 100) {
    break;
  }
}
```
### continue 
- 処理を末尾にまで飛ばす、次の条件の処理を実行する

```
int a = 0;
for (int i = 1; i <= 100; i ++) {
  if (i%2 == 0) {
    continue; //処理を末尾にまで飛ばす
  }
  a += i; //奇数の場合だけ加算
  //偶数の場合には、ここまで処理が飛ぶ。すなわちａには加算されない。
}
```
## 文字列と配列
### 基本型と参照型
- 基本型
  - byte short int long float double boolean
  - byte-baseで考える
  - 変数と値が、一対一で対応している  
- 参照型
  - メモリのどこかに **オブジェクト** と呼ばれる本体がある。
  - 変数には「参照」というそこにアクセスするために鍵が保存される仕組みになっている
  - [変数] ← 格納 - [参照] (鍵のようにアクセスして) [オブジェクト本体]
  - 参照型の代表として文字列と配列がある
  - 参照型では変数に格納されるのは、この［参照］。オブジェクトは、直接変数に格納されることはない
- 基本型の変数
  - 値が格納される
  - [基本型の変数] ← [値]
- 参照型の変数
  - [参照型の変数] ← [参照]が格納される 
  - [参照]を鍵にして、別の場所にある[オブジェクト（本体）］にアクセス可能

### 複数の参照
- 本体が１つで、参照が複数というケースがある
- 注意するのは、１つの変数が、本体を書き換えた場合、本体を参照している他の変数にも変化が及んでしまうこと

```
[オブジェクト本体]
　└　参照→変数a
　└　参照→変数b
　└　参照→変数c

```

### null
- 変数に参照をいれたくない場合もある。そうしたときに、空であることを示す特殊な値を入れるそれが `null`
- nullの入っている場合には、オブジェクトの参照は入っていないために、参照を使って機能や値を利用するとエラーが起きる
  - 参照型の変数.機能() , 参照型の変数.値

```
if ( ojb != null) {
  System.out.println("オブジェクトあり);
} else {
  System.out.println("オブジェクトなし");
}
```

### char
- charは16bitで文字を表現している
- 一文字を表現する`基本型`
- char型で文字を扱う際には、値を''シングルクオーテーションで囲む

``` 
char x = 'a';
char x = 'あ';
//また所詮数字なので、文字コードを指定することでも文字を表せる
char x = 97; // 97は[a]
char y = 12386; //12396は[ｎ]

System.out.println((int)'a'); //97
System.out.println((int)'ぬ'); //12396
System.out.println((char)97); // a
System.out.println((char)0x0061); //ぬ
```
- Javaでは16bitUnicodeという文字コードを利用している

#### エスケープシーケンス
- 特殊な文字は、`\`バックスラッシュを先頭につけた表記する

```
char c1 = '\n'; //改行
char c2 = '\t'; //タブ文字
char c1 =  '\''; // ' シングルクオテーション
``` 

## 文字列――String
- 文字を複数ならべて扱う
- 文字は `シングルクオテーション` で囲む
- 文字列は `ダブルｋオテーション` で囲む  

```
// 文字
char c = '字';

//文字列(String)
String s = "文字列";
```
- String
  - 参照型なので、変数に入るのは文字列の参照
  - 実体であるオブジェクトは別の場所にある
  - 機能を追加できる

```
String s = "aaa";
int i = s.longth(); // i には3がはいる
```

- 基本型の変数では、比較演算子を使うが、 参照型では、`equals` を使用する

```
String s1 = "aaa";
String s2 = "nbb";

if (s1.equals(s2)) {
  // 同じ
} else {
  //違う
}
```

## 配列
- 文字列は複数の文字を1つの変数として利用できるもの
- 配列は  **複数の値を** 1つの変数として利用できるもの
- 配列の中身は、基本型でも参照型でも構わない
- ただし、1つの配列に **入れる値は同じ型** 
- どの型を入れるのかは、変数の初期化の段階で決める
- 配列の中身のことを `要素` という
- `[]` は配列を表す記号ととらえる。
- int[] : int型の配列を作るという意味になる
- `int[3]` : int .の値が3つ入る配列を作るという宣言。
- `new` : 参照型のデータを作るという意味
  - 文字列も参照型だが、よく使うから省略されている
  - `String s = new String("aaa");`

- array[0] 添字

```
int[] array =  new int[3]; // int の値が3つ入る要素を作るという意味

int [] array = {33, 66, 99};

//下の書き方はできない
int [] array;
array = {33, 66, 99};
// プログラムの途中で{} と書かれても、どの型かわからないから
//逆に言うと、明示的に型を示せば、あとでも初期化できる
int [] array;
array = new int[]{33,66, 99};
```

- 配列は作成した段階で、内部の要素に自動的に値が設定される

|型  |初期値  |
|:------------ |:------------|
|byte  |0  |
|short  |0  |
|int  |0  |
|long  |0L  |
|float  |0.0f  |
|double  |0.0(0.0d)  |
|char  |'\u0000'  |
|boolean  |false  |
|参照型  |null  |

### 基本型と参照型の配列
- 基本型 = {値, 値, 値};

- 参照型は参照しているので、下のような処理が可能となる
  - `as[0]` は文字列`aaa`  の参照
  - 文字列の参照なのでその機能であるlengthが使用できる
```
String [] as = {"aaa", "bbb", "ccc"};
int len = as[0].length(); // len = 2
```

## 配列の入れ子構造- 多次元配列
- 入れ子構造の配列のことを「多次元配列」と呼ぶ。入れ子になっていることを「ネスト」していると呼ぶ
  - 配列 = {参照, 参照, 参照};
  - 参照 = {値, 値, 値};

```
int[][] a2d = new int[4][3];
for (int y = 0; y < 3; y++) {
  for(int x = 0; c < 4; x++) {
    a2d[x][y] = (x+1) * 10 + (y+1); 
  }
}

int[][] a2d ={
  {101, 102,. 103},
  {201, 202, 203},
  {301, 302, 303}
}
```
### 配列の複製
- 以下の例は、参照を複製するだけ。a1,a2は同じ配列を参照しているだけ

```
int[] a1 = {33, 66, 99};
int[] a2 = a1;

// このときに以下の動作をすると、参照しているのが確かめられる
int[] a1 = {33, 66, 99};
int[] a2 = a1;
a2[1] = 44;
System.out.println(a2[1]); // 44
System.out.println(a1[1]); // 44
```
#### 基本型の配列の複製
- 複製する方法
```
int[] a1 = {33, 66, 99};
int[] a2 = new int[a1.lenght];
for (int i = 0; i < a1.length; i++) {
  a2[i] = a1[i];
}
```

```
int[] a1 = {33, 66, 99};
int[] a2 = new int[a1.length];
System.arraycopy(a1, 0, a2, 0, a1.length);
// System.arraycopy(複製元配列, 複製元配列の読み取り開始位置, 複製先配列，複製先配列の書き込み開始位置, 書き込む長さ);
```

```
int[] a1 = {33, 66, 99};
int[] a2 = a1.clone();
```


```
import java.util.Arrays; //これが事前に必要

public class Test {
  public static void main(String[] args) {
    int[] a1 = {33, 66, 99};
    int[] a2 = Arrays.copyOf(a1,. a1.lenght);
  }
}
```
#### 参照型の配列の複製
- 通常の方法で配列を複製した場合は、新たな配列は作成されるが、その中に入っている参照は、素の配列と同じオブジェクト（本体）を指している。
- こういったコピーのことを  **シャローコピー**
- 一方で、内部から参照しているオブジェクト（本体）をすべて複製して新たに配列に格納する方法を  **ディープコピー** と呼ぶ  

```
配列a1 {参照, 参照, 参照,参照};

配列 {0,1} , {2,3} ,{4,5}, {6,7};

配列a2 {参照, 参照, 参照,参照};
```

- 複製方法

```
int[][] a1 = {
  {0,1}, {2, 3}, {4,5}, {6,7};
};

int len1 = a1.length;
int[][] a2 = new int[len1][];

for (int i = 0; i < len1; i ++) {
  int len2 = a1[i].length;
  a2[i] = new int[len2];
  for (int j= 0; j<len2; j ++) {
      a2[i][j] = a1[i][j];
    }
  }
}
```

```
int[][] a1 = {
  {0,1}, {2, 3}, {4,5}, {6,7};
};
int[][] a2 = a1.clone();

for (int i = 0; i < a1.length; i++) {
  a2[i] = a1[i].clone();
}
```

### 配列のダンプ
- ダンプ
  - メモリー内の情報を書き出すこと

```
package sample;
import java.util.Arrays; //これが事前に必要
public class Test {
  public static void main(String[] args) {
    int[] a = {33, 66,99};
j    System.out.println(Arrays.toString(a)); // 33, 66, 99 配列の中身が出力される
    
  }
}
```
- 多次元配列のダンプ

```
package sample; 
import java.util.Arrays;

public class Test {
  public static void main(String[] args) {
    int[][] a = {{33, 66}, {22, 55}};
    System.out.println(Arrays.deepToString(a)); // [[33,66], [22, 55]]
  }
}
```

## オブジェクト指向
- Javaのオブジェクト指向では、外部に公開する必要がない値や命令は、外から操作されないように隠蔽されている
- Javaでのオブジェクトを継承して改造する
- クラス
  - オブジェクトの雛形に相当するもの
- フィールド
  - オブジェクトの状態を保持する値のこと
- メソッド
  - オブジェクト固有の機能のこと
- メンバ
  -  クラスに属するフィールドとメソッドなどのこと

### 修飾子
- public
  - 外向けの値や機能のこと
- private
  - 内向けの値や機能のこと7


- 以前作ったCuiクラスとの違いは、［public static void main(String[] args)］にチェックを入れているかどうかです。
- ここでは、mainを使わないクラスを作成するので、チェックを入れません。
1. Cui/src/sample」を右クリックしてメニューを表示して、［新規］［クラス］を選ぶ。
2. 名前を「MyClass」にして［完了］ボタンを押す。
3. 「MyClass.java」が作成される。

## オブジェクトの作成
- 参照型の変数の初期化と同様
  - このときの参照型は `クラス` となる
- `型 変数 = new クラス();`
- instance
  - クラスのフィールドを利用するためには、どこかにメモリを確保しないといけない。記憶領域としてメモリを確保する
  - コンピュータでは `new` とともにメモリ上にフィールドが確保される。これを  **インスタンス** という 

- Javaでは以上で確保されたインスタンスと、クラスのメソッドをひとまとめとして、 **オブジェクトとする**

- オブジェクト
  - [メモリ]インスタンス
    - public 変数
    - private 変数
  - クラス
    - public メソッド
    - private メソッド

```
[メモリ]
　- インスタンス
　- 変数1 変数2
[クラス]
　- メソッド1
　- メソッド2
```
## staticフィールド と staticメソッド
- クラスにはオブジェクトを作成するためのフィールドやメソッド以外に、そのままつかえるフィールドやメソッドがある → **オブジェクトをつくらなくとも使える**
  - ex. `System.arraycopy`
- どのようなフィールドやメソッドからもでクラスを利用できるわけではない
- `static`  という修飾子がついたフィールドとメソッドだけが可能
  - static:静的な
  - オブジェクトのようにdynamic（動的）に作る必要のない部品
- staticメソッドからは、staticなフィールドやメソッドしか利用できない
  - staticがついていない非staticなフィールドは、オブジェクトを初期化した際に初めてインスタンスとしてメモリが確保される
- staticメソッドはオブジェクトを初期化しなくてもつかえる。つまり、インスタンスとは無関係に動く
- だらか、インスタンスへのアクセスが禁止されている。
- そのため、非staticなフィールドが利用できないことを示している

-  **staticはstaticで完結する** 
- staticなフィールドはオブジェクトとは別途メモリ上に確保される

## メソッド
- メソッドの構造
  1. 入力――値や参照の型（複数）
  2. 内部処理―ブラックボックス
  3. 出力――値や参照の方（単一）

```
[メソッドの構造]
[戻り値の型] メソッド名 (引数の型 変数) {
  内部処理
  return 戻り値;
}

int plus (int n1, int n2) {
  int result = n1 + n2;
  return result;
}
```

### void、引数なし
- void
  - 戻り値がない

```
private int n = 0;
public void set(int newN) {
  n = newN;
}
```

### 処理途中のreturn
- メソッドの途中で return を用いれば処理を打ち切ることができる
- 戻り値が必要なメソッドでは、終了するタイミングで、必ず戻り値を戻す
  - 下の例では、`boolean` 型の戻り値が求められているのに、それが存在しないからエラーになっている

```
// 下のような場合にはエラーになる
public boolean checkEven(int chckN) {
  if (chckN % 2 == 0) {
    retun true;
  }
  // returnでの戻り値がないから、エラーになる
}
 ```

 ## ローカル変数
 - メソッド内で宣言された変数はローカル変数と呼ばれる
   - ローカル変数はメソッドが終了した時点で、破棄されて利用できなくなる。
   - 再びメソッドが呼び出されたさいには、新たに宣言された変数が作成される。
   - ローカル変数はほかのメソッドから呼び出すことはできない
 - クラスに所属するstaticフィールドは、Java仮想マシンが終了するまで保持される

 - オブジェクトに属する非staticフィールドの値や参照は、オブジェクトが消滅するまで保持される


## 参照型の引数
- 参照型の引数を変数に設定した場合、メソッドに渡るのは、値ではなく参照になる
- そのため、メソッド内で、参照の本体を書き換えると、メソッド呼び出し元の変数の本体も、同じものを参照しているので書き換わる

## メソッドのオーバーロード
- overload--荷物の積みすぎ、
- Javaのオーバーロードは、同じ名前のメソッドをいくつも作ることが出来る
-  **引数を変える** ことで、同じ名前のメソッドが複数作られる

```
public class MyClass {
  public static int myMethod(){
    return 0;
  }
  public static int myMethod(int i){
    return 1;
  }
  public static int myMethod(int i, int j ){
    return 2;
  }
  public static int myMethod(int i, int j, int k){
    return 3;
  }
}

// 引数がそれぞれの型のメソッドを用意しておける
public class MyClass {
  public static int plusOne(int i) {
    return i + 1;
  }
  public static double plusOne (double f){`
    reutnr f + 1.0;
  }
}
```
## 可変長引数
- 引数を1~複数個渡したい場合に、その可能性をすべて考慮するのは非常に骨が折れる
- なので、そのさいにも１つのメソッドを書くだけで済む方法が用意されている。
  -  **可変長引数**  
  - `型... 変数` と書く
  - **必ずメソッドの末尾に書く** 
- 可変長引数のメソッドと、通常の引数のメソッドが同じクラス内にあり、見かけ上の引数の形が同じ場合は、通常の引数のメソッドが優先的に呼び出される
- 可変長引数の実体は配列なので、引数に配列を設定しても動作する

```
public static int sum(String s, int... iArr) {
  int res = 0;
  for (int i = 0; i < iArr.length; i ++) {
    res += iArr[i];
  }
  return res;
}

System.out.println(MyClass.sum(new int[]{1,2}));
```

## コンストラクタ
- 構築子とも呼ばれる
- クラスからオブジェクトを作成するときに呼び出される特殊なメソッドのこと
- **コンストラクタはクラスと同じ名前のメソッド** 
- クラスと同じ名前の `public [クラス名]`
- コンストラクタは初期化されたオブジェクト必ず戻すので、 **戻り値は書かない** 
- **オーバーロード** の機能と組み合わせることで様々な初期化設定方法を定義できる
- コンストラクタがクラスにない場合は、 **引数なしのコンストラクタ** が内部で自動的に用意される
- 自分でコンストラクタを書いた場合は、引数なしのコンストラクタが  **自動で生成されない** 
- そのため引数なしのコンストラクタは自分で書く必要がある

```
public class MyClass {
  public String label = "aaa";

  //コンストラクタ
  public MyClass (String newLabel) {
    label = newLabel; //ラベルを設定
  }
}

public class Sample {
  public static void main (String[] args){
    MyClass mc = new MyClass("遊ぶ");
    System.out.println(mc.label); // 遊ぶ
  }
}
```

## mainメソッド
- Applicationが実行されるときに、最初に呼び出されるメソッドのこと
- 引数には文字列の配列 `String[] args` が指定されているが、Applicationが実行時にとる引数のこと
- 引数に入れられる文字列の例
  - Applicationのファイルパス（ドラックアンドドロップするファイルのパスを受け取るなども）
  - 配列なので、複数のファイルパスも受け取れる
  - この値を利用して、起動オプションの設定も

- Eclipseでのmainメソッドの引数の設定
  - eclipseのメニューで［実行］［実行構成］を選択。
  - 左のリストの「Javaアプリケーション」で設定したい実行構成を選択。
  - ［引数］タブを選択。
  - ［プログラムの引数］に値を入力。

## 例外
### throw throws
- Javaの例外は `Exception` から派生したクラスを使って発生させる
- `new Exception()` で新しい例外を発生させて、throwに送っている。
- Javaには予めファイル読み込み時の例外や、データ形式誤り時の例外など、が用意されている

```
throw new Exception() // 例外を投げるという意味
```

- 例外の受け取り方
  1. メソッド全体で受け取る方法
  2. try catch で例外を受け取り処理する方法

#### メソッド全体で受け取る方法
- 例外が発生したら、メソッド全体で受け取る方法。
- 例外が発生したらメソッドの処理を中止して、メソッドの呼び出し元に例外処理を投げる
- 例外を受け取った呼び出し元では、例外に対して処理を続ける必要がある。
- このときに、呼び出し元にも、`throws` があれば、さらに例外処理を呼び出し元に丸投げできる
- 例外をメソッド全体で受ける場合は、引数の後に `throws` と書いてその後に例外を並べる

```
void method() throws ExceptionA, ExceptionB {
  処理1
  throw new ExceptionA();
  処理2
  throw new ExceptionB();
}
```

#### try catch
- 発生した例外を処理する方法はthrowsを使って呼び出し元のメソッドに処理を投げる方法
- try catch で例外を受け取り処理する方法
- Javaでは例外の最終的な処理を `try catch` で行う 
- 例外の起きる可能性のある場所を `try{処理}` で囲い、例外が起きたときの処理を `catch(例外の型 変数) {処理} ` で受け取る
- catch文は例外クラスの種類ごとに書く


```
try {
  例外がthrowされる可能性のある処理
  // throw new () があるかthrows ~ のついたメソッドがある
} catch (例外の型 変数) {
  例外が起きたときの処理
}
```

```
try {
  method(); //thorws ExceptionA, ExceptionB
} catch (ExceptionA eA) {
  // 例外Aが起きたときの処理
} catch (ExceptionB eB) {
  // 例外Bが起きたときの処理
} finaly {
  // 例外が起きた場合も、起きなかった場合も最終的に個々を通る
}
```

```
package sample:
public class Sample {
  putlic static void main(String[] args) {
    try {
      MethodA();
    } catch (Exception e) {
      e.printStackTrace();
    }
    public static void MethocA() throws Exception {
      throw new Exception();
    }
  }
}
```

## 再帰
- メソッドを利用した繰り返し計算の処理方法
- メソッドから自分自身を呼び出す処理
- for文を使わずに、メソッドを利用する理由は、ローカル変数がつかえること
- ローカル変数の値は、呼び出されたメソッドごとに、独立しているため、 **各処理頃に別の値を保持した場合** に便利

```
package sample;

public class Sample {
  public static void main(String[] args) {
    up(0);
  }
  public static int up(int i) {
    if (i < 3) {
      System.out.println(i);
      up(i + 1);
    }
    return i;
  }
}
```

## クラスオブジェクト
- パッケージによるクラスの整理
- Javaのたくさんのクラスを階層構造で整理する仕組み
- 例・java lang Stringのソースコードは `java/lang/String.java` となる
  - java.lang――パッケージ名 ,String――クラス名
  - 階層構造の区切りにはピリオドをうつ
  - String.javaファイルの冒頭には自分が即するパッケージを `package java.lang; `  と書く
- クラスを作成する際に、パッケージ名を ` sample` クラス名を`Smaple` としていた
- これは、`sample/Sample.java` というファイルを作成していた
- ファイルの冒頭には、`package sample;` という一文が自動的に書かれていた

` package sample;`

- 自分で作成したクラスは、他人と被らないように、する。自作クラスのパッケージ命名方法
  1. example.comというドメインをもっている
  2. ひっくり返して。com.example とする
  3. 分類する内容が、util(Utilityの略)ならば末尾につける
  4. com.example.util

- 実際にクラスを利用するには、`java.io.File f = new java.io.File("/");` と書く
- 実際は上記のように長く書かないで良い。そのための3つのルール
  1. 自分のクラスと同じパッケージのクラスは、パッケージ名を省略できる
  2. java.langのクラスは、Javaの基本的なクラスなので、パッケージ名を省略できる
  3. クラスの最初に、`import` 文を書く `import java.io.File` 


```
package sample;

import java.io.Console;
import java.io.File;

public class  Test {`
  public static void main(String[] args) {
    File f = new File("./");
    Console cons = System.console(.);
  }
}
```


### スーパークラスとサブクラス
- 親子関係
- サブクラスでは、スーパークラスの値や機能がつかえる

```
package sample;
public class SubClass extends SuperClass {

}
```

### super this
- superはスーパークラスのフィールドやメソッドにアクセスするための予約語
- this は自分のクラスやフィールドにアクセスするための予約語
- このthisは省略することできる

```
public class SuperClass {
  public String label = "Super";
  public String getLabel() {
    return label;
  }
}

pakcage sample;
public class SubClass extends SuperClass {
  public String label = "Sub";
  public String getLabel2() {
    return label;
  }
  public String getSuperLabel() {
    return super.label;
  }
  public String getThisLabel() {
    return this.label;
  }
}
```

## メソッドのオーバーライド
- スーパークラスのメソッドを無視して、サブクラスのメソッドを優先させるというものｊ
- メソッドの場合には、明示的に `@override` とアノテーション注釈をつけることになっている


- オーバーロード
  - 引数を変えて同じ名前のメソッドを複数つくるもの
- オーバーライド
  - 命令を無視する、決定を覆す、優先する

```
@override
public String getLabel() {
  String s = super.getLabel();
  s += label;
  return s;
}

```

- 参照元のコンストラクタを呼び出すときには `super()` 
- コンストラクタの  **最初の行** に書く

```
[継承元のコンストラクタを呼び出すとき]
public SubClass() {
  super();
}
```

## オブジェクトのキャスト
- オブジェクトも別の型に変換できる
- サブクラスとスーパークラス間のキャストは可能
  - サブクラスのなかにはスーパークラスの値や機能がまるごと入っている。そのため、スーパークラスとして扱っても、問題なし
  - サブクラスから、スーパークラスはそのまま代入できる
  - `(SuperClass)SubClass` と書かなくとも、自動的にキャストされる
- フィールドは **スーパークラスのもの** 、メソッドはオーバーライドされていれば、**サブクラスのもの** が使われる

```
SubClass subClass = new SubClass'();
SuperClass superClass = subClass;
```

- スーパークラスから、サブクラスへのキャスト
  - 実際にキャストできる中身ならばエラーにはならない
  - しかしキャストできない中身ならばエラーになる
- スーパークラスから、サブクラスにキャストするには、カッコとクラス名が必要
  - 下の場合には、superClassには、subClassのもっているフィールドとメソッドが足りていないためにエラーになる
```
[実行時にエラーになる java.lang.ClassCastException]
SuperClass superClass = new SuperClass();
SubClas subClass = (SubClass)superClass;
```

- キャストした中身がそのクラスのオブジェクトとして利用できる場合はエラーにならない
- 下の場合には、superClass のなかみは、SubClassだから、再度SubClassにキャストしてもエラーにならない
- 重要なのは、キャストしても変数の中身の情報が失われるわけではないということ

```[noerror.java]
[実行時にエラーにならない]
SubClass subClass1 = new SubClass();
SuperClass superClass = (SuperClass)subClass1;
SubClass subClass2 = (SubClass)superClass;
```

### オブジェクトのキャスト――メソッドの引数に対して
- スーパークラスを引数に取るメソッドでは、そのサブクラスも引数につかえる

```
public void method(SuperClass sc) {

}

SuperClass superClass = new SuperClass();
SubClass subClass = new SubClass();
method(superClass); // 問題なし
method(subClass); // 問題なし
```

### アクセス制御
- アクセスが可能か

|修飾子  |同一クラス  |同一パッケージ  |サブクラス  |その他  |
|:------------ |:------------|:------------|:------------|:------------|
|public  |○  | ○ | ○ | ○ |
|protected  | ○ |○  | ○ |×  |
|なし  | ○ |  ○|×  |×  |
|private  | ○ |×  |×  |×  |

- protected
  - 同一パッケージと、サブクラスからアクセス可能
- 修飾子なし
  - 同一パッケージからはアクセス可能
  - サブクラスからはアクセス不可能
- メソッドの可視性を下げることはできない
  - スーパークラスでpublic になっていたメソッドを、サブクラスでprivateにはできない
  - メソッドはフィールドと違い、オーバーライドされている
  - そしてスーパークラスのメソッドが無効化されている。
  - なので、可視性を下げるようにすると、サブクラスを、スーパークラスにした場合に問題がでる。
    - 可視性を下げてしまうと、スーパークラスのメソッドとは同じものとして扱えないから

### 定数
- 変数の中身を書き換えられない
- 変数の宣言のときには `final`という修飾子をつける
- Javaは定数は大文字で書く

```
filnal int I = 0;
filnal String S = "定数";

filnal String GREEN
filnal String BLUE
```

#### 参照型の定数の場合
- 定数は、値や参照が固定
  - 固定されているのは参照だけ。だから、参照先のオブジェクトのフィールドは自由に変更できる
  - 参照が書き換えできないだけで、その先のフィールドは定数ではないから書き換えられる。
  - あくまで変数に入っている値が固定なだけ

```
final int[] I_ARR = {0, 1, 2};
I_ARR[0] = 9;
System.out.println(I_ARR[0]); // 9と出力される
```

### 抽象クラス
- 一部のメソッドが実装されていない不完全なクラス
- **abstract** が抽象クラスの目印
  - クラスの宣言の頭に`abstract` をつけることで抽象クラスを作れる。
  - 抽象クラスには抽象メソッドが存在する。そのすべての抽象メソッドの中身を完成させると、そのクラスは使用可能になる
  - すべての抽象メソッドが実装されなかった場合は、さらにそのサブクラスで抽象メソッドを実装することになる
  - 抽象クラスを継承したクラスでは、抽象メソッドが実装された場合，abstract を取り除く。
  - またすべての抽象メソッドがなくなったら、クラスの `abstract`  を取り除く

```
[抽象クラス]
package sample;

abstract public class SuperClass {
  public int n = 1;
  abstract public int getN2();
  public int getN(){
    return n;
  }
}

[完成させたクラス]
package sample;

public class SubClass extends SuperClass {
  @Override
  public int getN2() {
    return n * 2; //
  }
}
```

## 多重継承とinterface
- Javaでは多重継承が禁止されている
- 擬似的にも多重継承を実現するのが  **interface** 
- interface
  - 定数と抽象メソッドだけで構成された特別なクラス 
- classではなく `interface` とかく
- interfaceのフィールドに可能な修飾子
  - public
  - static 
  - final
  - （修飾子なし）interfaceのフィールドは、finalを書かなくとも、勝手に定数になる
- interfaceのメソッドに可能な修飾子
  - public
  - abstruct
  - (修飾子なし）書かなくとも勝手に、publicになる

```
package sample;

public interface Interface1 {
  public final int N = 1;
  abstract public int getN1();
}
```

### interfaceの実装
- interfaceを継承する場合には、extends ではなく、`implements` を使う
- implentsは１つでかでなく、複数のinterfaceを継承できる
- interfaceを実装するクラスには、スーパークラスを別途設けることも可能

```
package sample;

public class SubClass implements Interface1, Interface2 {
  @Override 
  public int getN() {
    return N;
  }
  public int getN2(){
    return N * 2;
  }
}
```

#### リスナー
- interfaceの利用場面
  - イベントリスナーとして利用される
  - GUIにおいて、は `addXXListner` というメソッドが大抵ついている
  - このメソッドは、その部品に何かが起きたら呼びだされるinterfaceを登録するもの
- GUIの部品には、リスナーを登録するメソッドが用意されている。
- リスナーを登録しておくと、GUIの部品でなにかイベントが起きたときに、登録しておいたリスナーのメソッドが実行される
- このリスナーはinterfaceとして用意されているので、実際に使用する際には、このinterfaceを実装してから利用する
- またリスナーはinterfaceであるから、様々なクラスに、追加の処理として実装できる
- JFrameを継承したsampleクラスに、WindowStateListenerも実装している

```
package sampleclass;

import java.awt.event.WindowEvent;
import java.awt.event.WindowStateListner;

import javax.swing.JFrame;

public class SampleClass extends JFrame implementes WindowStateListner {
	private static final long serialVersionUID = 1L;

	public Sample() {
		// window
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100,100, 640, 480);
		
		this.addWindowStateListener(this);
	}
	
	
	public static void main(String[] args) {
		// TODO 自動生成されたメソッド・スタブ
		Sample smpl = new Sample();
		smpl.setVisible(true);
	}
	
	@Override
	public void windowStateChanged(WindowEvent e) {
		System.out.println(e);
	}

}

 ```

## Objectクラス
- すべてのクラスの祖先に当たる、オブジェクトクラス
- `extends` を書いていないクラスは、自動的に `java.lang.Object` を継承している
- 重要なメソッド
  - objectの比較――`equals`
  - objectの複製――`clone`

- equals
  - 参照型、つまりobjectの比較に使う命令
  - 

### Objectクラスの比較
- 下の比較では、「参照」を比較しているだけで、フィールドの値までは比較していない

```
[src/sample/MyClass.java]
package sample;

public class MyClass {
  public int n = 0;
}

[src/sample/Sample.java]
package sample;

public class Sample {
  public static void main(String[] args) {
    MyClass mc1 = new MyClass():
    MyClass mc2 = new MyClass():
    // 比較
    if (mc1.equals(mc2)){
      System.out.println("同じ");
    } else { 
      System.out.println("違う");
    }
  }
}


// 出力結果→「違う」
```

- そのため、メソッドをオーバーライドして、適切な比較処理を追加する
- `instanceof` は比較演算子。左辺のオブジェクトが、右辺のクラスとして使えるかどうか判定する
- 右辺が自身のクラスや、祖先のクラスやinterfaceなら、 `true` と判定される

```
@Override
public boolean equals(Object obj){
  if (obj instanceof MyClass ){
    MyClass mc = (MyClass)obj;
    return this.n == mc.n;
  }
  return false;
}
```

### clone
- オブジェクトの複製には、java.lang.Objectの `clone` メソッドを使うが、
- cloneメソッドを自作クラスで行う場合には、cloneメソッドをオーバーライドして `Cloneable` interfaceを実装する

- Objectのcloneメソッドは、オブジェクトの参照を保存しているインスタンを複製して、オブジェクトを複製してくれる。そのオブジェクトを自作クラスにキャストすれば、オブジェクトが複製される

```
package sample;

public class MyClass implements Cloneabe { 
  public int n = 0;
  // clone のオーバーライド
  @Override
  public MyClass clone() {
    MyClass res = nul;
    try {
      // クローン
      res = (MyClass)super.clone();
    } catch () {
      // 発生しないだろうと思われるエラー処理
      throw new InternalError(e.toString());
    }
  }
}
```
- 参照型フィールドの複製
  - シャローコピー
    - cloneはインスタンスを複製するが、参照型のフィールドでは、オブジェクトへの参照が複製されるだけ
  - ディープコピー
    - フィールドのオブジェクトも複製したい場合は、clone内でオブジェクトを複製する処理を時前でかく。
    - オブジェクトの内容も複製することをディープコピーとよぶ

```
package sample;
public class MyClass implements Cloneable {
  public int n = 0;
  public int[] iArr = {1, 2, 3};

  // cloneのオーバーライド
  @Override
  public MyClass clone() {
    MyClass res = null;

    try {
      // クローン
      res = (MyClass)super.clone();
    } catch (CloneNotSupportedException e) {
      // 発生ひないだろうと思われるエラー処理
      throw new InternalError(e.toString());
    }
    // ディープコピー
    res.iArr = iArr.clone();
    return res;
  }
}
```

### Classクラス
- `java.lang.Class` というものが存在する
- このClassからはクラスの名前やパッケージ名といった情報を取得できる
- 

```
Object obj = new Object();

System.out.println.out.println(obj.getClass().getName());
// java.lang.Objectと出力
System.out.println(obj.getClass().getSimpleName());
// Object
System.out.println(obj.getClass().getPackage().getName());
// java.lang
```

- クラスから直接情報を得ることも可能
- クラスの `public static final` フィールドのclassを使う
- `クラス名.class` と書くことでアクセス出来る

```
System.out.println.out.println(obj.class.getName());
// java.lang.Objectと出力
System.out.println(obj.class.getSimpleName());
// Object
System.out.println(obj.class.getPackage().getName());
// java.lang
`
```

### メソッド内のクラス
- クラスはファイルで一つずつ作るのが基本だが、それ以外にも作成できる特殊なクラスがある
- メソッドのなかでクラスを宣言し、そのメソッド内で使用する。
- 局所クラス（ローカルクラス）と呼ぶ
- 注意するのは、ローカル変数と同じで、メソッド内でしか使用できないこと

```
public void method() {
  class In{

  }

  In in new = In();
}
```
  

- 匿名クラス
  - 名前無しで作成してオブジェクトを生成するクラス
  - メソッド内でオブジェクトの作成をしつつ、その後に`{ }` を加えることで、そのクラスのサブクラスを一時的に作り、メソッドのオーバーライドなどを行う

```
public void method() {
  MyClass mc = new MyClass(){
    @Override
    public void method() {
      System.out.println("MethodAnonymous");
    }
  }
}
```

```
[interfaceの実装などで使われる]
JButton btn = new JButton();
btn.addActionListener(new ActionListener() {
  @Override
  public void actionPerformed(ActionEvent e){
    // クリック時の処理
  }
}
```

### ネストしたクラス
- クラスの中にstaticなクラスやstaticなinterfaceが入っている

```
package sample;

public class MyClass {
  // ネストしたクラス
  public static class NstCls {

  }
  // ネストしたinterface
  // interfaceは暗黙的にstaticとなる
  public interface NstIntr{
    public void method();
  }
}
```  
- ネストしたクラスを外部から利用するには、`外側のクラス.自身のクラス`

```
// ネストしたクラスを外部から作成
MyClass.NstClas nstCls = new MyClass.NstCls();
// ネストしたinterfaceを外部から実装
MyClass.NstIntr nstIntr = new MyClass.NstIntr() {
  @Override
  public void method() {

  }
}



[上の書き方が面倒なら下のように書ける]
import パッケージ名.クラス名.ネストしたクラス名
import sample.MyClass.NstCls;

// ネストしたクラスを外部から作成
NstCls nstCls = new NstCls();

```
### 内部クラス
- 内部クラスは、クラスの中にある **非static** なクラスのこと
- ネストしたクラスとの一番の違いは、外部クラスのインスタンスに紐付いていること
- こういった内部クラスを持つクラスのことを **エンクロージング型のクラス** と呼ぶ（エンクロージング：囲い込み）

```
package sample;
public class MyClass {
  private int n = 0;
  // [内部クラス（インナークラス）
  // 外部クラスのインスタンスに紐づく
  public class Innr {
    private int n = 9;
    public int getThisN() {
      return this.n; //自クラスの n
    }
    public int getMyClassN() {
      return MyClass.this.n; //外側のクラスのn
    }
  }

}
```

- 内部クラスのオブジェクトは、外部クラスのオブジェクトにぶら下がっている
- 内部クラスのオブジェクトから、外部クラスのインスタンスにアクセス可能になっている
- 外部クラスへのアクセスは `外部クラス名.this.フィールド名` とする

- `外部クラスのオブジェクト.new 内部クラスの型()` とすることで内部クラスのオブジェクトは作成される

```
package sample;

public class Sample {
  public static void main (String[] args) {
    MyClass mc = new MyClass();
    // 内部クラスを外部から作成
    MyClass.Innr pub = mc.new Innr();
    // 内部クラスから内部クラスの値を得る
    System.out.println(pub.getThisN()); // 9
    // 内部クラスから外部クラスの値を得る
    System.out.println(pub.getMyClassNo()); // 0
  }
}
```

- 内部クラスのオブジェクトを複数作る
  - その際には、それぞれの内部クラスのオブジェクトから外部クラスのオブジェクトにアクセス可能になる

### ラッパークラス
- 基本型の値を包み込む。int long float double

|基本型  |ラッパークラス  |
|:------------ |:------------|
|byte  |Byte  |
|short  |Short  |
|int  |Integer  |
|long  |Long  |
|float  |Float  |
|double  |Double  |
|char  |Character  |
|boolena  |Boolean  |

- 利用場面
  - オブジェクトを引数に取るメソッドがあったときに、値をラッパークラスで包むことで、引数に渡せる

```
int i = 0;
Integer i2 = new Integer(i);

void method(Object obj){ // こちらに代入できる

}
```

- またラッパークラスには便利なメソッドが含まれている
  - 文字列を数値にするメソッド ` int i = Integer.valueOf("99"); `
  - 上記において、Integerの戻り値は、intにキャストされている `int i = (int)Integer.valueOf("99");
-  ラッパークラスのオブジェクトは、そのまま基本型として使える。
  - その際には、対応した基本型に、暗黙的にキャストされる。→  **オートボクシング** 

```
Integer i1 = new Integer(10);
int i2 = 100 + i1; //i1は数値として処理される
System.out.println(i2);
```


- ラッパークラスの定数
  - ラッパークラスのフィールドには、各基本型を使ううえで、有用な定数が用意されている。
  - ex. Integer型では、最大値や最小値が用意されている

```
long n = 9999999991;
int i = 0;
if (n > Integer.MAX_VALUE) {
  // intの最大値2147483647 より大きい
  i = integer>MAX_VALUE
} else if ( n < Integer.MIN_VALUE) {
  // intの最小値-21474833648より小さい
  i = Integer.MIN_VALUE
} else {
  // intの値の範囲内
 i = (int)n; 
}
System.out.println(i); // 2147483647と出力
```

# ガベージコレクタ
- Javaのメモリ管理
- Javaでは値やオブジェクトを作るとメモリ上にデータが確保される
- そのまま確保し続けたら、メモリを食いつぶしてしまう。
- なので使い終わったメモリから解放する必要がある

- 基本型
  - 型に対応したメモリが確保されている
  - 3つの場合で、基本型の値は使用される
    - ローカル変数
      - メソッドが終われば破棄される→メモリは解放される
    - オブジェクトのインスタンス
      - フィールド→インスタンスが開放されるときに、一緒に開放される
    - クラスのstaticフィールド→仮想マシンが狩猟するまで保持されるので、メモリ管理の話からは除外
- オブジェクト
  - インスタンスがメモリ上に作成されている


- 要はインスタンスのメモリ管理が、Javaのメモリ管理
  - オブジェクトのインスタンスの解放は、Javaの仮想マシンが勝手に開放してくれる
  - メモリを監視して、変数から参照されていないインスタンスを定期的に探して開放する

- ガベージコレクタは、どこからも参照のないインスタンスを開放する。
- 参照の有るインスタンスは、開放しない      

### Javaの起動オプション
- 出力したjarファイルは様々な設定付きで実行できる
- Java仮想マシンのオプション


### java.lang.System
- in
  - コンソールからの入力に使われる
- out
  - コンソールへの出力に使われる
- err
  - コンソールへの出力に使われますが、エラーとして出力される

### java.lang.Runtime
- ラインタイムはプログラムの実行に必要な部品の集合
- `java.lang.Runtime` は、そうした情報を得たりすることが出来るクラス
- JavaのすべてのApplicationは、Runtimeクラスのインスタンスを１つだけ持つ。このインスタンスを取得することで、様々な操作を行える

```
Runtime r = Runtime.getRuntime(); // ランタイムクラスのインスタンスを取得
```
- メモリの状態を確認

```
// Java仮想マシンが使用を試みる災害メモリー容量を取得`
public long maxMemory();
// Java仮想マシンのメモリーの総容量を取得
public long totalMemory();
// Java仮想マシン内の空きメモリーの量を取得
public long freeMemory();
```

### mavenの説明
- https://reasonable-code.com/eclipse-maven/

```
グループIdとは、プロジェクトを一意に識別する名前で、プロジェクトのルートパッケージ名を指定します（例. org.apache.maven, org.apache.commons）。

アーティファクトIdとは、プロジェクトの成果物の名前で、jarやwarの名前を指定します（例. maven, commons-math）。
```
