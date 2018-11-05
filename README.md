# 发展
![avatar](https://mirror198829.github.io/static/docker/appdev.jpg)
![avatar](https://mirror198829.github.io/static/docker/appdev1.png)
# kubernetes
## 介绍
google出品，以Google Borg为原型，重新实现容器编排调度工具。
* 2014年开源
* 2015，谷歌将k8s捐赠给linux基金会下属原生计算基金会-CNCF
* 2017，战胜swarm和mesos，成为容器管理和调度编排领域的首选平台和事实标准
* 最终使命是成为新一代应用上云的首选平台，为广大开发者开启云原生应用的大门
* k8s将和人工智能、区块链等热门技术一起支撑互联网应用的未来
#### 容器编排管理平台
kubernets作为容器管理平台提供
* 以pod（容器组）为基本的编排和调度单元以及声明式的对象配置模型（控制器、configmap、secret等）
* 资源配额和分配管理
* 健康检查、自愈、伸缩与滚动升级
#### 微服务支撑平台
kubernets提供了对微服务的支撑
* 服务发现、服务编排与内部路由支持
* 服务快速部署和自动负载均衡
* 提供对“有状态”服务的支持等
#### 可移植的‘云平台’
提供
* 新一代应用云化的事实标准
* 为用户提供简单且一致的容器化应用部署、伸缩和管理机制，形成新的、通用的应用云化模型
* 云厂商锁定的问题得以解决，云应用支持跨云迁移
#### 为什么选择K8S
从生态圈的角度：
* Google的业内最成熟的容器编排管理经验的输出
* 2017年战胜Docker Swarm和apache mesos，成为云原生应用唯一值得绑定的容器编排管理平台
* 传统云平台提供商的全面支持。
从云应用的角度：
* 容器管理、调度和编排的事实标准
* 先进的workload管理之经验模型：pod和controllers
* 原生支持微服务抽象：服务注册、服务发现和自动负载均衡

## kubernetes架构与组件
#### 架构全图
![avatar](https://mirror198829.github.io/static/docker/k1.png)
# grafana + prometheus
### prometheus
参考文档：https://blog.xizhibei.me/2017/08/06/monitoring-with-prometheus/
* 时间序列数据库（时序性数据库），
* 灵活的查询语言
* 通过`拉`的方式采集数据  
—————— 采集数据的两个去向  
1.报警（alertManager）——报警分组、报警抑制、报警静默   
2.可视化：prometheus放弃了自己的promDash可视化工具。专注于数据采集与分析

#### 为什么要用grafana+prometheus？？
时间越长，关系型数据库的数据量越大，导致查询缓慢，同时编写这部分统计代码。使用prometheus可以不用绘图逻辑。需要把统计的数据按固定格式传递。
#### prometheus如何采集到数据并自动监控呢？
例如paas，是通过promtheus采集k8s库的数据，采集了自己存储起来，对外暴露指标 ，grafana就根据这些指标进行统计
### grafana的基本概念
1.datasource
  数据的存储源（Graphite、InfluxDB、OpenTSDB、Prometheus、Elasticsearch、CloudWatch）
2.dashboard
  row的集合
3.row
  panel的集合（一行有12个单元）
4.panel
  最小的可视化单位，支持多种数据的展示方式，table，graph
5.playlist
  dashboard的集合，当控制台数量太多时，用来快速在目标群中切换
6.Query Editor 查询编辑器
# openshift
红帽出品（IBM），基于容器化技术和google的k8s技术之上加固的商业技术。  
> docker容器管理的要求：

|要求|含义|
|---|---|
|调度|我的容器该在哪里运行|
|生命周期管理和健康检查|如何保证容器可以在不同环境下都正常运行|
|服务发现|我的容器现在正在哪里运行？提供哪些服务|
|监控|我的容器发生了什么|
|认证授权|谁可以对我的容器做哪些事情|
|聚合|如何管理由多个容器组成的服务|
|扩展性|动态的调整容器的规模|

> kubernets提供的功能  

调度、容器健康、服务发现、监控、认证授权、自动扩展、自愈、持久化接口

> openshift补充和增强  

* 提供网络支持
* 提供镜像仓库（私有镜像仓库与云平台结合，镜像仓库的多租户功能）
* 提供监控和日志
* 提供部署模型，如A/B、蓝绿部署
* 提供应用生命周期管理
* 提供如数据库、消息服务器等服务
* 提供自服务门户
