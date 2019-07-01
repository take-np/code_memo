# Gitの使い方

| コマンド | 意味 |
| -------- | ---- |
| コミット |      |
|          |      |

- git bash上で操作したほうが良い？
- cmdだと文字コードが異なるのか、`git commit -m 'first commit'` のようなコメントがうまくできない

```
# GithubへアップロードしたいProjectDirectoryに移動

cd /user/dev/projekct
# 必要ならば `git ignore` を作成し、Version管理しないファイルやDirectoryを記載。ex. *.log
vim .gitignore

# ProjectDirectory内にある、ファイルやDirectoryをすべてcommit
git add .
git commit -m 'first commit'

# 作詞した、GithubリポジトリのuRLをコピペして、リモートブラントとして設定

git remote add origin https://github.com/[your-name]/[project-name].git

# ローカルのファイルをアップロード
git push -u orgin master

```



## コミット
- ファイうりゃディレクトリの追加変更をリポジトリに記録する動作コミット実行時にはメッセージの入力を求められる
- 変更内容のわかりやすいk面とを書く
- 1行目：変更内容の要約
- 2行目：空行
- 3行目：変更の理由

## プッシュ
リモートリポジトリで自分の手元のローカルリポジトリの変更履歴を反映すること

```git pushのあとのorigin masterというのはoriginというリモートリポジトリのmasterというブランチにプッシュするという意味です。
この文字が間違っていると、pushが失敗するので気をつけるようにしてください。
https://techacademy.jp/magazine/10271
```

## プル
リモートリポジトリからローカルリポジトリを更新すること
リモートリポジトリから最新の変更履歴をダウンロードして、自分のローカルリポジトリにその内容を取り込む

## クローン
リモートリポジトリを複製するために操作
リモートリポジトリの内容をコピーして、別のマシンにローカルリポジトリとして作成できる

## ワークツリー
Gitの管理下に置かれた、実際に作業しているディレクトリのこと

## インデックス
リポジトリとワークルチ―の間には存在
リポジトリにコミットする準備をするための場所のこと
インデックスに登録されていないファイルはコミットされない

コミットでファイルの状態を記録するためには、インデックスにファイ売るを登録する


# Backlogへpushするときの手順- ヒェップさんが行ってくれたもの
```

t.miyazawa@LAP0344 MINGW64 ~
$

t.miyazawa@LAP0344 MINGW64 ~
$

t.miyazawa@LAP0344 MINGW64 ~
$ cd development/master_maintenance_app/

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ ls
app/  config/    db/      Gemfile.lock  log/          public/   README.md  test/  vendor/
bin/  config.ru  Gemfile  lib/          package.json  Rakefile  storage/   tmp/

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ ls -la
total 50
drwxr-xr-x 1 t.miyazawa 1049089    0 4月  19 09:04 ./
drwxr-xr-x 1 t.miyazawa 1049089    0 4月   5 15:07 ../
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:47 .bundle/
-rw-r--r-- 1 t.miyazawa 1049089  238 4月  15 13:21 .byebug_history
drwxr-xr-x 1 t.miyazawa 1049089    0 4月  19 09:12 .git/
-rw-r--r-- 1 t.miyazawa 1049089  695 3月  28 21:30 .gitignore
-rw-r--r-- 1 t.miyazawa 1049089   10 3月  28 21:30 .ruby-version
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 app/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 bin/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 config/
-rw-r--r-- 1 t.miyazawa 1049089  130 3月  28 21:30 config.ru
drwxr-xr-x 1 t.miyazawa 1049089    0 4月   5 15:15 db/
-rw-r--r-- 1 t.miyazawa 1049089 2009 4月  19 09:04 Gemfile
-rw-r--r-- 1 t.miyazawa 1049089 5128 4月  19 09:07 Gemfile.lock
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 lib/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:53 log/
-rw-r--r-- 1 t.miyazawa 1049089   80 3月  28 21:30 package.json
drwxr-xr-x 1 t.miyazawa 1049089    0 4月  12 16:01 public/
-rw-r--r-- 1 t.miyazawa 1049089  227 3月  28 21:30 Rakefile
-rw-r--r-- 1 t.miyazawa 1049089  374 3月  28 21:30 README.md
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 storage/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:30 test/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:53 tmp/
drwxr-xr-x 1 t.miyazawa 1049089    0 3月  28 21:47 vendor/

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ git remote add backlog https://np-develop.backlog.jp/git/SYSM_OPS_RD/mastermaintaince.git

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ ls
app/  config/    db/      Gemfile.lock  log/          public/   README.md  test/  vendor/
bin/  config.ru  Gemfile  lib/          package.json  Rakefile  storage/   tmp/

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ vi .git
.git/       .gitignore

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ vi .git
.git/       .gitignore

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ vi .git/
COMMIT_EDITMSG  description     hooks/          info/           objects/        refs/
config          HEAD            index           logs/           packed-refs

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ vi .git/
COMMIT_EDITMSG  description     hooks/          info/           objects/        refs/
config          HEAD            index           logs/           packed-refs

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ cat .git/config
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
        symlinks = false
        ignorecase = true
[remote "origin"]
        url = https://github.com/take-np/master_maintenance_app.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
[remote "backlog"]
        url = https://np-develop.backlog.jp/git/SYSM_OPS_RD/mastermaintaince.git
        fetch = +refs/heads/*:refs/remotes/backlog/*

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$ git push backlog master
Enumerating objects: 7399, done.
Counting objects: 100% (7399/7399), done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5953/5953), done.
Writing objects: 100% (7399/7399), 33.04 MiB | 2.24 MiB/s, done.
Total 7399 (delta 1512), reused 6452 (delta 1020)
remote: Resolving deltas: 100% (1512/1512), done.
To https://np-develop.backlog.jp/git/SYSM_OPS_RD/mastermaintaince.git
 * [new branch]      master -> master

t.miyazawa@LAP0344 MINGW64 ~/development/master_maintenance_app (master)
$
```
