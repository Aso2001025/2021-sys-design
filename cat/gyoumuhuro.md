```uml
  @startuml
    opt 未登録
      ユーザー -> webサーバー: ユーザー登録
      webサーバー -> DBサーバー: ユーザー登録
      DBサーバー -> DBサーバー: 登録処理
      DBサーバー -> webサーバー: 登録処理
       alt 登録成功
        webサーバー -> ユーザー: 登録完了メッセージを表示
      else 登録失敗
        webサーバー -> ユーザー: 失敗メッセージを表示
      end
    end
      ユーザー -> webサーバー: ログイン
      webサーバー -> DBサーバー: ログイン照会
      DBサーバー -> DBサーバー: ログイン認証
      DBサーバー -> webサーバー: 認証結果
      activate ユーザー
      alt 認証成功
        webサーバー -> ユーザー: ログイン成功メッセージを表示
      else 認証失敗
        webサーバー -> ユーザー: ログイン失敗メッセージを表示
      end
     
     
    
    opt ログイン中
    
      alt ペットを登録したい場合
        ユーザー -> webサーバー: ペット登録
        webサーバー -> DBサーバー: ペット登録
        DBサーバー -> DBサーバー: 登録処理
        DBサーバー -> webサーバー: 登録結果
        webサーバー -> ユーザー: 登録完了メッセージ
      end
      
      ユーザー -> webサーバー: 検索（商品名）
      webサーバー -> DBサーバー: 検索処理（商品名）
      DBサーバー -> DBサーバー: 検索処理
      DBサーバー -> webサーバー: 検索結果
      webサーバー -> ユーザー: 検索結果
      
      alt 定期便対象商品かつ定期便を希望する場合
        ユーザー -> webサーバー: 定期便申し込み
        webサーバー -> DBサーバー: 定期便申し込み
        DBサーバー -> DBサーバー: 定期便登録処理
        DBサーバー -> webサーバー: 処理結果
        alt 登録成功
          webサーバー -> ユーザー: 登録完了メッセージを表示
        else
          webサーバー -> ユーザー: 登録失敗メッセージを表示
        end
      else
        ユーザー -> webサーバー: 商品をカートに入れる（商品名）
        webサーバー -> DBサーバー: 商品をカートに入れる（商品名）
        DBサーバー -> DBサーバー: カートに追加処理
        DBサーバー -> webサーバー: 処理結果
        webサーバー -> ユーザー: 処理結果
      
        ユーザー -> webサーバー: 購入（カート内の情報）
        webサーバー -> DBサーバー: 購入処理（カート内の情報）
        DBサーバー -> DBサーバー: 購入処理
        DBサーバー -> webサーバー: 処理結果
        alt 購入成功
          webサーバー -> ユーザー: 購入完了メッセージを表示
        else 購入失敗
          webサーバー -> ユーザー: 購入失敗メッセージを表示
       end
      end
      
      ユーザー -> webサーバー: ログアウト
      webサーバー -> DBサーバー: ログアウト照会
      DBサーバー -> DBサーバー: ログアウト処理
      DBサーバー -> webサーバー: ログアウト結果
      webサーバー -> ユーザー: ログアウト結果
    end
    
    deactivate ユーザー
    
  @enduml
```