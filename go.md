# Go

## 语言安装

[下载地址](https://golang.org/dl/)

```shell
(workspace) ➜ curl -O https://dl.google.com/go/go1.11.5.darwin-amd64.tar.gz
# direnv 工作目录配置，shell脚本
(workspace) ➜ tar -zxvf go1.11.5.darwin-amd64.tar.gz
(workspace) ➜ mv go 1.11
(workspace) ➜ mkdir /usr/local/go
(workspace) ➜ mv 1.11 /usr/local/go
(workspace) ➜ mkdir /usr/local/go/1.11/userlib
```

## 沙盒环境

要构造一个好用的go沙盒环境要满足以上四点，只用direnv配合gopath、goroot、gobin即可

#### 编写配置

```shell
(workspace) ➜ cd WORKDIR
# direnv 工作目录配置，shell脚本
(workspace) ➜ cp weDevOps/go-envrc ./.envrc
(workspace) ➜ direnv allow .
(workspace) ➜ go version
```

#### 官方依赖手动安装

被墙了

```shell
# 例如安装grpc
(workspace) ➜ cd WORKDIR
(workspace) ➜ git clone https://github.com/grpc/grpc-go.git $GOPATH/src/google.golang.org/grpc
```

#### 第三方依赖手动安装

```shell
# 例如安装gorm mysql库
(workspace) ➜ cd WORKDIR
(workspace) ➜ go get -u github.com/jinzhu/gorm
```

#### 交叉编译

```shell
(workspace) ➜ cd WORKDIR
(workspace) ➜ cp weDevOps/build.sh ./
(workspace) ➜ ./build.sh linux
```

## 包管理

#### dep(1.10版本以前配合vendor)

```shell
(workspace) ➜ dep init
(workspace) ➜ dep update
(workspace) ➜ go build
```

#### go mod(1.11版本以后)

```shell
(workspace) ➜ go mod init
# direnv 工作目录配置，shell脚本
(workspace) ➜ go build
(workspace) ➜ go mod vendor
(workspace) ➜ go mod tidy
```

#### golang工作好工具

 - go run -race 竞态条件检查
 - go tool pprof 优化跟踪工具
 - github.com/nsf/gocode 自动补全程序
 - github.com/rogpeppe/godef 定义跳转和快速提示信息
 - github.com/lukehoban/go-find-references 搜索参考引用
 - github.com/lukehoban/go-outline 文件大纲
 - sourcegraph.com/sqs/goreturns 代码格式化
 - golang.org/x/tools/cmd/gorename 重命名
 - go-delve 调试代码 [mac安装教程](https://www.jianshu.com/p/cc4621d9c0aa)

# TODO

 - 搭建ss代理，可直接安装官方依赖
