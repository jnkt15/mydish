# 🍴 MyDish
### 作った料理を記録して共有できる、料理投稿SNSサービス。

![toppage](https://user-images.githubusercontent.com/73867079/104409356-7246ab00-55a9-11eb-941c-5866e34a28f7.png)


# 💭　概要

### 自分用のお料理ログとして使用。
### 家族内でのお料理レパートリー共有サービスとして活用。
作った料理を登録して、自分だけの料理レパートリーを作ることができます。
「今日は何作ろう？」と迷ったら、次に作る料理を「お気に入り」や「作る予定リスト」から選んだり、使いたい材料を元に検索して探したりすることができます。


# 🌐  App URL
### **https://mydish-123.herokuapp.com/** 


# 💻  利用方法

#### `☆ トップページから新規登録・ログイン`
#### `☆ 一覧画面へ遷移する`
#### `☆ 新規投稿は右に表示される「新しい料理を作る」ボタンをクリック
[![Image from Gyazo](https://i.gyazo.com/59b29ebb519875a3bed6064f01b28142.gif)](https://gyazo.com/59b29ebb519875a3bed6064f01b28142)
  <br>

#### `☆ 投稿完了後は投稿詳細画面へ遷移する`<br>
[![Image from Gyazo](https://i.gyazo.com/816bc1adcc460aa2481861d074051abd.gif)](https://gyazo.com/816bc1adcc460aa2481861d074051abd)
  <br>

#### `☆ 投稿完了後はトップページの一覧画面に表示される`<br>
[![Image from Gyazo](https://i.gyazo.com/1f6ac04550a73a5494bf8c4e33ce8ff0.gif)](https://gyazo.com/1f6ac04550a73a5494bf8c4e33ce8ff0)
  <br>

#### `☆ 一覧画面から１つの投稿を選択 → 投稿詳細画面へ遷移する`
#### `☆ 投稿者本人であれば投稿の編集・削除が投稿詳細画面から可能になる`<br>
 [![Image from Gyazo](https://i.gyazo.com/81686dc57b849909a2ad04f3140d2f33.gif)](https://gyazo.com/81686dc57b849909a2ad04f3140d2f33)
  <br>
  
#### `☆ 投稿詳細画面から、作った感想・次回作るときのためのメモを入力し、ログを作成できる`<br>
  [![Image from Gyazo](https://i.gyazo.com/2b65bc3dd35d36049f55e38cc95f68ce.gif)](https://gyazo.com/2b65bc3dd35d36049f55e38cc95f68ce)
  <br>

#### `☆ 投稿詳細画面からコメントができる`
#### `（コメント追加すると、料理を作った人の通知メニューが赤くなり通知されます。）`<br>
  [![Image from Gyazo](https://i.gyazo.com/89a3194e4778e7abe56af3fd90d22c75.gif)](https://gyazo.com/89a3194e4778e7abe56af3fd90d22c75)
  <br>

#### `☆ 投稿詳細画面からお気に入りを登録、作る予定リストに追加できる`
#### `（メニューから「お気に入り」「作る予定リスト」をクリックすると料理を見ることができます。）`<br>
  [![Image from Gyazo](https://i.gyazo.com/0587617f1ed2202ff39f98a572d92e27.gif)](https://gyazo.com/0587617f1ed2202ff39f98a572d92e27)
  <br>

#### `☆ 検索バーから関連するワードを入力し「検索」ボタンをクリックすると、関連するワードを含む料理の一覧が表示される`<br>
  [![Image from Gyazo](https://i.gyazo.com/537d14e3c0114649387dfe3625aab1d7.gif)](https://gyazo.com/537d14e3c0114649387dfe3625aab1d7)


# 🚜 開発環境

- VScode
- Ruby 2.6.5
- Rails 6.0.3.4
- mysql2 0.5.3
- JavaScript
- gem 3.0.3
- heroku 7.46.0


# テーブル設計

## User テーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false, unique: true |
| picture            | string | null: false               |
| introduction       | text   |                           |
| sex                | string | null: false               |
| password 　　　　　　| string | null: false               |

### Association

- has_many :dishes
- has_many :favorites
- has_many :comments

## Dish テーブル
| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| name             | string     | null: false                    |
| description      | text       | null: false                    |
| category_id      | integer    | null: false                    |
| reference        | text       | null: false                    |
| memo             | text       | null: false                    |
| picture          | text       | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :favorites
- has_many :comments

## Favorites テーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| dish    | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :dish

## Comments テーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| dish    | references | null: false, foreign_key: true |
| content | text       | null: false                    |

### Association

- belongs_to :user
- belongs_to :dish