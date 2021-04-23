```uml
  @startuml
  start
  if(weather値は) then(1)
  :快晴です;
  else(2)
  :曇りです;
  else(3)
  :雨です;
  else(その他)
  :不明です;
  endif
  end
  @enduml
```
