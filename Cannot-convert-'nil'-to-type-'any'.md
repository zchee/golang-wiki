When I use go1.18 to compile my project

```go
err := recover()
if err != nil{
    .....
}
```
will throw an exception:`Cannot convert 'nil' to type 'any'`

How can i fix it in go1.18?