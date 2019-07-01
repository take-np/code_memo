# Pythonのメモ

## 型変換
- 文字列型への変換 str
- 数値型への変換 int
```
  price = 100
  print ("りんごの価格は" + str(price) + "円です")
  //下はエラーになる
  print("りんごの価格は" + price + "円です")
```

## 条件式 比較演算子
- x == Y 等しいか
- x != y 等しくないか
- 条件式では、行末に **:** コロン
- 条件式が成立したときには、**インデント** の中の処理が実施される。インデントはそのままプログラムに影響するので、記述には気をつける
```
score = 100
if score == 100: // 行末のコロンを忘れない
  print ("ok")
```
### 場合分け else, elｌif
- else の行末にも コロン**:**


### 入力した値を受け取る
- input
- input_count = input('個数を入力してください')

```
input_count = input ('個数を入力してください')
# inputで受取った値は文字列型

count = int(input_count)
# 数値型に変換
```

## データ管理
- リスト
- [要素1, 要素2]
- リストにはそれぞれインデックス番号が振られている。
- 0から始まる番号
```
[1, 2, 3]
['mike', 'kate']
name = [1, 'mike', 5, 'kate']
print(name[1])
# 1

```
- リストの更新

```
foods = ['pasta', 'pizza']
foods[1] = "sushi"
```

- 要素の追加

```
foods.append('ramen') //リストの末尾に要素を追加
```

### リストの要素をすべて取得 for
- **for 変数名 in リスト** と書くことで、リストの要素の数だけ、処理を繰り返す
- for文の行末にはコロンを入れる

```
foods=['pasta', 'curry', 'sushi']
for food in foods: //行末にコロン
  print('I like' + food)
```
