---
title: "LaravelでのCRUD | Laravel入門"
---

# Chapter11

リソースコントローラを使って、TodoアプリのCRUD機能を作ります。

| メソッド | URI | ルーチン | ルート名 | 役割 |
|---|---|---|---|---|
| GET | /todo |	index | todo.index | 一覧の表示 |
| GET | /todo/create | create | todo.create | タスク作成ページの表示 |
| POST | /todo | store | todo.store | タスク作成の送信 |
| GET | /todo/{todo_id} | show | todo.show | タスク単体の表示 |
| GET | /todo/{todo_id}/edit | edit | todo.edit | タスク編集ページの表示 |
| PUT/PATCH| /todo/{todo_id} |update|todo.update | タスク編集の送信 |
| DELETE | /todo/{todo_id} |destroy|todo.destroy | タスクの削除 |


2020年11月4日 ここまで

## 課題

1. 上記のリソースコントローラを参考に、タスクの作成・編集・削除機能を追加してください。ただし、編集及び削除できるのは自分が作成したタスクのみです。
    1. タスク作成ページの作業イメージは [こちら](https://github.com/qst-exe/c2-php-todo/issues/4)
    1. タスク作成送信の作業イメージは [こちら](https://github.com/qst-exe/c2-php-todo/issues/5)
    1. タスク編集ページの作業イメージは [こちら](https://github.com/qst-exe/c2-php-todo/issues/6)
    1. タスク編集送信の作業イメージは [こちら](https://github.com/qst-exe/c2-php-todo/issues/7)
    1. タスク削除の作業イメージは [こちら](https://github.com/qst-exe/c2-php-todo/issues/8)
1. UI的に使いにくいところ抽出して修正してください    
1. 現状のタスクの進捗は数字で表現されています。これを文字表記にしてください。



