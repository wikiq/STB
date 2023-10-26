## Kubernetes主要由以下几个核心组件构成。

- etcd保存了整个集群的状态。
- Kube-apiserver提供了资源操作的唯一入口，并提供认证、授权、访问限制、API注册和发现等机制；
- kube-controller-manager负责维护集群的状态，比如故障检测、自动扩展、滚动更新等；
- kube-scheduler负责资源的调度，按照预订的调度策略将pod调度到相应的机器上。
- kubelet负责维持容器的生命周期，同时也负责Volume（CVI）和网络（CNI）的管理。
- Container runtime负责镜像管理以及Pod和容器的真正运行（CRI），默认的容器运行时为Docker；
- kube-proxy负责为Service提供cluster内部的服务发现和负载均衡。

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-0ee8bceb43ee5ff3d8aa9545d5889340b82202bc%2Farchitecture%20(5).png?alt=media)

## 除了核心组件，还有一些推荐的Add-ons：

- kube-dns负责为整个集群提供DNS服务。
- ingress controller 为服务提供外网入口
- Heapster 提供资源监控
- Dashboard 提供GUI
- Federation 提供跨可用区的集群
- Fluentd-elasticsearch 提供集群日志采集、存储与查询

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-b2bcdccbc97b9d0698a5c772eff342380536f1fa%2Fcomponents%20(6).png?alt=media)

## 分层架构

Kubernetes设计理念和功能其实就是一个类似Linux的分层架构，如下图所示：

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-a5b00a4ed34f26eb6f2d560c08ec5ff37d7c6b7e%2F14937095836427%20(4).jpg?alt=media)

- 核心层：Kubernetes 最核心的功能，对外提供 API 构建高层的应用，对内提供插件式应用执行环境
- 应用层：部署（无状态应用、有状态应用、批处理任务、集群应用等）和路由（服务发现、DNS 解析等）
- 管理层：系统度量（如基础设施、容器和网络的度量），自动化（如自动扩展、动态 Provision 等）以及策略管理（RBAC、Quota、PSP、NetworkPolicy 等）
- 接口层：kubectl 命令行工具、客户端 SDK 以及集群联邦
- 生态系统：在接口层之上的庞大容器集群管理调度的生态系统，可以划分为两个范畴
  - Kubernetes 外部：日志、监控、配置管理、CI、CD、Workflow、FaaS、OTS 应用、ChatOps 
  - Kubernetes 内部：CRI、CNI、CVI、镜像仓库、Cloud Provider、集群自身的配置和管理等

## 核心组件

### 核心组件

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-e79e660e4e46d70805f3de0902fbb373e87cf506%2Fcore-packages.png?alt=media)

### 核心 API

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-f3f84293ded3ae6dc5c13c99d6f0d5496e391332%2Fcore-apis%20(4).png?alt=media)

### 生态系统

![img](https://4130827217-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LDAOok5ngY4pc1lEDes-887967055%2Fuploads%2Fgit-blob-923672fb5524e8b6e345b864e82844f8ede8deba%2Fcore-ecosystem%20(3).png?alt=media)

关于分层架构，可以关注下 Kubernetes 社区正在推进的 [Kubernetes architectural roadmap](https://github.com/kubernetes/community/tree/master/sig-architecture)。