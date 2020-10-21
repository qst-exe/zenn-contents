---
title: "Laravel authを使ったログイン機能 | Laravel入門"
---

# Chapter8

Laravelに備わっている標準Authentication(Auth)を使ってログイン機能を作ります。

## Authentication(認証)

[認証 - Laravelドキュメント](https://readouble.com/laravel/7.x/ja/authentication.html)

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

※ npmでコケるひとはこちらからダウンロードしてください

https://nodejs.org/en/

## ルーティングの設定変更

`routes/web.php` のルーティングを書き換えてログイン必須にする


```php:routes/web.php
<?php

use Illuminate\Support\Facades\Route;

/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

Route::get('/', 'HomeController@index')->name('home');

Auth::routes();

Route::group(['middleware' => ['web', 'auth']], function () {
    Route::resource('todo', 'TodoController', ['only' => [
        'index', 'show'
    ]]);
});

```

ログイン後のデフォルトページを変更する

`RouteServiceProvider.php` の24行目を `/home` から `/todo` に変えれば大丈夫です。

```php:app/Providers/RouteServiceProvider.php
<?php

namespace App\Providers;

use Illuminate\Foundation\Support\Providers\RouteServiceProvider as ServiceProvider;
use Illuminate\Support\Facades\Route;

class RouteServiceProvider extends ServiceProvider
{
    /**
     * This namespace is applied to your controller routes.
     *
     * In addition, it is set as the URL generator's root namespace.
     *
     * @var string
     */
    protected $namespace = 'App\Http\Controllers';

    /**
     * The path to the "home" route for your application.
     *
     * @var string
     */
    public const HOME = '/todo';

    /**
     * Define your route model bindings, pattern filters, etc.
     *
     * @return void
     */
    public function boot()
    {
        //

        parent::boot();
    }

    /**
     * Define the routes for the application.
     *
     * @return void
     */
    public function map()
    {
        $this->mapApiRoutes();

        $this->mapWebRoutes();

        //
    }

    /**
     * Define the "web" routes for the application.
     *
     * These routes all receive session state, CSRF protection, etc.
     *
     * @return void
     */
    protected function mapWebRoutes()
    {
        Route::middleware('web')
            ->namespace($this->namespace)
            ->group(base_path('routes/web.php'));
    }

    /**
     * Define the "api" routes for the application.
     *
     * These routes are typically stateless.
     *
     * @return void
     */
    protected function mapApiRoutes()
    {
        Route::prefix('api')
            ->middleware('api')
            ->namespace($this->namespace)
            ->group(base_path('routes/api.php'));
    }
}
```

パスワードリセットメールを送信できるように `.env` の26行目付近にメール情報を設定します。

```
MAIL_MAILER=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=c2php.app@gmail.com
MAIL_PASSWORD=(パスワードは別途共有します)
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=c2php.app@gmail.com
MAIL_FROM_NAME="職業実践2 Laravel Todo App"
```
