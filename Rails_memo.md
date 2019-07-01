時間の記録
|2019/03/31|10p|60min|
||||
||||
||||


## Railsメモ
### 制御の反転 IoC Inveersion of Contorl
プログラムの実行主体が逆転する性質。
クラスのように、機能をまとめたものといえば、フラームworkとライブラリは似ているが、上記の実行主体の点が異なる

- フレームワーク
	- ユーザーコードが、Applicationフレームワークによって呼び出される
　- フレームワークが、アプリのライフルール（初期化からジッ処理、終了までの流れ）を管理している。
　- その要所要所で、何をスべきか、をユーザーコードに問い合わせる
　- ユーザーコードはｍ，もはやアプリの管理者ではなく、Application Frameworkの要求にしたがう
- ライブラリ
	- ユーザーコードから呼び出されるもの。
　- ライブラリが、何かを自発的に行うわけではない。ユーザーコードからの指示を受けて初めて何らかの処理を行う
RasilはこうしたフレームワークのなかでもWebApplicationの開発するためのフレームワーク。
Waf Web Application Framework
※その他には、デスクトップアプリを開発するためのフレームワークもある

## MVCパターン
- Model - View - Controller パターン
- Model - ビジネスLogic
	- 汎用的に再利用可能なビジネスLogic。データの操作などを担当。外部Serviceやデータベースとの関わる
- View - ユーザーinterface
	- 最終的な出力（HTMLやJSONなど）の描画出力を担当

- Controller - ModelとViewの制御
　- リクエストデータの処理、ビジネスLogicの呼び出し、出力へのふりわけ
1. Controller クライアントからのリクエストを受け取り、
2. ModelからビジネスLogicが呼び出される。controllerに結果が送られる。
3. 処理結果が、viewに引き渡される
4. クライアントへレスポンスが渡される
### MVCパターンのメリット
- プラグラマとデザイナーで並行作業を行いやすい
- デザインとLogicのそれぞれの修正が相互に影響しない（保守が容易）
- 機能単位のテストを独立して実施できる（テストを自動化しやすい）

- MVCパターンはRails固有の概念ではない。Webの世界ではMVCパターンを前提とした開発が一般的

### Railsの設計哲学
- DRY(Dont't Repeat Yourself) 同じ記述を繰り返さない
	- ex. データベースのスキーマ定義を設定ファイルとして記述する必要がない。データベースにテーブルを作成すらだけで、あとはRailsが自動的に認識してくれる
- CoC ( Convention over Configuration) 設定よりも規約
	- ex. Conventionとは、Railsがあらかじめ用意している名前付けのルール。usersテーブルを読み込むためには、Userという名前のクラスを利用する。互いに関連付けの必要がないのは、users（複数形）とUser（単数形）がRailsの規約によって結び付けられているため

## Railsのライブラリ構造
- Railsはアプリ開発のためのライブラリはもちろん、コード生成のための、ツールや動作確認のためのServerなどをひとまとめにしたフルスタック（全部入り）なフレームワーク

- Rails
	- Action Pack - Action Controller / Action Dispatch / Acition View の総称（MVCのVC）
		- Action Controller - Controllerの管理、リクエスト処理、状態処理、レスポンスの生成などを司る
	　- Action Vew - HTMLやXML、JSONなどの各種フォーマットでのレスポンスを生成。View開発に役立つ。ヘルパーやレイアウト機能を提供。Ajaxにも対応
	　- Action Dispatch - リクエストをどのクラスで処理するかを決定するルーティング機能を提供
　- Active Model - 命名規則、喧騒機能など、Modelの基本的な規約を定義
　- Active Record - データベースアクセスのための基本機能を提供
	- Action Mailer - メールの送受信のためのライブラリ
　- Active Job - バックグラウンドで実行すべきJobを管理
　- Action Cable - RailsアプリにWebSocket機能を提供
　- Active Support - Ruby標準ライブラリの拡張
　- Raities - Railsの各種コンポーネントやプラグインをつなぎ合わせるRailsのコア


## generate
```
bundle exec rails g [controller] [method]
```

- コントローラと、アクション、対応したviewが生成される

```
bundle exec rails g [model] [カラム名;カラム型]

bundle exec rail db:migrate
```

- モデルが生成される。モデルの中身を変更することで、テーブルのカラムを作成できる






