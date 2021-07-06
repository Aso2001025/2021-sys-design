```startuml
@startuml
package "ECサイト" as target_system{
  entity "顧客マスタ" as customer <m_customers> {
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
 
  entity "購入テーブル" as purchase <d_purchase>{
    + order_id [PK]
    --
    costomer_code [FK]
    purchase_date
    total_price
  } 
 
  entity "購入テーブル詳細" as purchase_detail <d_purchase_detail>{
    detail_id [PK]
    order_id [PK]
    --
    item_code [FK]
    price 
    num
  }
  
  entity "カテゴリマスタ" as category <m_category>{
    category_id [PK]
    --
    name
    peg_date
  }
  
  entity "商品マスタ" as items <m_items>{
    item_code [PK]
    --
    item_name
    price
    category_id [FK]
    image
    detail
    del_flag
    reg_date
  }
}

customer ||-r-o{ purchase
purchase ||-r-|| purchase_detail
purchase_detail }○-d-¥{ items

@enduml
```
