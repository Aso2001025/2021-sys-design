```uml
  @startuml
    opt ログイン
      ユーザー -> webサーバー: ログイン
      webサーバー -> DBサーバー: ログイン照会
      DBサーバー -> DBサーバー: ログイン認証
      DBサーバー -> webサーバー: 認証結果
      alt 認証成功
        webサーバー -> ユーザー: ログイン成功メッセージを表示
      else 認証失敗
        webサーバー -> ユーザー: ログイン失敗メッセージを表示
      end
     end
     
    activate ユーザー
    opt 商品検索
      ユーザー -> webサーバー: 検索（商品名）
      webサーバー -> DBサーバー: 検索処理（商品名）
      DBサーバー -> DBサーバー: 検索処理
      DBサーバー -> webサーバー: 検索結果
      webサーバー -> ユーザー: 検索結果
    end
    
    deactivate ユーザー
    
  @enduml
```
