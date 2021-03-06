# 容器管理面板简介

## 应用治理

* **应用跨机编排**：结合 Docker 最新的集群功能，对应用，服务，任务与容器间逻辑关系进行了全新阐述；一个 Stack 文件即可驱动整个应用的跨主机编排，并保证应用内服务的自动发现；JSON文件、向导表单、应用目录、命令行工具多种应用下发模式，满足初中高级不同用户群体，只需输入两个关键字就可下发一个应用

* **服务滚动更新**：可以控制在固定时间内的并行更新任务数，避免更新峰值影响集群吞吐；提供了服务 Docker 镜像更新的 webhook，可以与上游的镜像构建对接来触发镜像更新的回调；利用命令行工具触发版本回滚，开发者友好；未来会提供完整的版本管理，让用户能够随意选择旧版本回滚

* **任务按需伸缩**：运行中的服务可以随时进行扩容缩容，增减任务个数，满足业务要求；并且可以为每一个任务设置CPU内存的资源跨度，保证全局的资源隔离

* **服务全局容错**：用户不仅可以配置任务的失败重启策略来达到服务容错，而且通过设置任务的重启间隔，在固定时间窗口内的重启次数，来避免异常任务的频繁调度，消耗集群资源。保证集群的整体稳定性

* **多机负载均衡**：集群中的每个节点都可以将流量分摊、引导至服务的每个任务，不仅提高了服务的可用性和吞吐量，而且消除了负载均衡单点。落地过程中，用户可以使用前置的 F5 硬负载对接部分甚至整个后端集群的主机

* **多种分发模式**：固定任务数与一主机一任务模式，结合长时(long-running)任务，批处理任务，定时任务可以实现多种任务分发组合，满足不同应用场景
 
## 镜像管控

* **应用目录**：应用目录可以帮助企业用户打造企业内部的镜像市场，一键下发公共应用，提高运维效率

* **私有镜像**：私有镜像功能实现了用户管理与镜像管控的闭环，通过对接企业内部用户系统，用户可以使用内部的账号/密码无缝推送(docker push)镜像到私有镜像仓库，拉取(docker pull)亦然

* **公有镜像**：结合用户管理功能，你可以将自己的镜像公开供他人使用，达到资源共享
 
## 集群运维

* **主机管理**：可以查看集群内各个主机的配置、状态；可以随时快速添加主机；可以一键将某主机上的任务调度至其它机器以停服维护该主机；可以为主机打标签来配合任务调度，或者以此划分生产、测试环境

* **虚拟网络**：内置 overlay 网络实现应用网络隔离和独立的网络规划能力，也可以利用 Docker 的网络插件功能无缝对接多种 overlay 网络方案

* **webssh**：用户可以利用 webssh 进入容器内部进行操作，无需从终端侵入主机，同时结合用户管理限制用户进入他人的容器内部，张弛有度

* **实时监控**：容器级别的CPU，内存，网络IO监控；服务级别的CPU，内存，网络IO汇聚监控。用户能够从全局和底层单元多角度监控主机和服务的运行状况

* **实时日志**：容器级别的实时日志收集；服务级别的实时日志收集。另外，日志中的关键词如 Error, Warning 会高亮显示

## 仓库认证

* **镜像仓库的认证管理**：用户可以管理自己多个镜像仓库的认证信息。在发布应用时，可以利用认证信息拉取相应仓库的镜像到集群中进行部署


## 轻量化设计

* **安装便捷**：十分钟，零基础搞定安装

* **插件化架构**：不仅可以利用 docker 特性灵活插拔存储与网络驱动，还可按需启停用户管理，镜像管理等功能，甚至可以对接不同的账户系统。未来会有更多插件释出

* **对接上下游**：提供服务更新的 webhook 对接上游镜像构建；提供服务入口列表对接外部硬负载；提供 LDAP 集成对接企业帐户系统；提供任务扩缩接口对接外部触发器

* **开发接口**：提供命令行工具和 API 接口，便于二次开发，无缝对接企业内部运维流程
