---
title: "Laravel authを使ったログイン機能 | Laravel入門"
---

# Chapter8

Laravelに備わっている標準Authentication(Auth)を使ってログイン機能を作ります。

## Authentication(認証)

[認証 |Laravelドキュメント](https://readouble.com/laravel/7.x/ja/authentication.html)

## authの導入

![完成イメージ](https://storage.googleapis.com/zenn-user-upload/2n4i8rddvkciawf2m71r20xwh30k)

composerでライブラリの導入(Laravelのバージョンでコマンドが違うので要注意)

```
$ composer require laravel/ui 2.*
```

認証に必要なるルーティングとビューを作成

```
$ php artisan ui vue --auth
```

Vue関連のパッケージをインストールする

```
$ npm install && npm run dev
```

## ルーティングの設定変更

ルーティングを書き換えてログイン必須にする

[routes/web.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/80651712faf1036d3b23666adfcdd86ea5cf8390/routes/web.php)

ログイン後のデフォルトページを変更

[app/Providers/RouteServiceProvider.php](https://raw.githubusercontent.com/qst-exe/c2-php-todo/80651712faf1036d3b23666adfcdd86ea5cf8390/app/Providers/RouteServiceProvider.php)
