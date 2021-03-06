---
title: "PHPフレームワークを使ったアプリ開発 | Laravel入門"
---

# Chapter7

PHPフレームワーク「Laravel」を使ってアプリ開発を行います。

[Webアプリケーションフレームワークについて](https://docs.google.com/presentation/d/1onUP5XoR9SAaq9yOdswa84rxFh0LPO35g_7UhuTlv6E/edit?usp=sharing)

## Laravelのインストール

`Git Bash` または `VS Code` のターミナルからコマンド起動をしてください。

Laravelインストーラのダウンロード(composerのインストールが必須です)
```
$ composer global require laravel/installer
```

プロジェクト作成の場所に移動(1か2のどちらかを実行すればOKです)

1) Git Bashの場合
```
$ cd /c/xampp/htdocs/
```

2) VS Codeの場合
```
$ cd C:\xampp\htdocs\
```

プロジェクトの作成
```
$ composer create-project "laravel/laravel=7.*" todo
```


`htdocs` に `todo` フォルダができているので、 `VSCode` の `フォルダを開く` から `todo` を開いてください。

[各ディレクトリの構成](https://readouble.com/laravel/7.x/ja/structure.html)

Laravelサーバの起動
```
$ php artisan serve
```

Laravelで作ったアプリケーションは以下のURLから閲覧できます。

http://localhost:8000/

## GitHubでのリポジトリ作成

今まではForkしてリポジトリを作っていましたが、これからは各個人のアカウントに直接リポジトリを作ってください。

リポジトリ作成後には、対象プロジェクトを `VS Code` で開いてcommit&pushをしてください。

[GitHubでのリポジトリ作成](https://youtu.be/jp_l-arRaz8)

### GitHubの内容が更新されないとき

#### GitHubの内容が「README.md」だけになっている

```
$ git add .
```

を実行した後に以下の動画の続きを試してみてください

[https://youtu.be/jp_l-arRaz8?t=36](https://youtu.be/jp_l-arRaz8?t=36)

#### ターミナルに The requested URL returned error: 403 のエラーが出ている 

GitにPushできないときには [こちらの操作](https://wak-tech.com/archives/933) をしたあとに 

```
$ git push -u origin main
```
 
 を試してください

## テーブルの作成

```
$ cp .env.example .env
```

`.env` ファイルの12行目付近にいつもの情報を記載してください。

```
DB_DATABASE=todo
DB_USERNAME=root
DB_PASSWORD=password
```

テーブルの作成

```
$ php artisan make:migration create_todos_table
```

生成されたファイルの中身は以下のものと同じようにしてください(YYYY_mm_dd_HHiissは今の時間になっているので違ってもOKです)

[YYYY_mm_dd_HHiiss_create_todos_table.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/495a7bcc009bd7cc912f3ca00f601bcc66cde9a2/database/migrations/2020_10_11_100323_create_todos_table.php)

マイグレーション

```
$ php artisan migrate
```

## Seederの作成

seederの作成
```
$ php artisan make:seeder TodoTableSeeder
```

[TodoTableSeeder.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/76a7233d782999004bcafea2ccf87124fed336c4/database/seeds/TodoTableSeeder.php) の中身

`TodoTableSeeder.php` の`run` が実行されるように `DatabaseSeeder.php` の設定

```php:DatabaseSeeder.php
<?php
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
         // TODO: UserSeederをTodoTableSeederに変更する 
         // $this->call(UserSeeder::class);
         $this->call(TodoTableSeeder::class);
    }
}

```

seederの実行
```
$ php artisan db:seed
```

## Todo一覧の作成

![Todo一覧の作成](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/36927/aaed0d55-aae9-eb3c-150e-987f30e9b22e.jpeg "Todo一覧の作成")

Todoモデルの作成
```
$ php artisan make:model Todo
```

Todoコントローラーの作成
```
$ php artisan make:controller TodoController --resource
```

### 各リソースコントローラのアクション

[リソースコントローラ](https://readouble.com/laravel/7.x/ja/controllers.html#resource-controllers)

---- 

### ルーティングとController、Viewの紐付け

ルーティングを設定

[routes/web.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/feature/index/routes/web.php)

メソッドにデータ取得とViewを紐付ける処理を追加

[app/Http/Controllers/TodoController.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/feature/index/app/Http/Controllers/TodoController.php)

Todo一覧ページのViewを記述

[resources/views/todo/index.blade.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/99f74d4c268371aac47d968b4cca3b170117617d/resources/views/todo/index.blade.php)

http://localhost:8000/todo にTodo一覧が表示されます。

## Todo単体ページの作成

![Todo単体ページの作成](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/36927/ce867ccc-a868-3b11-7840-9b2d53ff790f.jpeg "Todo単体ページの作成")

### ルーティングとController、Viewの紐付け

ルーティングを設定

[routes/web.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/feature/show/routes/web.php)

メソッドにデータ取得とViewを紐付ける処理を追加

[app/Http/Controllers/TodoController.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/feature/show/app/Http/Controllers/TodoController.php)

[resources/views/todo/index.blade.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/feature/show/resources/views/todo/index.blade.php)

Todo単体ページのViewを記述

[resources/views/todo/show.blade.php](https://raw.githubusercontent.com/qst-exe/c2-laravel-todo/4bf89ada0e4ac64212c83be0af75a6ca2a672d0f/resources/views/todo/show.blade.php)

## ページネーションの追加

![ページネーションの追加](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/36927/64fa6560-2a36-55d5-27b2-17c8a7192869.jpeg "ページネーションの追加")


ページネーションの処理追加

[app/Http/Controllers/TodoController.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/main/app/Http/Controllers/TodoController.php)

ページネーションのView追加

[resources/views/todo/index.blade.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/main/resources/views/todo/index.blade.php)


## この章終了時点でのコード

https://github.com/qst-exe/c2-php-todo/tree/chapter1
