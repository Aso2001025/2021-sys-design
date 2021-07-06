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
 
 entity "購入テーブル" as <d_purchase>{
  + order_id [PK]
  --
  costomer_code [FK]
  purchase_date
  total_price
 }
}

@enduml
```
