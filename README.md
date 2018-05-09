# QueryServer

<!-- TOC -->

- [QueryServer](#queryserver)
    - [1 概述](#1-概述)
    - [2 使用](#2-使用)
        - [2.1 安装依赖](#21-安装依赖)
        - [2.2 编译运行](#22-编译运行)
        - [2.3 版本发布](#23-版本发布)
    - [3 文档](#3-文档)
        - [3.1 项目文档](#31-项目文档)
        - [3.3 Todo List](#33-todo-list)
    - [4 依赖项目](#4-依赖项目)

<!-- /TOC -->

## 1 概述

|目录|说明|
|:--:|:--:|
|cmake|cmake脚本文件|
|docs|项目相关文档|
|scripts|项目相关的脚本|
|src|项目源码（按模块组织）|
|test|项目测试使用的脚本|

## 2 使用

### 2.1 安装依赖

```bash
# sudo apt-get install libopenblas-dev
# clone project
$ git clone https://bitbucket.org/bxq2011hust/queryserver.git queryServer
$ cd queryServer
```

### 2.2 编译运行

```bash
# require cmake3
$ mkdir build
$ cd build
$ cmake ..
$ make -j"$(nproc)"

# run
$ ./bin/queryServer

# test, cmake with -DBUILD_TEST=ON ..
$ make test
```

**PS:** 编译要求gcc版本4.9以上，当配置文件不存在时（首次运行），会使用默认的配置参数，并在当前目录下自动生成配置文件`config.json`

### 2.3 版本发布

- 修改版本号：修改最外层`CMakeLists.txt`文件中的`VERSION_MAJOR.VERSION_MINOR.VERSION_PATCH`值为相应版本号
- 合并分支：发起PR将当前分支合并到develop分支,测试通过后合并develop到master分支。
- 添加标签：以相应的版本号新建标签。

>**PS**:[版本号命名规则](https://semver.org/)

## 3 文档

### 3.1 项目文档

```bash
# 生成文档位于build/documents
$ make doc
```

1. [代码规范](docs/Code-Style.md)
1. [API说明](docs/API.md)
1. [配置说明](docs/config.md)
1. [12-Factor标准](https://12factor.net/zh_cn/)

### 3.3 Todo List

- [ ] GPU检索接口初步实现

## 4 依赖项目

- [`oktal/pistache`](https://github.com/oktal/pistache)
- [`boost`](http://www.boost.org/)
- [`nlohmann/json`](https://github.com/nlohmann/json)
- [`muflihun/easyloggingpp`](https://github.com/muflihun/easyloggingpp)