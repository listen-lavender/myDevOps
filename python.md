# Python

## 沙盒环境

要构造一个好用的python沙盒环境要满足以上四点，只用direnv，需要更多的工作量，可以利用Pyenv和virtualenv辅助快速构建理想的沙盒环境

#### 安装

Mac安装
```shell
(workspace) ➜ brew install pyenv pyenv-virtualenv
```

Ubuntu安装
```shell
(workspace) ➜ curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
(workspace) ➜ git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
```

#### 激活命令

bash
```shell
(workspace) ➜ echo 'eval "$(pyenv init -)"'            >> ~/.bash_profile
(workspace) ➜ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
```

zsh
```shell
(workspace) ➜ echo 'eval "$(pyenv init -)"'            >> ~/.zshenv
(workspace) ➜ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshenv
```

```shell
# pyenv查看可安装的python版本
(workspace) ➜ pyenv install --list
# 2.5
# 2.7.10
# 3.6.8
# 3.7.2
# 3.8-dev
# activepython-2.7.14
# activepython-3.5.4
# activepython-3.6.0
# anaconda3-4.3.1
# ironpython-2.7.5
# jython-2.7.1
# micropython-1.9.4
# miniconda-3.16.0
# pypy-1.9
# pypy3.5-5.8.0
# stackless-2.7.14
```

#### 编写配置

```shell
(workspace) ➜ cd WORKDIR
# direnv 公共配置，shell脚本
(workspace) ➜ cp weDevOps/direnvrc ./.direnvrc
# direnv 工作目录配置，shell脚本
(workspace) ➜ cp weDevOps/pyenv-virturalenv-envrc ./.envrc
(workspace) ➜ direnv allow .
(workspace) ➜ pyenv version
(workspace) ➜ pip install -r requirements.txt
```

#### python工作好工具

 - bpython，更好用的解释器
 - python自省，help命令、dir命令、__version__属性、__file__属性
 - cProfile
 - cython

# TODO
