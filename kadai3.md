```uml
  @startuml
  start
  if(weather値は) then(1)
  :快晴です;
  elsethen(2)
  :曇りです;
  else then(3)
  :雨です;
  else(その他)
  :不明です;
  endif
  end
  @enduml
```
