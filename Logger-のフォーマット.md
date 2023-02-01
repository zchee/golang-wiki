## フォーマット全般
### 必ず入っている情報
- `level` : ログレベル
- `time` : 時刻(JST)
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


## 出力例
### optionで int型の age, string型の name が入っている
```
{"level":"INFO","time":"2023-02-01T09:57:21+09:00","caller":"handler/pet.go:38","message":"pet log example","request_id":"6ebc1c29-96d0-48f5-93dc-2346c404a14a","uri":"/pets","method":"GET","age":1,"name":"hogehoge name"}
```

### log level error時
stack で スタックトレースが出る
```
{"level":"ERROR","time":"2023-02-01T10:00:30+09:00","caller":"middleware/recovery.go:36","message":"recovery","request_id":"a4feaba0-9bc1-4edf-a118-761f8588fee2","uri":"/users","method":"GET","error":"hoge hoge panic","stack":"github.dena.jp/ride/anyca-server/app/adapter/api/middleware.(*Middleware).Recovery.func1.1\n\t/anyca-server/app/adapter/api/middleware/recovery.go:36\nruntime.gopanic\n\t/usr/local/go/src/runtime/panic.go:890\ngithub.dena.jp/ride/anyca-server/app/adapter/api/middleware.(*Middleware).HandleTransaction.func1\n\t/anyca-server/app/adapter/api/middleware/transaction.go:20\ngithub.com/gin-gonic/gin.(*Context).Next\n\t/anyca-server/vendor/github.com/gin-gonic/gin/context.go:173\ngithub.dena.jp/ride/anyca-server/app/adapter/api/middleware.(*Middleware).HandleError.func1\n\t/anyca-server/app/adapter/api/middleware/error.go:16\ngithub.com/gin-gonic/gin.(*Context).Next\n\t/anyca-server/vendor/github.com/gin-gonic/gin/context.go:173\ngithub.dena.jp/ride/anyca-server/app/adapter/api/middleware.(*Middleware).Logger.func1\n\t/anyca-server/app/adapter/api/middleware/logger.go:18\ngithub.com/gin-gonic/gin.(*Context).Next\n\t/anyca-server/vendor/github.com/gin-gonic/gin/context.go:173\ngithub.com/gin-contrib/requestid.New.func2\n\t/anyca-server/vendor/github.com/gin-contrib/requestid/requestid.go:48\ngithub.com/gin-gonic/gin.(*Context).Next\n\t/anyca-server/vendor/github.com/gin-gonic/gin/context.go:173\ngithub.dena.jp/ride/anyca-server/app/adapter/api/middleware.(*Middleware).Recovery.func1\n\t/anyca-server/app/adapter/api/middleware/recovery.go:43\ngithub.com/gin-gonic/gin.(*Context).Next\n\t/anyca-server/vendor/github.com/gin-gonic/gin/context.go:173\ngithub.com/gin-gonic/gin.(*Engine).handleHTTPRequest\n\t/anyca-server/vendor/github.com/gin-gonic/gin/gin.go:616\ngithub.com/gin-gonic/gin.(*Engine).ServeHTTP\n\t/anyca-server/vendor/github.com/gin-gonic/gin/gin.go:572\nnet/http.serverHandler.ServeHTTP\n\t/usr/local/go/src/net/http/server.go:2947\nnet/http.(*conn).serve\n\t/usr/local/go/src/net/http/server.go:1991"}
```
