---
title: "FAQ | Laravel入門"
---

# Laravelの環境構築で詰まったときに見る章

随時追記していきます。

## MySQLが起動しないとき

https://qiita.com/kyorochan0219/items/01fafab61fc66aef86f8

こちらの操作を試したときには、 [XAMPPのMySQLのPortは正しいかどうか](#XAMPPのMySQLのPortは正しいかどうか) の箇所にあるように `.env` のportも変更するようにしてください

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


## Gitのpushに失敗するとき

[[Windows 10] Git BashでGitHubにSSH接続](https://qiita.com/coffee_g9/items/e1b9ab28cfa54f854308) のリンクを参考にssh接続をできるように設定をしてください

https://qiita.com/coffee_g9/items/e1b9ab28cfa54f854308
