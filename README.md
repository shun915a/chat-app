# テーブル設計

## users table

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms table

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

## room_users table

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| name   | references | null: false, foreign_key: ture |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## messages table

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: ture |
| room    | references | null: false, foreign_key: ture |

### Association

- belongs_to :room
- belongs_to :user
