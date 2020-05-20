
# README
 
## Users テーブル
 
| Column     | Type    | Options                  |
| ---------- | ------- | ------------------------ |
| nickname   | string  | null: false, unique:true |
| email      | string  | null: false, unique:true |
| password   | string  | null: false, default""   |
| first_name | string  | null: false, default""   |
| last_name  | string  | null: false, default""   |
| first_kana | string  | null: false, default""   |
| last_kana  | string  | null: false, default""   |
| birthday   | date    | null: false              |
| tel        | string  |                          |
| image      | text    |                          |
| profile    | text    |                          |
 
### Association

- has_many :comments
- has_many :items
- has_many :likes
 
## Address テーブル
 
| Column        | Type    | Options                  |
| ------------- | ------- | ------------------------ |
| post_number   | string  | null: false, default""   |
| prefecture_id | integer | null: false, foreign_key |
| city          | string  | null: false, default""   |
| address       | string  | null: false, default""   |
| build_name    | string  |                          |
 
### Association
 
- belongs_to :user
- belongs_to :prefecture
 
 
## items テーブル
 
| Column        | Type    | Options                        |
| ------------- | ------- | ------------------------------ |
| name          | string  | null: false                    |
| detail        | text    | null: false                    |
| price         | integer | null: false                    |
| brand_id      | integer | null:false,foreign_key: true              |
| pay_side	    | integer | enum,null: false 				|
| post_date     | integer | enum,null: false				|
| status        | integer | enum,null: false			      |
| prefecture_id | integer | null: false, foreign_key: true |
| category_id   | integer | null: false, foreign_key: true |
| user_id       | integer | null: false, foreign_key: true |
 
### Association
 
- has_many :likes
- has_many :images
- has_many :comments
- has_many :categories through: :item_categories
- belongs_to :user
- belongs_to :prefecture
- belongs_to :brand
 
## comments テーブル
 
| Column  | Type    | Options                        |
| ------- | ------- | ------------------------------ |
| comment | text    | null: false                    |
| user_id | integer | null: false, foreign_key: true |
| item_id | integer | null: false, foreign_key: true |
 
### Association
 
- belongs_to :user
- belongs_to :item
 
## brands テーブル
 
| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |
 
### Association
 
- has_many :items
 
 
## images テーブル
 
| Column  | Type    | Options                        |
| ------- | ------- | ------------------------------ |
| url     | text    | null: false                    |
| item_id | integer | null: false, foreign_key: true |
 
### Association
 
- belongs_to :item
 
## item_categories テーブル
 
| Column        | Type    | Options                        |
| ------------- | ------- | ------------------------------ |
| item_id       | integer | null: false, foreign_key: true |
| categories_id | integer | null: false, foreign_key: true |
 
### Association
 
- has_many :items
- has_many :categories
 
## prefectures テーブル
 
| Column | Type   | Options              |
| ------ | ------ | -------------------- |
| name   | string | null:false,default"" |
 
### Association
 
- has_many :users
 
## likes テーブル
 
| Column  | Type    | Options                       |
| ------- | ------- | ----------------------------- |
| user_id | integer | null: false,foreign_key: true |
| item_id | integer | null: false,foreign_key: true |
 
### Association
 
- belongs_to :item
- belongs_to :user
 
## categories テーブル
 
| Column | Type         | Options     |
| ------ | ------------ | ----------- |
| name   | string       | null: false |
| path   | string:index |             |
 
### Association
 
- has_many :items through: :item_categories
 
