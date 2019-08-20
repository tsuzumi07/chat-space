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

## chat-space DB設計
##usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|string|null:false, index: true
|email|string|null:false, unique:true

#Association
has_many :massages
has_many :group_users
has_many :groups through,group_users


##massageテーブル
|column|type|options|
|------|----|-------|
|body|text|
|image|string|
|group-id|integer|null:false, foreign_key:true
|user-id|integer|null:false,foreign_key:true

#Association
belongs_to :group
belongs_to :user


##groupsテーブル
|column|type|options|
|------|----|-------|
|group_name|string|null:false,unique:true|

#Association
has_many :group_name
has_many :massages

##groups_usersテーブル
|column|type|options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

#Association
belongs_to :group
belongs_to :user