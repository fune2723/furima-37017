## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| name               | string | null: false |
| birthday           | date   | null: false |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| image              | string     | null: false                    |
| item_name          | string     | null: false                    |
| message            | text       | null: false                    |
| category           | string     | null: false                    |
| situation          | string     | null: false                    |
| area               | string     | null: false                    |
| days               | integer    | null: false                    |
| price              | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association

- belong_to :users
- has_one :purchases

## purchases テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| item               | references | null: false, foreign_key: true |
| shipping_address   | references | null: false, foreign_key: true |

### Association

- belong_to :users
- belong_to :items
- has_one :shipping_addresses

## shipping_addresses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| post_code          | integer    | null: false                    |
| prefecture         | string     | null: false                    |
| municipality       | string     | null: false                    |
| address            | string     | null: false                    |
| building           | string     | null: false                    |
| number             | integer    | null: false                    |
| item               | references | null: false, foreign_key: true |

### Association

- belong_to :purchases