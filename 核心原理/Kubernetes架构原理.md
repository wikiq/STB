## Kubernetes主要由以下几个核心组件构成。

etcd保存了整个集群的状态。
Kube-apiserver提供了资源操作的唯一入口，并提供认证、授权、访问限制、API注册和发现等机制；
kube-controller-manager负责维护集群的状态，比如故障检测、自动扩展、滚动更新等；
kube-scheduler负责资源的调度，按照预订的调度策略将pod调度到相应的机器上。
kubelet负责维持容器的生命周期，同时也负责Volume（CVI）和网络（CNI）的管理。
Container runtime负责镜像管理以及Pod和容器的真正运行（CRI），默认的容器运行时为Docker；
kube-proxy负责为Service提供cluster内部的服务发现和负载均衡。