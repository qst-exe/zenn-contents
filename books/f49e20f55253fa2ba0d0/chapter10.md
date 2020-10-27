---
title: "Bladeテンプレートを使ったコーディング | Laravel入門"
---

# Chapter10

Laravelのビューテンプレートエンジン「Blade」を使った効率的なコーディングを習得します。


## Bladeとは

Laravelの場合には、index.phpとindex.blade.phpがあるときには、index.blade.phpを優先して読み込んでくれます。

### 変数などの出力

```php:sample.blade.php
{{ hoge }}
```


### コメント

```php:sample.blade.php
{{-- このように書かれたテキストはコメント扱いです --}}
```


### ifディレクティブ

```php:sample.blade.php
@if (条件式)


@endif
```

### その他のディレクティブ

条件式がfalseの場合に表示する

```php:sample.blade.php
@unless (条件式)
表示内容
@endunless
```

変数が空の場合に表示する

```php:sample.blade.php
@empty (変数)
表示内容
@endempty
```

変数が定義されている(nullでない)場合に表示される

```php:sample.blade.php
@isset (変数)
表示内容
@endisset
```


isset, empty, is_nullなどの挙動の違い 

https://www.php.net/manual/ja/types.comparisons.php


### 繰り返し

for文の代替

```php:sample.blade.php
@for (初期条件; 条件; 後処理;)
表示内容
@endfor 
```

foreach文の代替

```php:sample.blade.php
@foreach (配列 as 変数)
表示内容
@endforeach
```

while文の代替

```php:sample.blade.php
@while (条件)
表示内容
@endwhile
```

※ 他にも色々なディレクティブがあるので、調べてみてください。ただし、ディレクティブを多用するとビューがロジックを持ち過ぎてしまうので要注意です。


### レイアウトについて

#### 継承

クラスの継承と同じような感覚でレイアウトの継承を行うことができます。

#### セクション

セクションはレイアウト内に用意される区間のこと

#### @extend 

親テンプレートの読み込み

#### @yield

viewごとに変わるコンテンツ(ページタイトルやコンテンツ)


#### @section

親テンプレートで記述した内容を子テンプレートで利用できる

#### @include

外部テンプレートの読み込みができる。ヘッダーやサイドバー、フッター等で利用される

