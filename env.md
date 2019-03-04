# 应用隔离利器 direnv

由于开发语言、第三方依赖库的各种版本，工作中经常要为一个应用创建一套隔离的运行环境，使用当前应用指定的语言和依赖库版本，称之为沙盒环境

#### 解决痛点：

 1. 开发语言多版本
 2. 支持独立的第三方库版本
 3. 因为开发语言版本会共用，所以某些官方库或者兼容性好的大依赖库，需要支持共用，节省安装时间
 4. 配置一次，使用无感知

python开发者，有Pyenv和virtualenv沙盒工具，pyenv支持了1、3，virturalenv支持了2、3，那么还有更好用的工具吗？direnv能够支持以上4点。

#### 安装

Mac安装
```shell
(workspace) ➜ brew install direnv
```

Ubuntu安装
```shell
(workspace) ➜ apt-get install direnv
```

#### 激活命令

bash
```shell
(workspace) ➜ echo 'eval "$(direnv hook bash)"'        >> ~/.bashrc
```

zsh
```shell
(workspace) ➜ echo 'eval "$(direnv hook zsh)"'         >> ~/.zshrc
```
#### 工作目录配置

```shell
# 公共配置
(workspace) ➜ vi ~/.direnvrc
(workspace) ➜ cd WORKDIR
# 编写目录载入载出的配置文件，支持shell脚本
(workspace) ➜ vi .envrc
(workspace) ➜ direnv allow
(workspace) ➜ cd ..
# 进入工作目录，执行load环境过程
(workspace) ➜ cd WORKDIR
# 退出工作目录，执行unload环境过程
(workspace) ➜ cd ..
```

#### 多环境使用env文档

[direnv wiki](https://github.com/direnv/direnv/wiki/)

# TODO

 - 终极隔离利器 docker