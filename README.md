## users
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|email|string|no|||
|password|string|no|||
|nickname|string||||
|birth_year|integer||||
|gender|integer|||1:male 2:female|
|name|string||||
|blog_url|string||||
|prof_image|string||||
|self_introduction|text||||
|region_id|integer|||||
#### relation
has_many:topics
has_many:communities, through: :community_users
has_many:community_users
has_many:goals
has_many:days
belongs_to:region
belongs_to:config

## communities
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|user_id|integer|no|ForeignKey||
|communities_category_id|integer|no|||
|condition_of_join|string|no|||
|publish_level|string|no|||
|authority|string|no|||
|introduction|text|||max 500文字|
|communities_image|string|||||
#### relation
has_many:topics
has_many:users, through: :community_users
has_many:community_users
belongs_to:community_category

## topics
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|body|text|no|||
|community_id|integer|no|ForeignKey||
|user_id|integer|no|ForeignKey|||
#### relation
belongs_to:user
belongs_to:community

## community_categories
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|community_category|string|no||||
#### relation
has_many:community

## goals
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|goal|text||||
|goals_category_id|integer|no|ForeignKey||
|achieve_year|integer||||
|achieve_month|integer||||
|achieve_date|integer||||
|this_month_goal|integer||||
|user_id|integer|no|ForeignKey|||
#### relation
belongs_to:user
belongs_to:goals_category
belongs_to:genre

## goals_categories
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|goals_category|string|no||||
#### relation
has_many:goals

## genres
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|genre|string|no||||
#### relation
has_many:goals
has_many:days

## regions
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|region|string|no||||
#### relation
has_many:users

## configs
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|user_id|integer|no|ForeignKey||
|unit_of_velocity|integer|no||1:時速(km/h) 2:ペース(分/km)|
|publishing_id|integer|no|ForeignKey||
|condition_publishing_id|integer|no|ForeignKey||
|monitor|integer|||check:新しい商品のモニターを希望する|
|weekly_letter|integer|||check:掲載する|
|link_approval|integer|no||1:確認して承認 2:自動で承認||
#### relation
has_many:users
belongs_to:publishing
belongs_to:condition_publishing

## publishings
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|publishing|string|no||公開範囲設定|
#### relation
has_many:configs

## condition_publishings
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|condition_publishing|string|no||公開範囲設定|
#### relation
has_many:configs

## days
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|genre_id|integer|no|ForeignKey||
|distance|integer||||
|hour|integer||||
|minute|integer||||
|second|integer||||
|memo|text||||
|step_count|integer|||walkのみ|
|weight|integer||||
|body_fat_rate|integer||||
|input_calorie|integer||||
|body_age|integer||||
|waist|integer||||
|heart_rate|integer||||
|max_bp|integer||||
|min_bp|integer||||
|weather_id|integer||ForeignKey||
|diary|text||||
|image|string||||
|date|date|||||
#### relation
belongs_to:user
belongs_to:genre
belongs_to:weather

## weathers
|column|Type|Null|Key|other|
|:--|:--|:--|:--|:--|
|id|integer|no|PrimaryKey||
|weather|string|no||||
#### relation
has_many:days
