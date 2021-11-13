# 环境依赖
开发运行机器MacBook Pro 

使用三个依赖：mysql，etcd，redis

本地已安装mysql，etcd本地安装，redis使用docker启动

## install etcd and start
### ectd info
[etcd](./etcd.md)

## docker start redis
### Step 1:pull image
```shell 
docker pull redis:latest
```
### Step 2:  Launch the redis server instance
```shell 
docker run --name redis -p 6379:6379 -d redis
```


## benchmark
```shell
wrk -t10 -c1000 -d30s --latency "http://localhost:8888/check\?book\=go-zero"
```
![Benchmark](./image/bookstore-benchmark.png)


