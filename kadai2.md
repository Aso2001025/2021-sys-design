```uml
  @startuml
  お客 -> ホール係: 注文
  ホール係 -> 厨房: 席番号と料理
  厨房 --> ホール係: 完成した料理
  ホール係 --> お客: 注文した料理
  @enduml
```
  
  