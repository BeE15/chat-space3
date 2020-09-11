## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|password_confirmation|string|null: false|
### Association
- has_many :groups_users
- has_many :groups, through: groups_users
- has_many :messages



## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
### Association
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
