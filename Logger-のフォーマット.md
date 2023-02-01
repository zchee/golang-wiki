### 必ず入っている情報
- `level` : ログレベル
- `time` : 時刻
- `caller` : ログ呼び出し箇所
- `message` : logメッセージ
- `request_id` : requestごとに一意なID
- `uri` : リクエストのアクセス先
- `method` : リクエストのメソッド
- `ip` : アクセス元のIP
- `user_agent` : アクセス元のUserAgent

## Errorの時のみ入っている
- `stack` : スタックトレース


### オプション
- `xxx: yyy` : 任意の組み合わせのキー・バリュー（share_id: 100, car_id: 200など）。幾つでも追加可能



```
{"level":"INFO","time":"2023-02-01T09:42:08+09:00","caller":"middleware/logger.go:12","message":"request","request_id":"66aeea69-2db1-4210-ba31-3ce01d13093e","uri":"/users","method":"GET","ip":"172.26.0.1","user_agent":"curl/7.79.1"}
```