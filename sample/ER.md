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
 
  entity "購入テーブル" as purchase <d_purchase> <<T.TRANSACTION_MARK_COLOR>>{
    + order_id [PK]
    --
    costomer_code [FK]
    purchase_date
    total_price
  } 
 
  entity "購入テーブル詳細" as purchase_detail <d_purchase_detail> <<T.TRANSACTION_MARK_COLOR>>{
    detail_id [PK]
    order_id [PK]
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
    reg_date
  }
}

customer ||-r-o{ purchase
purchase ||-r-|{ purchase_detail
purchase_detail }o-d-|| items
items }o-l-|| category

@enduml
```
