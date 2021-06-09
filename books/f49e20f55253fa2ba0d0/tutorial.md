---
title: "チュートリアル"
---

# Chapter0

今回はPHPのプログラムを動かしてみましょう。
プログラムはなるべく、写経してエラーの原因が分からないときにはコピペで大丈夫です。

細かな挙動の意味については今後の授業で詳しく説明していきます。

## 事前準備

[repl.it](https://repl.it/) でPHPのプロジェクトを作成しましょう。

## 困ったときに見るべきサイト

- [PHP入門](https://www.javadrive.jp/php/)
- [PHPマニュアル](https://www.php.net/manual/ja/index.php)

## Hello World

```php
<html>
<head>
    <title>PHP Test</title>
</head>
<body>
<?php echo '<p>Hello World</p>'; ?>
</body>
</html>
```

### 課題

1. 出力する文字を変えてみよう
1. 文字に色を着けてみよう
1. 文字を変数に格納してみよう
1. コメントを記述してみよう

## フォーム

index.php

```php
<form action="action.php" method="post">
    名前: <input type="text" name="name" />
    年齢: <input type="text" name="age" />
    <input type="submit" />
</form>
```

action.php

```php
こんにちは、<?php echo htmlspecialchars($_POST['name']); ?>さん。
あなたは、<?php echo (int)$_POST['age']; ?> 歳です。
```

### 課題

1. フォームを1つ追加してみよう(職業, 好きな食べ物等)
1. action.php を <?php から始まる形式で書き換えてみよう


## カウントアップ

index.php

```php
<?php

$counter_file = 'counter.txt';

// ファイルが存在しなければデフォルト値:0のファイルを作成する
if (! file_exists($counter_file)) {
 file_put_contents($counter_file, 0);
}

$counter = file_get_contents($counter_file);
$counter++;

// fopen()、fwrite()、 fclose() を続けてコール
if (file_put_contents($counter_file, $counter) === FALSE){ 
 print('ファイル書き込みに失敗しました');
}

print('count:'.$counter);
echo "<br><button onclick='window.location.reload();'>更新</button>";
```

### 課題

1. countが10を超えそうになったら、0に戻すようにしよう


## 掲示板

index.php

```php
<html>
<head><title>PHP TEST</title></head>
<body>

<p>掲示板</p>

<form method="POST" action="<?php print($_SERVER['PHP_SELF']) ?>">
    <input type="text" name="personal_name"><br><br>
    <textarea name="contents" rows="8" cols="40">
</textarea><br><br>
    <input type="submit" name="btn1" value="投稿する">
</form>

<?php

if($_SERVER["REQUEST_METHOD"] === "POST"){
    writeData();
}

readData();

function readData(){
    $keijban_file = 'thread.txt';

    // ファイルが存在しなければデフォルト空文字のファイルを作成する
    if (! file_exists($keijban_file)) {
        $fp = fopen($keijban_file, 'w');
        fwrite($fp, '');
        fclose($fp);
    }

    $fp = fopen($keijban_file, 'rb');

    if ($fp){
        if (flock($fp, LOCK_SH)){
            while (!feof($fp)) {
                $buffer = fgets($fp);
                print($buffer);
            }

            flock($fp, LOCK_UN);
        }else{
            print('ファイルロックに失敗しました');
        }
    }

    fclose($fp);
}

function writeData(){
    $personal_name = $_POST['personal_name'];
    $contents = $_POST['contents'];
    $contents = nl2br($contents);

    $data = "<hr>\n";
    $data = $data."<p>投稿者:".$personal_name."</p>\n";
    $data = $data."<p>内容:</p>\n";
    $data = $data."<p>".$contents."</p>\n";

    $keijban_file = 'thread.txt';

    $fp = fopen($keijban_file, 'ab');

    if ($fp){
        if (flock($fp, LOCK_EX)){
            if (fwrite($fp,  $data) === FALSE){
                print('ファイル書き込みに失敗しました');
            }

            flock($fp, LOCK_UN);
        }else{
            print('ファイルロックに失敗しました');
        }
    }

    fclose($fp);
}

?>
</body>
</html>
```

### 課題

1. 投稿者名と内容を装飾してみよう
1. 投稿者名と内容が空のときには、掲示板に投稿できないようにしよう
