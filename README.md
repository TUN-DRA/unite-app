# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| trainer_name       | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Column      | Type    | Options     |
| ----------- | ------- | ----------- |
| lobby       | string  | null: false |
| top1        | integer |             |
| top2        | integer |             |
| jungle      | integer |             |
| bottom1     | integer |             |
| bottom2     | integer |             |
| description |  text   |             |
| rank        | integer |             |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user