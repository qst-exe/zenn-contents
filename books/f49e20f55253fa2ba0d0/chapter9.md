---
title: "Eloquentのリレーション活用 | Laravel入門"
---

# Chapter9

リレーション機能を使って、データ同士の関連性を定義してログインしたユーザーのタスクのみが閲覧できるようにします。


## リレーション

リレーションとは…

https://wa3.i-3-i.info/word11596.html

Todoアプリのケースでは、 `users` テーブルと `todos` テーブルを紐付けるようにします。

```
$ php artisan make:migration add_todo_user_id
```

### 課題

`users` テーブルと `todos` テーブルを紐づけるためのマイグレーションスクリプトを作成してください。

```
ヒント
マイグレーション, リレーション, 外部キー制約
```
 
紐付けるマイグレーションを書いたら、マイグレーションの実行

```
$ php artisan migrate
```

## seederの修正

seederを修正して、 `user_id` をデフォルトで設置するようにします。

### 課題

1. seederを修正して、タスク1~10はユーザーid1、タスク11~20はユーザーid2、…タスク91~100はユーザーid10の所有タスクとなるようにseederを修正してください。
1. seederを修正して実行すると、とある問題が発生します。問題の原因を考えて修正してください。


テーブルを削除してマイグレーションとseederを実行するコマンド

```
$ php artisan migrate:fresh --seed
```

この時点で以下のアカウントが有効になっています。

```
メールアドレス: hoge+1@test.com
パスワード: password
```

## データ取得 

todo一覧のデータを `user_id` に応じて取得するようにします。

### 課題

1. todo一覧のデータを `user_id` に応じて取得するようにしてください。
1. todo単体ページについて起きている問題を考えて対応してください。


回答例1

https://github.com/qst-exe/c2-php-todo/commit/a2f297730bb8c56873207af32d1e8b9d891c5af3


回答例2

https://github.com/qst-exe/c2-php-todo/commit/3074856867d9c2b3ebdf8ca58136980618ad351c
