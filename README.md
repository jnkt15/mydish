# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## user テーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false, unique: true |
| picture            | string | null: false               |
| introduction       | text   |                           |
| sex                | string | null: false               |
| password 　　　　　　| string | null: false               |

### Association

- has_many :posts
- has_many :likes

## dish テーブル
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
- belongs_to :dish

## Favorite テーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| dish    | references | null: false, foreign_key: true |
