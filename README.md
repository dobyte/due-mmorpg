## due高性能分布式游戏服务器实验探索案例-MMORPG

### 一、项目介绍

本项目属于《due高性能分布式游戏服务器开发》项目的实验探索项目。旨在通过本项目从0到1的构建为广大MMORPG游戏开发爱好者提供一个完全开源、免费的交流学习平台。本项目属于学习实验性质项目，版权归全体源码贡献者所有，任何组织或个人不得将本项目源码用于其他任何商业项目或商业行为中。

### 二、项目目标

* 帮助初学者能够快速入门和掌握due框架的应用和开发
* 帮助MMO游戏爱好者全方位了解和掌握MMO服务器的开发流程
* 拓展框架的应用场景、完善框架功能、提升框架性能和稳定性
* 提升框架社区活跃度、完善社区生态、推动框架项目良性发展

### 三、开发交流

<img title="due游戏服务器框架交流群" src="group_qrcode.jpeg" alt="due游戏服务器框架交流群" width="177">
<img title="个人二维码" src="personal_qrcode.jpeg" alt="个人二维码" width="177">

欢迎广大游戏开发爱好者加入共同学习进步。

### 三、开发环境

由于本项目属于全体网友共建项目，为了保证项目代码的一致性，避免出现各种各种奇怪的问题，这里对项目的开发环境做一些硬性规定：

* 开发语言: go v1.23.0+
* 开发框架: due v2.2.6+
* 开发工具: goland、vs code
* 开发平台: windows、mac、linux
* 其他环境: docker
* 参考案例：https://github.com/fuyouawa/MMORPG

### 五、集群架构

### 六、快速开始

#### 1.安装docker

进入[docker](https://www.docker.com/)官网下载最新版[docker](https://www.docker.com/)安装包安装

#### 2.安装开发组件

```shell
$ cd ./docker
$ docker-compose up -d
```

#### 3.安装protobuf编译器

- Linux, using apt or apt-get, for example:

```shell
$ apt install -y protobuf-compiler
$ protoc --version  # Ensure compiler version is 3+
```

- MacOS, using Homebrew:

```shell
$ brew install protobuf
$ protoc --version  # Ensure compiler version is 3+
```

- Windows, download from [Github](https://github.com/protocolbuffers/protobuf/releases):

#### 4.安装due-cli开发工具包

```shell
$ go install github.com/dobyte/due-cli@latest
```

#### 5.安装开发工具链

```shell
# 安装grpc开发工具集
$ due-cli install grpc

# 安装gorm dao文件生成器
$ due-cli install gorm

# 安装protobuf开发工具集
$ due-cli install proto
```

### 七、目录结构

```shell
docker/           # 开发组件docker快速构建
gate/             # 网关服（ws实现）
internal/         # 内部共享代码块
  code/           # 统一错误码
  component/      # 公共组件（单例）
  config/         # 配置数据解析、监听模块
  constraint/     # 公共约束函数
  dao/            # mysql数据库操作类（由gorm-dao-generator工具生成）
  define/         # 公共常量定义
  event/          # 事件总线发布、订阅
  http/           # http模块函数
  middleware/     # 逻辑服中间件
  model/          # mysql数据模型定义（通过定义的模型生成dao操作类）
  protocol/       # 客户端与服务器间的通信协议定义
  service/        # 微服务调用客户端、逻辑模块
  share/          # 服务器集群公共数据、配置、资源
  utils/          # 公共工具函数库
mesh/             # 微服务集群
web/              # Web服（http实现）
```