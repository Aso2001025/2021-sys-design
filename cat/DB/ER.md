
```startuml
@startuml

!define MASTER_MARK_COLOR PaleGreen 
!define TRANSACTION_MARK_COLOR LightSkyBlue

package "ECサイト" as target_system{
  entity "顧客マスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>>{
    + costomer_code [PK]
    --
    pass
    name
    addless
    tel
    mail
    del_flag
    reg_date
  }
  
  entity "ペットマスタ" as pet <m_pets> <<M,MASTER_MARK_COLOR>>{
    + pet_code [PK]
    --
    costomer_code [FK]
    pet_name
    pet_age
    pet_category
    reg_date
  } 
  
  entity "病気マスタ" as disease <m_disease> <<M,MASTER_MARK_COLOR>>{
    + disease_code [PK]
    --
    disease_name 
  } 
  
  entity "アレルギーマスタ" as allergy <m_allergy> <<M,MASTER_MARK_COLOR>>{
    + allergy_code [PK]
    --
    allergy_name 
  } 
  
  entity "持病テーブル" as have_disease <d_have_disease> <<T,TRANSACTION_MARK_COLOR>>{
    + disease_code [PK][FK]
    costomer_code[PK][FK]
    disease_code[PK][FK]
    --
  } 
  
  entity "アレルギーテーブル" as have_allergy <d_have_allergy> <<T.TRANSACTION_MARK_COLOR>>{
    + disease_code [PK][FK]
    costomer_code[PK][FK]
    allergy_code[PK][FK]
    --
  } 
  
 
  entity "購入テーブル" as purchase <d_purchase> <<T,TRANSACTION_MARK_COLOR>>{
    + order_id [PK]
    --
    costomer_code [FK]
    purchase_date
    total_price
  } 
 
  entity "購入テーブル詳細" as purchase_detail <d_purchase_detail> <<T,TRANSACTION_MARK_COLOR>>{
    pet_code [PK]
     [PK]
    --
    item_code [FK]
    price 
    num
  }
  
  entity "カテゴリマスタ" as category <m_category> <<M,MASTER_MARK_COLOR>>{
    category_id [PK]
    --
    name
    peg_date
  }
  
  entity "商品マスタ" as items <m_items> <<M,MASTER_MARK_COLOR>>{
    item_code [PK]
    --
    item_name
    price
    category_id [FK]
    image
    detail
    del_flag
    periodic_delivery
    reg_date
  }
}

customer ||-r-o{ purchase
customer ||-d-o{ pet
pet ||-d-o{ have_disease
pet ||-d-r-o{ have_allergy
have_disease }o-d-|| disease
have_allergy }o-dr-|| allergy
purchase ||-r-|{ purchase_detail
purchase_detail }o-d-|| items
items }o-l-|| category

@enduml
```
