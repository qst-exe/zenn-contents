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

## 課題

1. 上記のリソースコントローラを参考に、タスクの作成・編集・削除機能を追加してください。ただし、編集及び削除できるのは自分が作成したタスクのみです。
2. 現状のタスクの進捗は数字で表現されています。これを文字表記にしてください。



