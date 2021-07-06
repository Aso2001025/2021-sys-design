```startuml
@startuml
packege "ECサイト" as target_system{
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
}

@enduml
```
