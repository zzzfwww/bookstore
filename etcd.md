## 安装etcd

### 从github官网下载etcd

```shell
ETCD_VER=v3.5.1

# choose either URL
GOOGLE_URL=https://storage.googleapis.com/etcd
GITHUB_URL=https://github.com/etcd-io/etcd/releases/download
DOWNLOAD_URL=${GOOGLE_URL}

rm -f /tmp/etcd-${ETCD_VER}-darwin-amd64.zip
rm -rf /tmp/etcd-download-test && mkdir -p /tmp/etcd-download-test

curl -L ${DOWNLOAD_URL}/${ETCD_VER}/etcd-${ETCD_VER}-darwin-amd64.zip -o /tmp/etcd-${ETCD_VER}-darwin-amd64.zip
unzip /tmp/etcd-${ETCD_VER}-darwin-amd64.zip -d /tmp && rm -f /tmp/etcd-${ETCD_VER}-darwin-amd64.zip
mv /tmp/etcd-${ETCD_VER}-darwin-amd64/* /tmp/etcd-download-test && rm -rf mv /tmp/etcd-${ETCD_VER}-darwin-amd64

/tmp/etcd-download-test/etcd --version
/tmp/etcd-download-test/etcdctl version
/tmp/etcd-download-test/etcdutl version
```

### 拷贝可执行文件到执行目录 启动etcd服务
```shell
cp /tmp/etcd-download-test/etcd* ~/etcd
~/etcd &
```

### etcd 常用命令
查询所有的keys，或者以某个前缀的keys
```shell
etcdctl get --prefix ""
etcdctl get --prefix "/my-prefix"
```
只列出keys，不显示值
```shell
etcdctl get --prefix --keys-only ""
etcdctl get --prefix --keys-only "/my-prefix"
```
