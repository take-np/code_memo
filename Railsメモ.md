il2018/09/11

railsで以下を実行するとトップ画面のビュートコントローラーが作成される
## ページ作成に必要なもの
- view
- controller
- routing


rails generate controller home top
- viewファイル
	- htmlファイルのようなもの
- コントローラー
- アクションはブラウザに返すビューを、viewsフォルダの中から見つけ出す役割を持っている。
	- コントローラー内のメソッドを**アクション**
	- アクションはコントローラーと同じ名前のビューフォルダから、アクションと同じ名前のhtmlファイルを探してブラウザに返す
- ルーティング
	- ブラウザとコントローラを経由してビューを返しているのが、ルーティング
	- 送信されたURLに対して「どのコントローラのどのアクション」で処理するのか決める対応表のこと
	- ページが表示されるまでに**ルーティング→コントローラ→ビュー**の順で商利が行われている。
	- get "URL" => "コントローラ名#アクション名"
		- ブラウザから[localhost:3000/home/top]urlが送信されたときに、**home**　コントローラの　**top**　アクションで処理されるようになる

http://pentan.info/ruby/ror/url2controller.html
- http://localhost:3000/【コントローラ名】/【アクション名】
- アクセスされるファイル

| 操作     | パス     |
| :------------- | :------------- |
| コントローラ | app/controllers/【コントローラ名】_controller.rb |
| ビュー	 | app/views/【コントローラ名】/【アクション名】.html.erb|


	─ app
	　├ controllers
	　│└ 【コントローラ名】controller.rb
	　└ views
	　　└ 【コントローラ名】
	　　　└ 【アクション名】.html.erb

	アクセスされるメソッド
	class 【コントローラ名】Controller < ApplicationController
  	def 【アクション名】

  	end
	end


## コマンドの意味
- トップページを作成する**rails generate controller home top**
	- home : コントローラ名
	- top : アクション名
- 以上を実行すると、コントローラと空に対応したファイルが自動で作成される。
- ただし**同じ名前のコントローラがすでにある場合には**このコマンドを使うことはできない
- その場合には、ルーティング、コントローラ（アクション）、ビューを**自分で追加する**

### CSSファイル
- app/assets/stylesheets フォルダに入っている
- rails generate hontroller  home ... コマンドをジッコすると、CSSファイルも作成される。SCSSはCSSを拡張したもの
- railsでは、**stylesheets**　フォルダに保存されているCSSファイルにコードを書けば、すべてのビューに適用される。
### 画像
画像は　**public**　フォルダに配置しておくと、**<img src="/画像名">**　で指定できる


## データベース作成
投稿一覧ページに表示する投稿をデーターベースに保存する

## 目的に合わせたコントローラ作成
- 投稿に関するコントローラは　**post**　で作成する
- ** rails generate controller posts index**
	- 一覧ページを作成するときには、**index**　アクションを使用するのが一般的なので、そのアクションを用意する
	- posts : コントローラ名
	- index : アクション名
	- rails g controller posts indexで作成されるファイルとルーティング
		- tweet_apps/app/controllers/ **posts_controller.rb**
		-tweet_apps/view/posts/**index.html.erb**
		- tweet_apps/config/**routes.rb** / get "post/index "" => "posts#index"
		- posts indexへのルーティングが追加される

### 投稿内容を変数に代入
#### html上に<% %>Rubyコードを記述
- erb は Embedded Rubyの略
- 埋め込むRubyコードをブラウザに表示したい場合には **<%= %>** で囲む
	- **<%= %>** は変数の値を実際に表示したい場合
	- **<% %>** は変数の定義などに使用
-

### 投稿内容をいちいち表示しいられないので、繰り返処理表示を実行する
- 配列を用意する
- 配列からデータを受け取り、ひとつずつ表示する
	<%
	posts = [
	 "aaa", "****bb",...
	]

	<% posts.each do |post| %>
	 <div class="posts-index-item">
	  <%= post %>
	</div>
	//投稿の数だけ、htmlを書く必要がなくなる
	<%end%>


### Railsはアクションで変数を定義することが一般的
- コントローラのアクションで変数を提議するのが普通
- 通常アクションで定義した変数をビューでは使用できない。しかし、**@** から始めることによって、ビューファイルでも使用ｄけいる
- なので、アクションで定義したビューの変数には **@** をつける
-

	def index
		@post= ["aaa", "bbb", ...]
	end

## データーベース
- テーブル
	- 方のこと
- カラム
	- 縦の列
- レコード
	- １行ずつのデータ

- データベースを作成するためには、まずはじめにモデルを作成する
- データベースに変更を加えるためのモデル
### データベースに変更を反映するFileを作成する
- マイグレーションファイル
	- データベースに変更を支持するためのFile
	- **rails g(generate) model Post(テーブル名) content:text(カラム名:テータ型)**
		- Post postsテーブルを作成する場合には、Postと単数形にする
	- content ：カラム名
	- text ：データ型。textは長い文字列を意味しており、contentカラムにどのようなデータがはいるかを示している
	- 上記のコマンドを実行すると、マイグレーションファイルが作成される
- 続いて、 **db/migrate** を実行
	-

### データベースに変更を反映する
- データベースに変更を反映するには **rails db:migrate** のコマンドを実行
	- rails db:migrate ではなく、**rake db:migrate** だった。Railsのヴァージョンの問題？　cf. https://teratail.com/questions/86921
- コマンドを実行すると、マイグレーションファイルに書いてある指示通りに、テーブルを作成する

#### マイグレーションエラー
- Railsでは、データベースに反映されていないマイグレーションファイルが存在する状態で、どこかのページにアクセスすると、**マイグレーションエラー** が発生する

### モデル- tableを操作するためのもの
**rails g(generate) Post content:text** にてpostsデーブルを操作するPostモデルが生成されている。
- app/models/post.rb が作成されている
	- ファイルのなかには、ApplicatonRecordを継承したPostクラスが定義されている。
	- このようにApplicationRecoredを継承したクラスを **モデル** という
	- ※今回の作成の場合には、ApplicatonRecord ではなく、**ActiveRecord::Base** となっている
		- ActiveRecord::Baseのファイルはどこじゃ？？
### rails g model コマンド
- rails g model Post　の Post部分には、**モデル名** を指定する。指定するモデル名は **単数** ※コントローラ名は、**複数形** なので注意する
- このコマンドで作成されるファイルは以下の２つ
	- app/models フォルダにモデルが定義されたファイル
	- db/migrateフォルダにマイグレーションファイル

#### rails console
- ターミナル上で **rails console** と入力するとターミナルを起動できる。quit で終了
- コンソール上で定義した変数は、 quit でコンソールを終了するまで使用可能

### tableに投稿データを保存する
1. newメソッドでPostモデルのインスタンスを作成
2. postsテーブルに保存

	rails console
	post = Post.new(content: "Hello  world")
	post.save

	 ※Progateでは、「 models/post.rbがApoplicationRecordを継承していることで、saveメソッドが使用可能」と記載されているが、今回のものもできる？
	 → どうやらできるよう。可能なようです。どこにクラスの内容が記載されているのか


	 rails console
	 post = Post.first //最初のデータを取り出す
	 post.content // データテーブルの最初のデータの、content

post.all // すべての投稿を取り出す
post.all[0] //投稿の配列から一つのデータを取り出す。インデックス番号を指定する
post.all[0].content //配列のデータからcontentの内容を取り出す。



## テーブルの投稿データを表示する。すべての投稿表示する
postコントローラのindexアクション内の@postsに、Post.allで種痘したデータを代入する
ビューでは、@postsに代入されている配列データをeach分でひとつずつ変数postに代入し、
	[posts_controller.rb]
	def index
		@post = Post.all
	end

	[posts/index.html.erb]
	<% @posts.each do |post| %>
	 <div class="posts-index-item">
	 	<%= post.conten%>
	 </div>
	 <% end %>

### 共通のレイアウトでまとめる
- Rails では、**views/layouts/application.html.erb** に共通のHTMLを書いておける
- このページに、全ページ胸痛のヘッダーを表示されるようにする。
- views/layouts/application.html.erbには　**<%= yeild %>** というコードが書かれている。
- tophtml.erbなどのかくびゅーふぁいるは、この<%= yeild %> に代入され、application.html.erbの一部としてブラウザに表示されている。

	[application.html]
	<!DOCTYPE html>
	<html lang="en" dir="ltr">
		<head>
			<meta charset="utf-8">
			<title></title>
		</head>
		<body>
			<%= yield %> // こここに各ビューファイルが代入される
		</body>
	</html>

### link_toメソッド
- railsでは **link_to** メソッドを使うと <a>タグを作成できる。
- link_toメソッドは、Rubyのコードなので **<%= %>** で囲む
- 第一引数に標示する文字、第二引数にURLを書く

	[applicaton.html.erb]
	<%= link_to("About", "/about") %>
	// 以下の<a>タグに変換される
	<a href="/about">About</a>

# 投稿機能の作成
### 自動作成されるカラム
- テーブル作成時に自動生成されるもの
	- id, created_at, update_at
	- id
		- データベースに保存されるときに数字が自動で入る
		- idは1から入り重複しない
	- created_at, update_at
		- データベースに保存されたときに自動的に入る

## find_byメソッドっで投稿を種取得する
- 投稿詳細ページでは、データゲースから特定のidのと横行を取得するから、idは重要
- 特定のid の投稿を取得するために **find_by** メソッドを用いる
- ** モデル名.find_by(カラム名: 値)
	- post = Post.find_by(id:3)
	- post.content // "Rails 勉強中"
	- ※モデル：データベースを操作するときに必要

## 投稿詳細ページの作成
- 新たにページを作成するときに必要なももの
	- ルーティング、アクション、ビュー
- 投稿詳細ページのURLに表示したい投稿のidを入れるようにする
- そして、投稿のidをもつ投稿データを標示するようにする

### 新しいルーティングの描き方 :id　のように書く
- **posts/:id** のようにかくと **posts/~~** のようなすべてのURLが該当する
	- ルーティングのURL部分に **:** を用いて **post/:id** と指定することで、/post/1でもpost/2 でも、showアクションに行くように設定できる
- ただし、ルーティングを記載する順序に注意する。ルーティングは合致するURLを上から順番に探す。
	- なので、posts/:idを、posts/indexよりも上に書くと、localhost:3000/posts/indexといいうURLは、posts/:idのルーティングに一致してしまう

	[routes.rb]
	get "post/:id" => "posts#show"
	[posts_controller.rb]
	def show
	end


### URLからidの部分を取得する　変数params
- コントローラのアクション内では、ルーティングで設定したURLの[:id]部分の値を取得できる。
- その値は **params** という変数にハッシュとして入っている
	- **params[:id]** のように使用
	- ※ハッシュ
		- 複数のオブジェクトへの参照をまとめて管理することのができるオブジェクト
		- https://www.rubylife.jp/ini/hash/
		- 配列がインデックスを使って要素を区別して居たのに対して、ハッシュはキーと呼ばれるものを使用し区別する
		- 配列と違い、何番目の要素という指定はできない

	[route.rb]
	get "posts/:id" => "posts#show"

	[posts_controller.rb]
	def show
	@id = params[:id]
	end

	// なぜ上記のように設定したときに、postsテーブルの idが取得されるのか。というかURL上のposts/:idの部分には、各投稿のidはなぜ反映されるのか。自分たちでは設定していないはず

### 投稿詳細ページ params[:id]とfind_by

	[posts_controller.rb]
	def show
		@post = Posf.find_by(id: params[:id])
	end

	[posts/show.html.erb]
	<div class="posts-show-item">
		<% @post.content %>
		<div class="post-time">
			<%= @post.created_at %>
		</div>
	</div>

### Ruby 変数展開
- Rubyで文字列のなかで、変数を表示する方法
	name = "Sato"
	puts "こんにちは#{name}さん"


## 新規投稿
	- ルーティング、アクション、ビューを追加する
	- posts/:id よりは上に置くこと

### 入力フォームの作成 <textarea></textarea> <input>タグ

	[posts/new.html.erb]
	<textarea></textarea> //入力フォーム
	<input type="submit" name="" value="投稿"> //投稿ボタン

### 入力内容の保存 createアクションで、form_tagメソッド
1. 投稿 /posts/created
2. createアクション
3. データベースに保存

- createアクションのルーティングは **post** を使用する
- フォームの値を受け取る場合には、**post** とする。これはPostモデルのPostとは関係ない
- sessionの値を変更する場合は **post**
- 通常はget、フォームの値を受け取るときにはget

#### form_tagメソッド
- **form_tag(送信先のURL) do** と記述し、送信先のURLを指定する
- これによって、<input type="submit"> の投稿ボタンを押したときに、指定されたURLにデータが送信される

	[posts/new.html.erb]
	<%= form_tag("posts/create") d0 %>
### リダイレクト redirect_to("URL")
- 他のURLに転送するさいには、用いる
- createアクションではビューファイルを用意するかわりに、**リダイレクト** を用いる
- リダイレクトは

	[posts_controller.rb]
	def create
		redirect_to("/posts/index")
	end

### 投稿内容の保存 name属性
- textareaタグに **name属性** を指定すると、入力データを送信することができるようになる
- <textarea name="content"></textarea>
- name属性の値を **キー** とした **ハッシュ** がRails側に送信される
- name属性を指定したフォームに入力あれたデータは、コントローラのアクション内で受け取ることができる
- フォームのデータは変数 **params** で受け取る。paramsはname属性に設定した文字列をキーとした、ハッシュになっている。
- Postインスタンスを作成するさいに、params[:content]を用い→、contentが入力データであるインスタンスを作成している。
	[new.html.erb]
	<textarea name ="content"></textarea>
	<ipnut type = "submit" value="投稿">

	[posts_controller.rb]
	def create
		@post = Post.new(content: params[:content])
		@post.save
		redirect_to("/posts/index")
	end

### 変数paramsのまとめ
paramsの使い方
1. [:--]を使用した **ルーティングのURLから値を取得する**
2. [name= "--"] がついた **フォームの入力内容を受け取る**

	1.get "posts/:--" =>
	2.<textarea name= "--" >>/textarea>

### 投稿の並べ替え orderメソッド
- **order (カラム名: 並び替えの順序)** のように使用する
	- 並び替えの順序 **昇順:asc** **降順:desc**

	[posts_controller.rb]
	def  index
		@posts = Post.all.oerder(created_at: :desc)
	end

# 投稿の編集・削除　contentを上書きする
## 投稿の編集
- rails consoleにてデータベースの編集
1. 編集したい投稿を取得
2. 投稿のcontentを上書き
3. 編集した投稿を保存
4. 保存したのちに、postsテーブルの、update_atのカラムが更新される

	rails consoel
	post = Post.find_by(id:1)
	post.content = "Rails" //新しい値
	post.save

##投稿の削除 destroyメソッド
1. データベースから削除対しh投稿を取得する
2. destroyメソッドを用いて投稿を削除する


	rails console
	post = Post.find_by(id: 2)
	post.destroy


## 投稿編集ページの作成
- どの投稿の編集ページが判別するために、投稿編集ページのURLには編集したい投稿の:idを入れるようにする
- →ルーティングには、idを含める
- ビュー、ルーティング、アクションを追加する。

### 編集時の初期値の表示
- <textarea><%= @post.content %></textarea>
- <textarea></textarea>タを挟んだ値は初期値として表示される
- editアクションにて、urlのidの値をparamsを用いて取得する

	[posts_controller.rb]
	def edit
		@post= Post.find_by(id: params[:id])
	end

## 投稿の編集 updateアクション
- ルーティング
	-	post "posts/:id/update" => "posts#update" //フォームの値を受け取るので、[post]にする
- コントローラ
	- 完了後に投稿一覧あg面に転送するので、redirect_toを使う

- ビュー
	- フォームで入力した内容を、データベースに保存するために、updateアクションに投稿データを送信する。なので **form_tag** メソッドを用いる


	[posts/edit.html.erb]

	<% = form_tag("posts/:id/update") do %>
	<textarea><%= @post.content %></textarea>
	<input type="submit" name="" value="保存">
	<% end %>

## 投稿の削除 destroyメソッド
- ルーティング
	- destroyアクションはデータベースに変更を加えるので、**post** で定義する
- アクション
	- posts_controllerにdestroyアクションを定義する
###　ビューファイルでのdestroyアクションの書き方 postアクションであることに注意する
- link_to("削除", "/posts/#{@post.id}/destroy")のように書くと、ルーティングでは、**get "/posts/:id/destroy"** と書かれたアクションを探してしまう。
- post用のkink?toの書き方
- **<%= link_to("削除", "/posts/#{@post.id}/destroy", {method: "post"}) %>**
- のようにlink_toの第三引数に、**{method: "post"}** を使いすると、postとして定義されているルーティングにマッチする


# 投稿を制限する
## 空の投稿を防ぐ validationの設定　presence
- バリデーションは、不正なデータがデータベースに保存されないようにチェックする仕組みのこと
- バリデーションは **モデル** で設定する
- **valideates** を用いて、カラム名と内容を指定する
- {presence: true} を用いると、そのカラムの値が存在するかどうか、をチェックできる


	[models/post.rb]
	class Post < rbがApoplicationRecord
		**validates :検証するカラム名, {検証する内容}**
	end

	[models/post.rb]
	class Post < ApplicationRecords
		validates :content, {presence: true}
	endf

## 文字数制限　length

	[models/post.rb]
	class Post < ApplicatonRecord
		validates :content, {length: {maximum: 140}}
	end

## 検証する内容の複数指定
- バリデーションで検証する内容は、ハッシュとなっているから、**コンマ(,)** で区切ることで、複数指定できる


	validates :content, {presence: true, length: {maximum: 140}}

## バリデーションとsaveメソッド trueとfalseで場合分け
- 投稿に失敗したさいに、再度編集画面に戻るようにする
- saveメソッドで場合分けをする
- saveメソッドは戻り値を返している
	- 保存失敗時には、**false**
	- 保存成功時には、 **true**

	[posts_controller.rb]
	if @post.save
		#保存できた場合
		redirect_to("/post/index")
	else
		#保存できなかった場合
		redirect_to("/posts/#{@post.id}/edit")
	end

## 投稿失敗時に直前の投稿内容（失敗した投稿内容）を表示させるようにする renderメソッド
- updateアクションには、投稿失敗前には、@post.content に投稿に失敗した内容（140文字より多い文字数とか）が入っている
- 投稿に失敗した場合には、editを経由してしまうので、editのアクションが再度実行され、投稿内容が編集のものにもどる
- なので **edit** アクションを経由せずに、updateアクションから、edit.html.erbに飛べれば良い

### render メソッド
- renderメソッドを用いることで、**別のアクションを経由せず** 直接ビューを表示できる
- redirect_toメソッドを使った場合と違い、そのアクション内で定義した@変数をビューでそのまま使える
- **render("フォルダ名/ファイル名")** のように、表示したいビューを指定する。
- ※なぜ  2018/09/15なぜ render("posts/#{@post.id}/edit")ではないのか？？

	[posts_controller.rb]
	def update
		@post = Post.find_by(id: params[:id])
		@post.content =params[:content]
		render("posts/edit") //editアクションを経由せずに、直接edit.html.erbを表示できる
	end

##エラーメッセージを表示
- saveメソッドをよびだしたときにバリデーションに失敗すると、Railsでは自動的にエラーメッセージが生成されるようになっている
- **@post.errors.full_messages** のなかにエラー内容が配列で入っている
- @post.errors.full_messagesにエラーメッセージの配列が入っているタッめ、each分を用いることですべて標示できる


	[posts/edit.html.erb]
	<% @post.errors.full_messages.each do |message| %>
		<%= message %>
	<% end %>
## サクセスメッセージを標示する フラッシュ
- ページに一度だけ表示されるメッセージのこと。フラッシュが表示されたあと、ページを更新したり、別のページに移動したりすると、フラッシュは表示されなくなる


	[posts_controller.rb]
	def update
		if @post.save
		flash
	end

	[layouts/application.html.erb]
	<body>
		<header>

		</header>
    <% if flash[:notice]%>
      <div class="flash">
        <%= flash[:notice] %>
      </div>
    <% end %>
	</body>

## 新規投稿や削除でもメッセージを標示する
- 編集と同様の操作を行う

ただ、新規投稿の場合には、new.html.erbで変数@postを使用するがnewアクションでは、まだ変数@postが定義されておらず、newアクションで経由したときに、エラーが表示される

# ユーザーを作成する
- テーブルとモデルを用意する
1. ユーザーのデータをほぞんできるようにデータベースにusersテーブルを作成
2. テーブルを操作するためのmodelも用意する
- テーブルとモデルを用意したら、Userモデルのインスタンスを作成することでuserの新規追加が可能となる

	ralis g model User(#モデル名) name(#カラム名):string(#データ型）, email:string
	rails db:migrate


## バリデーションの追加
- emailとユーザー名が被らないように追加する。また同じメールアドレスやユーザー名でも登録できないように設定する
- postの時と同様にmodelに追加する
### 値の重複がないかチェックする
** uniqueness

## ユーザーの登録
- 投稿を作成したときと同様の手順で作成する
- 特攻作成ページでは複数行の入力フォームだったので、<textarea>タグを用いたが、ユーザー名とメールアドレスは１行で十分なので **<input>** タグを用いる
- inputタグは終了タグが不要
- 送信するために、iputタグにはname属性を指定する

	<p>ユーザー</p>
	<input>
	<メールアドレス>
	<input>
	<iput type="submit", value="新規登録">

value属性にRubyを埋め込む。
<input>タグの初期値にはRubyのコードを使うには、**<%= %>** を埋め込む
- value = "" ""のなかに、<%= %>を埋め込む


 	<input name="name" value = "<%= @user.name %>" >

## ユーザー編集機能の実装
- 投稿編集機能と同じこと
1. ユーザー編集ページの作成
2. 変更の保存
3. サクセス・エラーメッセージの表示


# ユーザー画像の表示
## プロフィール画像を表示する仕組み
- データベースに画像のファイル名を保存しておき、そのファイル名の画像を表示する。
- ファイル名を表示するために、データベースに、usersテーブルに、image_nameを追加する
- 画像の保存されるフォルダ **tweet_apps/public/user_image/default_user.jpg/**

## データベースにカラムを追加する 画像ファイル名を保存するカラム
- usersテーブルに、imaga_nameカラムを追加する
1. マイグレーションファイルを作成する
2. まいふレーションファイルの内容をデータベースに反映する

## rails g migration コマンド
1. **rails g model** コマンドでは、 **モデルとマイグレーションファイルの両方が作成されてしまう**
2. マイグレーションファイルのみを作成するように、 **rails g migration** コマンドを使う
3. 指定されたファイル名のマイグレーションファイルが作成される。ファイル名は追加するカラム名を含めるなどわかりやすいほうが良い。またファイル名は自動的に戦闘にファイルの作成日時が追加される

マイグレーションファイルの場所 **/db/migrate/ マイグレーションファイル名**


	[ターミナル]
	rails g migration add_image_name_to_users

- マイグレーションファイルを使い、テーブルに変更を加えるためには、マイグレーションファイルのなかの **change** メソッドの中に変更内容を記入する。
- rails db:migrate（今回の場合は、rake db:migrate）は、changeメソッドの中身を実行するためのコマンド

raims g modelによって生成されたマイグレーションファイルは、chamgeメソッドの中身が自動生成されていた。なので、マイグレーションファイルの中身に変更を加えることなく、そのままrails db:migrate(今回の場合は、rake db:migrate) を実行すれば、データベースに変更を加えることができた


	[rails g model によって生成されたマイグレーションファイル]

	class CreateUser < ActiveRecord::Migrate
		def change
			create_table posts do |t| //postsという名前のテーブルを作成している
				t.text :content // データ型がtextである、名前がcontentであるカラムを作成している

			end
		end
	end

カラムを追加するマイグレーションファイル
- changeメソッドの中身を自分で書く
- **add_column :テーブル名 :カラム名, :データ型**
- changeメソッドを追加したら、rals db:migarate(rake db:migrate)でデータベースに変更を反映する


	class AddImageNameToUsers < ActiveREcored::migration
		def change
			add_column :users, :image_name, :string
		end
	end

### 初期画像の設定
- 初期画像はpublic/user_imagesフォルダのなかに張っている（今回の設定の場合？ rails new tweet_apps と設定した場合には、すべてこのディレクトリに画像が保存される設定になっているのか？それとも、自分で設定しているのか？
- tweet_apps/public/user_images/

- ユーザー登録時にimage_nameカラムの値が、default_user.jpgになるように設定する
- createアクションの@userを定義しているところで、newメソッドの引数として、image_nameを記述するようにする


	[users_controller.rb]
	def create
		@user = USe.new ( name: params[:name], email: params[:email], image_name: "default_user.jpg")

	end

## ユーザー画像の表示
- htmlの **<img>** を用いる
- 画像は、public/use_imageにフォルダに保存されているので、src属性の値は、/user_image/ファイル名 とする、
- 今回の場合には、publicフォルダ配下にあるので、ファイル名からで記述はよいか？
	- <img src="<%= "/#{user.image_name}"%>"> のsrc属性にてディレクトリとファイル名を指定する。ここでは、public 配下にあるので、ファイル名だけで参照ができている
	- このpublicはいkになぜ自動的に参照できるのか？
	- srv属性の特徴？
- rubyのコードの値は、<% %>で囲む

## ユーザー画像の設定 type=file, {multipart: ture}
- **input** タグに、 **type="file"** をついかすることで、 画像ファイルを選択するボタンを表示できる。
- name属性はimageにしておく
- 画像の送信は特殊な設定であるから、form_tagに **{multiport: true}** を追加しておく。


	<%= form_tag("...", {multipart: true}) do %>

## 画像のアップロード ファイル名のデータベースへの保存と、画像の保存
### Rubyでファイルを作成、保存する方法
- Fileを作成するには、Rubyに元か用意されている、Fileクラスを利用する
- ファイルを作成するためには、Fileクラスの **write** メソッドを用いる。
- **File.write("Fileの場所", "ファイルの中身")**


	rails console
	File.write("public/sample.txt", "Hello, World")


## 画像のアップロード
- updateアクションにつける機能
	- Fileをデータベースに保存
	- publicフォルダ内に画像を作成

### ファイル名をデータベースに保存する
- nameやemailと同様に、@user.image_nameの値を上書きする

	[users_controller.rb]
	def update
		@user.image_name = "#{@user.id}.jpg" //画像のファイル名を、image_nameカラムに保存する。ファイル名は、user_idとなるようにする

### 画像を受け取る
- 画像ファイルも、nameやemailと同様にparams[:image]で受け取れる。
- 画像を保存するには、画像データを元に画像ファイルを作成する_必要がある。
- Fileを作成留守ためには、Fileクラスを作成する。
- ただし、画像データは特殊なテキストFileであるがめに、File.writeではなく、**File.binwrite** メソッドを用いる。
- 変数imageに対して、 **readメソッド** を用いることで、画像データを取得出来る


	[users_controller.rb]
	def update
		@user.image_name = "#{@user.id}.jpg"
		image = params[:image] //送信されたFileの情報が入っている
		File.binwrite("public/#{@user.image_name}", image.read)
		// File.binwrite("Fileの場所"m ファイルの中身（画像データ)
	end

### 画像が存在するか判定する
- 画像を保存する処理は、画像データが送信された場合だけ実行する

	[users_controller.rb]
	def update
		if params[:image]
			@user.image_name = "#{@user.id.jpg}"
			image= @arams[:image]
			File.binwrite("public/#{@user.image_name}", image.read)
	end

# ログイン機能
- ルーティング、アクション、ビューを追加する

## パスワード用のフォーム
- inputタグのtype属性を **password** とすると、入力したパスワードが伏せ字となる、パスワード用のフォームとなる


	<p>パスワード</p>
	<input type="password">

## データベースにパスワードカラムを追加する
1. マイグレーションファイルを作成する
2. マイグレーションファイルのchangeメソッドの中身を変更
3. rails (rake) db:migrateで、変更を反映

## パスワードにバリデーションを設定する
- ユーザーの情報には必ずパスワードを設定したいので、validationを設定する
	- 存在するかのバリデーションは、presence

## ログインの設定
- ルーティングとアクションの追加
- form_tagメソッドで、login_form.html.erbのフォーム送信先を設定する
- フォームに入力された値が、Rails側に送信されるように、input タグにname属性を追加する
- /login で上記2つのルーティングはかぶっているように見えるが、getとpostでは異なるルーティングとして扱われるので問題ない
	- link_toではデフォルトで、getのルーティングを探し、form_tagではデフォルトで、postのルーティングを探す

## ログインするユーザーを特定する
- フォーッ無に入れたメールアドレスとパスワードは、params[:email], params[:password] で受け取れる
- メールアドレスと、パスワードが一致するユーザーを取得し、変数@userに代入する

### ユーザーが存在する場合としない場合でパターンを分ける
- 存在する場合には、メッセージを表示し、ユーザー一覧ページにもどる
- ユーザーが存在しない場合には、ログインページを再表示する

	[users_controller.rb]
	def login
		@user = User.find_by(email: params[:email], passwrod: params[:password])
		if @user
			flash[:notice] = "ログインしました"
			redirect_to("/users/index")
		else
			render("users/login_form")
		end
	end

### ユーザーが存在しない場合の処理
- 登録されていないemailやpasswordが入力されたときには、再度ログイン画面を表示する、フォームに初期値を入れる、再度ログイン画面を表示する

#### エラーメッセージの表示
- 今回のエラーは、バリデーションのエラーメッセージとは異なり、「find_byメソッドで検索したが、ユーザーがいなかった」というエラー。なので、エラーメッセージは **自作する必要がある**


	[user_controller.rb]
	def login
		if @user
		else
			 @error_message = "アドレスとパスワードが一致しない"
			 render("users/login_form")
		 end
	end

	[login_form.html.erb]
	<% if @error_message %>
		<div class="form-error">
			<%= @error_message %>
		</div>
	<% end %>

## ログインしたユーザーの情報を保持し続ける 変数session
- 変数session
	- ページを移動してもユーザー情報を保持し続けるための特殊な変数
	- sessionに代入された値は、ブラウザに保存される。
	- ブラウザは、以降のアクセスで、sessionの値をrailsに返す
- session[:キー名] = 値
- user_idをキーとして、値を打移入する。@userが存在する場合に変数sessionに@user.idを代入することで、特定したログインユーザーの情報が保持される
	- ビューファイル上に表示することで、ブラウザから送信されたsessionの値を取得することができる


	[users_controller.rb]
	def login
		@user = User.find_by()

		if @user
			session[:user_id] = @user.id
	end
	[applicatoin.htmml.erb]
	<li>
		現在ログインしているユーザーのid:
		<% = session[:user_id]
	</li>


## ログアウト機能 nilを代入し、sessonの値を空にする
- ログイン処理とは逆に、ログアウトは変数sessionに代入した値を削除する
- ログイン・ログアウトはsessionがすべて
- **nil** を使う
- 機能を実装するために、アクションとルーティングを用意する。ルーティングはログインと同様に、get ではなく **post** を利用する
- sessionの値を変更する場合は **post**


	[users_controller.rb]
	def logout
		session[:user_id] = nil
		flash[:notice] = "ログアウトしました"
		redirect_to("/login")
	end

### ヘッダーメニューの表示をログインの有無で切り替える
- ログイン状態では、ログインページへのリンクを表示しないようにする
- ログイン状態では、sessionの値が異なることを利用して、両者で表示される内容をかえる
	- ログイン状態で表示するもの
		- session[user_id]
		- 投稿一覧
		- 新規投稿
		- ログアウト
	- ログアウト状態で表示するもの
		- TweetAppとは
		- ログイン

	[application.html.erb]
	<% if session[:user_id] %>
		<li> </li> //ログイン中の表示内容
	<% else %>
		<li> </li>
	<% end %> //ログアウト状態の表示内容


## ユーザー登録時のログイン
- ユーザーフォームにパスワード用のフォームを追加し、ユーザー登録時にパスワードカラムの値がせっていされるようにする
- createアクションのnewメソッドに引数としてpasswordを追加するようにする

	[new.html.erb]
	<p>パスワード</p>
	<input name="password", type="password", value="<%= @user.password %>" >

	[users_controller.rb]
	def creat
		@user = User.new(
			name: params[:name],
			email: params[:email],
			image_name: "default_user.jpg",
			password: params[:password]
			)
	end

- ユーザー登録時にログイン状態にする
作成したユーザーがそのままログイン状態となるように、usersコントローラーのcreateアクション内で作成したユーザーのid をsession[:user_id] に代入する

	[users_controllre.rb]
	def created
		@user = User.new()
		if @user.save
			session[:user_id] = @user.id
	end

### ユーザー名の表示
- ログイン中のユーザーの情報をデータベースから取得する
- find\byメソッドでusersテーブルからidからのの値がsesson[:user_id]と等しいユーザーを取得し、変数に代入する

	[layouts/application.html.erb]
	<% current_user = User.find_by(id: session[:user_id]) %>

	<li>
	 <%= link_to(current_user.name, "/users/#{current_user.id}") %>
	</li>

### アクション側で胸痛の変数を提議する before_action, application controller
- current_userは変数はビューで定義しているが。ビューで定義して大丈夫なのか
- applicatoin.html.erbの仕組み
	- 各アクションに対応したビューファイルは、application.html.erbの <%= yield %>部分に代入されている。
	- そのため、applicatoin.html.erbはすべてのアクションから呼び出されている
	- そのため、application.html.erbで使用したい変数を、アクション側で定義するとなると、すべてのアクションで@current_userを定義しないといけない

- 各コントローラで共通する処理がある場合には、before_actionを使用する
- アクションが呼び出された際には必ず、before_actionは実行される。
- 全アクションに共通する処理をまとめる事ができる
-
- すべてのコントローラーで共通する処理は **application** コントローラでにまとめることが出来る。
- set_current_userメソッドを提議すし、before_actionにしているすることで、全戸とローラで@current_userを定義できる

	[application.controllre.rb]

	before_action :set_current_user
	//アクションを呼び出す前位に、set_current_userメソッドを呼びあすことができる

	def set_current_user
		@current_user = User.find_by(id: session[:user_id])
	end


### ログインしていない場合のアクセス制限 before_action,application_controllre
- ログインしていない状態ではアクセスできないページを作成。ログインshていない場合でも、URLをt直接入力するとアクセスできていしまう。この場合、@current_userが居ない異倍位には、ログインページにリダイレクトするようにする、この処理は他のアクションでも利用したいので **applicationコントローラ** と **before_action** をもちいて処理を共通化させる
- application_controllerに **autenticate_user** というメソッドを作成し、アクセス制限の処理を共通化する
- すべてのアクションで実行したわけではなく、特定のアクションで実行したい。その場合、**only** を用いて、各コントローラでbefore_actionを使うことで指定したアクションでのみメソッドを実行することが出来る
- アクションはapplicationコントローラを **継承** していくので、継承元のメソッドを使うことができる
- @変数で定義した変数は同じクラスの異なるメソッドでも共通して使用可能。なので、sed_current_userで定義している@current_userは、authenticate_userでも使用できる

	[application_controllre.rb]
	def authenticate_user
		if @current_user == nil
			flash[:notice] = "ログインが必要です"
			redirect_to("/login")
	end
	[users_contoller.rb]
	before_action :authenticate_user, {only: [:edit, :update]}
	// onlyを用いて、適用したいアクションを指定する。
	// onlyでアクションを指定するときは、[]を用いて **配列形式** にする

### ログインしているユーザーが入れないページ。メソッドを作成し、適用する
- ログインユーザーが存在する場合、投稿一覧ページにリダイレクトする

	[applicaton_controller.rb]
	def forbid_login_user
		if @current_user
			flash[:notice] = "すでにログイン済です"
			redirect_to("/posts/index")
	end

	[home_controllre.rb]
	before_actiono :forbid_login_user, {only: [:top]}
	[users_controller.rb]
	before_action :forbid_login_user, {only: [:new, :create, :login, :login_form]}



### ユーザーの編集を制限する ログインしているユーザーの情報のみ編集できるようにする
- 詳細ページのユーザーとログインしているユーザーが一致する時にだけ編集リンクを表示する

	[users/show.html.erb]
	<% if @user.id == @current_user.id %>
		<%= link_to("編集", "users/#{user.id}/edit")
	<% end %>

- リンク先の表示制限だけでは、URLを直接入力するとアクセスできてしまうので、アクションでも制限する
- usersコントローラーのeditアクションおよびupdateアクションに制限をかける。ensure_correct_userメソッドを用意する。
- ログイン中のユーザーid と編集したいユーザーのid が一致しない場合にはフラッシュを表示し、投稿一覧ページにリダイレクトする
- ログイン中のユーザーid は@current_user.id に、 編集したいユーザーidはparams[:id]に代入されている。
- ただし、parasm[:id]で取得される値は **文字列** であり、数値で取得される@current_user.idと比較してもfalseとなる
- **to_i** メソッドを用いると。文字列を数値に変換できる
-

	[users_controller.rb]
	before_action :ensure_correct_user, {only: [:edit, :update]}

	def ensure_correct_user
		@user = User.find_by(id: params[id]).to_i
		if @user.id != @current_user.id
			flash[:notice] = "権限がありません"
			redirect_to("/posts/index" )
	end


# 投稿とユーザーを紐付ける
- 投稿一覧ページには、ユーザーの画像、名前が表示される
- ユーザーの詳細ページには、そのユーザーの投稿の一覧が表示される

## 投稿とユーザーを紐付ける user_idを用いて投稿とユーザーを紐付ける
- **どのユーザーがその投稿を作成したのか** を明らかにするために、postsテーブルに **user_id** というカラムを作成する
- postsテーブルにuser_idカラムを追加するために、マイグレーションファイルを作成する

	[ターミナル]
	rails g migration add_user_id_to_posts

	[マイグレーションファイルの中身]
	def change
		add_column :posts, :user_id, :integer
	end

- postsテーブルにuser_idカラムを作成したら、user_idは必ずあるべきであるから、ヴァリでーしょんFileを作成する。

 	[models/post.rb]
	validates :user_id, {presence: true}

## 新規投稿をログインユーザーにホモ付ける
- 投稿したユーザーのidを保存する
- 新規投稿作成時に、usre_idの値を入れて保存するようにする。
- 投稿したユーザーは@current\userであるから、@current_user.idで取得できる。

	[posts_controllre.rb]
	def created
		@post = Post.new(
			content: params[:content],
			user_id: @current_user.id
			)
	end

## 投稿にユーザー情報を表示する
-  投稿の詳細ページで、ユーザー名と、ユーザー画像を表示する
- 投稿にユーザー名やユーザー画像を表示するためには、そのユーザーの情報を表示する必要がある。
- 投稿詳細ページであるから、postsコントローラのshowアクションで、usersテーブルから、そのid に該当するユーザーの情報を取得する
- 取得した情報を投稿の詳細ページで表示する


	[posts_controller.rb]
	def show
		@post = Post.find_by(id: params[:id])
		@usee = User.find_by(id: @post.user_id)
	end

	[posts/show.html.erb]
	<div class="post-user-name"
		<img src=" <%="user_images\#{@user.image_name}"%>" >
		<%= link_to(@user.name, "/users/#{@user.id}") %>
	</div>

## renderとriderect_toの違い
|             |                                                    |
| ----------- | -------------------------------------------------- |
| redirect_to | 指定したcontroller、actionに再度リクエスト送信     |
| render      | controllerで処理した結果の出力先Viewを指定する<br> controllerのインスタンス変数は、そのままviewに返される|

基本的には以下の分類
- redirect_to
	- データを追加、更新、削除
- render
	- データの取得

アクション内には、renderもredirect_toも指定しない場合には、render アクション名を省略しているのと同じ効果
yよって、例えばindexアクション内であれば、views/index.html.erbが呼ばれる
※なければ、missing templete errorが返る


## yamlファイル
- 構造化のデータ表現方法
- あくまで仕様を表すのみ。使用を処理するには別途実装が必要
- 以下の設定で使われている
	- 各種設定ファイル
	- データの保存・シリアライゼーション用
	- データ交換用フォーマット
	- ログファイル
ruby

- 描き方

| 描き方     | データ構造のアウトプット       |
| ---------- | ------------------------------ |
| シーケンス | 配列形式データ構造を表す       |
| マッピング | ハッシュ形式でデータ構造を表す |


```
[inputSequence1.yml]
- d1
- d2
- d3


[inputSequence2.yml]
 d1

	- x1
	- x3
- d3

[output.rb]
require 'yaml'
d = YAML.load_file('inputSequence.yml')
e = YAML.load_file('inputMapping.yml')

p d # =>["d1", "d2", "d3"]
p e # =>["d1", ["x1", "x2"], "d3"]


name : tomato
email : potate@gmail.com

# => {"name" => "tomato", "email"=>"potato@gmail.com"}

name : tomato
emails:
	mail : potato@gmail.com
	sub : jagaimo@gmail.com
# =>{"name"=>"tomato", "emails"=>{"main" => "potato@gmail.com", "sub" => "jagaimo@gmail.com"}}
```
[参考リンク](https://qiita.com/Yama-to/items/587544993fb62610528a)



## rails api でわからないこと
= do
end
は一般的なモデル？API固有の書き方

- rabl
- apiにおけるview。クライアントからポイントを指定して、APIを叩かれたときに取得した情報を返すが、それを返す形式含め定義した場所が、viewファイルに対応する
- rablは、

### わからない単語
|             |     |
| ----------- | --- |
| desc        |     |
| helpers     |     |
| params (do) |     |
| post(do)    |     |
| put (do)    |     |
| delete (do) |     |
| requires    |     |
|             |     |


## helperの説明
- viewやモデルっでっ共通して使用したい機能を定義できる
- 基本的にはviewで読み込まれるようになっている。モデルで使用したい場合には、**include** で読み込む必要あり


[helperの使い方](https://qiita.com/shunsuke227ono/items/21f5968ca7ca0391b583)
[侍エンジニアリング	](https://www.sejuku.net/blog/28563)
## routesを極める
### debugを極める

```
ルーティングを書く際にはrake routes￼を実行する癖をつけましょう。ルーティングを作成するだけでなく、Railsのデバッグ時にも有用で、迷ったらとにかくrake routesを実行してもいいくらいです。

rake routesは実行のたびにRails環境を読み込むので、そのままでは遅いので有名です。以下のような方法で高速化しましょう。

pryとpry-rails gemがインストールされているなら、rails consoleを起動しておいてshow-routesを実行
spring gemがインストールされているならspring rake routesとすれば2度目以降から高速になる
dev環境が起動中ならhttp://localhost:3000/rails/infoを参照する (Rails 4)
```

[routesを極める](https://techracho.bpsinc.jp/baba/2014_02_17/15665)
### resources RESTfulなルーティングを自動生成
================================
 resoueces
 - RESTfulなルートを自動で実現する
以下の例では、productsテーブルに対して、実行
 resouces :name #:name はリソース名
 またここのプロダクトに対して、reviewが紐付いている場合など、は、その階層構造を表現できる
 resources :products do
   resources :reviews
 end
 # ================================

 [説明](https://www.sejuku.net/blog/27728)

### routesの設定
RESTfulなAPIを設定するに当たり、ルーティングが作成されるが、それらのroutesを確認できる。
また、名前空間や、アクションのみにスコープを設定する方法もある
[侍エンジニア](https://www.sejuku.net/blog/13078)

###  scaffold ――RailsでWebアプリを簡単に作成できる昨日
- scaffoldで作製したアプリには **CRUD** 機能が備わる
	- Create
	- Read
	- Update
	- Delete


## API
api中の下のものはhttpのメソッドに対応しているのではないか？
```
post do
	document = Document.new(doument_params)
end
https://qiita.com/kadotami/items/6cd455122acedf9510f2
```

#

## git
git add -
git commmit -m "メッセージ"
git push origin master

### includeとrequire

- require
	- クラスや、ファイルの読み込み
- include
	- Moduleおつかいメソッドを追加する





## Gemの更新
- gemの依存関係を調べる
```
gem dependency -R [gem_name]
```


- 特定のファイルだけ更新する
```
bundle update -conservative [gem-name]
```
https://qiita.com/itume/items/a1137da9eef7165dde38
http://makotottn.hatenablog.com/entry/2017/09/20/013404

- 
