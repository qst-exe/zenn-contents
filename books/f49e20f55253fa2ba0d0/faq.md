---
title: "FAQ | Laravel入門"
---

# Laravelの環境構築で詰まったときに見る章

随時追記していきます。

## MySQLにログインできないとき

以下の項目を順番にチェックしていってください

### MySQLのパスワードは正しいかどうか

`xampp > phpmyadmin > config.inc.php` をチェック

(PC環境によっては、`.php` の拡張子がついていない場合があります )

![](https://storage.googleapis.com/zenn-user-upload/xlhxom53dhjiwdbrxt0prdhya5fu)


### MySQLのパスワードを設定する

以下のコマンドを実行したのちにパスワードを「password」に変更してください

```
$ mysqladmin -u root password
```

## DBのマイグレーションに失敗するとき


### データベースを作成しているかどうか

[MySQLにログインできないとき](#MySQLにログインできないとき) も合わせて確認すること

### XAMPPのMySQLのPortは正しいかどうか

![](https://storage.googleapis.com/zenn-user-upload/2l23twykgfose1e10npcas9ro4xi)
