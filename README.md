# README

#　テーブル設計

## usersテーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| shop_name          | string | null: false              |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| owner_name         | string | null: false               |

### Association
- has_many :menus
- has_many :orders


## menusテーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| name               | string     | null: false                    |
| price              | integer    | null: false                    |
| description        | text       | null: false                    |
| user               | references | null: false, foreign_key: true |


### Association
- belongs_to :user
- has_one :order

## ordersテーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| menu    | references | null: false, foreign_key: true |

### Association
- belongs_to :menu
- belongs_to :seat
- has_one :seat

## seatsテーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| seat_id            | integer    | null: false                    |

### Association
- belongs_to :order