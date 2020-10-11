---
title: "クラスについて"
---

# Chapter4


クラスについてです。

実際の仕事で頻繁に活用する部分で、詰まる箇所の多い場所でもあります。

## 困ったときに見るべきサイト

- [PHP入門](https://www.javadrive.jp/php/)
- [PHPマニュアル](https://www.php.net/manual/ja/index.php)

## クラスに入る前に

コード共有ツール [floobits](https://floobits.com/qst-exe/career2-php-thread/file/index.php:1)

CSRF対策の実装 [サンプルコード](https://github.com/qst-exe/career2-php-thread/blob/dev/index.php)

## クラスとは

[クラスの基礎](https://www.php.net/manual/ja/language.oop5.basic.php)

[クラスについてのスライド](https://docs.google.com/presentation/d/1PRWiSHmD7vePoipqRrc0Ya2aNXR-uunYGXbGEjCyc4c/edit?usp=sharing)

### 課題1

掲示板Appをクラス(Threadクラス)を使って書き換えてください。
(メソッドはこの通りでなくても大丈夫です)

```php
<?php

class Thread {

    public function __construct()
    {

    }
    
    public function getList() {
    
    }
    
    public function post() {
    
    }

    public function delete() {
    
    }
}

```

### 課題2

掲示板Appに複数のスレッドが立てられるようにしてください。スレッドのタイトルはなくても大丈夫です。
