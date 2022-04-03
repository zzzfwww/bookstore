## 生成api goctl 使用方式
```shell
 goctl api go -api *.api -dir ./  --style=goZero
```

## 生成rpc goctl使用方式
```shell
goctl rpc protoc *.proto --go_out=./ --go-grpc_out=./  --zrpc_out=./ --style=goZero
```
