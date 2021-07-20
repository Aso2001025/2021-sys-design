# DB定義書
## ER図
[ER図はこちら](https://github.com/Aso2001025/2021-sys-design/blob/main/cat/DB/ER.md "ER図はこちら")

# DBテーブルカラム一覧
### 購入テーブル (d_purchase)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|オーダーID|order_id|bigint(20)|○|○||
|顧客コード|customer_code|varchar(50)||○|○|
|購入日|purchase_date|date||○||
|総額|total_price|int(11)||○||

### 購入詳細テーブル (d_purchase_detail)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|オーダー詳細ID|detail_id|bigint(20)|○|○||
|オーダーID|order_id|bigint(20)|○|○|○|
|商品コード|item_code|int(11)||○||
|価格|price|int(11)||○||
|数量|num|int(11)||○||

### 顧客マスタ (m_customers)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|顧客コード|customer_code|varchar(50)|○|○||
|パスワード|pass|varchar(50)||○||
|氏名|name|varchar(20)||○||
|住所|address|varchar(100)||○||
|電話番号|tel|varchar(20)||○||
|メールアドレス|mail|varchar(100)||○||
|削除フラグ|del_flag|int(1)||||
|更新日|reg_date|date||○||

### ペットマスタ (m_pets)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|ペットコード|pet_code|int(11)|○|○||
|顧客コード|customers_code|varchar(50)|○|○|○|
|名前|pet_name|varchar(20)||○||
|年齢|pet_age|int(2)||○||
|猫種|pet_category|varchar(20)||||
|更新日|reg_date|date||○||

### 病気マスタ (m_disease)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|病気コード|disease_code|varchar(50)|○|○||
|病気名|disease_name|varchar(50)||○||

### アレルギーマスタ (m_allergy)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|アレルギーコード|allergy_code|varchar(50)|○|○||
|アレルギー名|allergy_name|varchar(50)||○||

### 持病テーブル (d_have_disease)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|ペットコード|pet_code|int(11)|○|○|○|
|顧客コード|customers_code|varchar(50)|○|○|○|
|病気コード|disease_code|varchar(50)|○|○|○|


### アレルギーテーブル (d_have_allergy)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|ペットコード|pet_code|int(11)|○|○|○|
|顧客コード|customers_code|varchar(50)|○|○|○|
|アレルギーコード|allergy_code|varchar(50)|○|○|○|

### 定期便テーブル (d_periodic_delivery)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|顧客コード|customers_code|varchar(50)|○|○|○|
|商品コード|item_code|int(11))|○|○|○|
|配達間隔|delivery_interval|date||○||
|次のお届け日|next_delivery_date|date||○||
|更新日|reg_date|date||○||

### カテゴリーマスタ (m_category)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|カテゴリーID|category_id|int(11)|○|○||
|カテゴリ名|name|varchar(20)||○||
|更新日|reg_date|date||○||

### 商品マスタ (m_items)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|商品コード|item_code|int(11)|○|○||
|商品名|item_name|varchar(50)||○||
|価格|price|int(11)||○||
|カテゴリーID|category_id|int(11)||○|○|
|商品画像名|image|varchar(200)||○||
|商品説明|detail|varchar(500)||||
|削除フラグ|del_flag|int(1)||||
|定期便フラグ|periodic_delivery_flag|int(1)||○||
|更新日|reg_date|date||○||

### レビューテーブル (d_review)
|和名|属性名|型|PK|NN|FK|
|---|-----|-|--|--|--|
|レビューコード|review_code|int(11)|○|○||
|商品コード|item_code|int(11)|○|○|○|
|顧客コード|customers_code|int(11)||○|○|
|評価|star|int(1)||○||
|レビュータイトル|review_title|varchar(200)||||
|レビュー内容|review_detail|varchar(500)||||

