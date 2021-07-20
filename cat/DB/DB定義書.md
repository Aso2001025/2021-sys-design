# DB定義書
## ER図
[ER図はこちら](https://github.com/Aso2001025/2021-sys-design/blob/main/sample/md/ER.md "ER図はこちら")

# DBテーブルカラム一覧
### 購入テーブル (d_purchase)
d_purchase
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|order_id|bigint(20)|○|○||
|customer_code|varchar(50)||○|○|
|purchase_date|date||○||
|total_price|int(11)||○||

d_purchase_detail
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|detail_id|bigint(20)|○|○||
|order_id|bigint(20)|○|○|○|
|item_code|int(11)||○||
|price|int(11)||○||
|num|int(11)||○||

m_customers
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|customer_code|varchar(50)|○|○||
|pass|varchar(50)||○||
|name|varchar(20)||○||
|address|varchar(100)||○||
|tel|varchar(20)||○||
|mail|varchar(100)||○||
|del_flag|int(1)||||
|reg_date|date||○||

m_pets
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|pet_code|int(11)|○|○||
|customers_code|varchar(50)|○|○|○|
|pet_name|varchar(20)||○||
|pet_age|int(2)||○||
|pet_category|varchar(20)||||
|reg_date|date||○||

m_disease
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|disease_code|varchar(50)|○|○||
|disease_name|varchar(50)||○||

m_allergy
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|allergy_code|varchar(50)|○|○||
|allergy_name|varchar(50)||○||

d_have_disease
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|pet_code|int(11)|○|○|○|
|customers_code|varchar(50)|○|○|○|
|disease_code|varchar(50)|○|○|○|


d_have_allergy
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|pet_code|int(11)|○|○|○|
|customers_code|varchar(50)|○|○|○|
|allergy_code|varchar(50)|○|○|○|

d_periodic_delivery
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|customers_code|varchar(50)|○|○|○|
|item_code|int(11))|○|○|○|
|delivery_interval|date||○||
|next_delivery_date|date||○||
|reg_date|date||○||

m_category
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|category_id|int(11)|○|○||
|name|varchar(20)||○||
|reg_date|date||○||

m_items
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|item_code|int(11)|○|○||
|item_name|varchar(50)||○||
|price|int(11)||○||
|category_id|int(11)||○|○|
|image|varchar(200)||○||
|detail|varchar(500)||||
|del_flag|int(1)||||
|periodic_delivery|int(1)||○||
|reg_date|date||○||

d_review
|属性名|型|PK|NN|FK|
|-----|-|--|--|--|
|review_code|int(11)|○|○||
|item_code|int(11)|○|○|○|
|customers_code|int(11)||○|○|
|star|int(1)||○||
|review_title|varchar(200)||||
|review_detail|varchar(500)||||

