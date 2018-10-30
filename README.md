# 发展
![avatar](https://mirror198829.github.io/static/docker/appdev.jpg)
![avatar](https://mirror198829.github.io/static/docker/appdev1.png)
# docker
## 简介
`docker`：2013年横空出现。  
以Docker为代表的内核容器技术不是新技术，而是将已有技术（LXC,cgroups,Union FS）进行了更好的包装和整合，并形成了一种标准镜像格式。   
开源项目，它可以将任何应用以轻量级的形式打包、发布、运行  
可以粗糙的理解为轻量级的虚拟机。开挂的chroot。 
Docker与传统虚拟化方式不同在于，只在操作系统层实现虚拟化，只虚拟操作系统而不虚拟内核。  
Docker是什么呢，白话点说，就是一个Container的管理工具。  
计算机基本单元由虚拟机变为了容器，越来越多应用的构建、部署与运行选择在容器中进行。

|特性|容器|虚拟机|
|---|---|---|
|启动|秒级|分钟级|
|硬盘使用|MB-GB|GB|
|性能|接近原生|小于原生|
|系统支持量|单机支持上千个容器|一般几十个|  
## 术语
|en|中文|作用|
|---|---|---|
|host|宿主机|正在使用的电脑|
|image|镜像|本地建的或者远端拉去的重复使用的软件打包|
|container|容器|镜像运行实际|
|registry|仓库|存储很多镜像的仓库|
|daemoon|守护程序|用来接收用户命令，和registry共享|
|client|客户端|给daemon输送命令|
## docker命令
|命令|用途|
|---|---|
|docker pull|获取image|
|docker build|创建image|
|docker images|列出image|
|docker run|运行container|
|docker ps|列出container|
|docker rm|删除container|
|docker rmi|删除image|
|docker cp|在host和container之间拷贝文件|
|docker commit|保存改动为新的image|
## dockerfile
类似配置文件，通过dockerfile可以构建一个image
#### dockerfile语法
|命令|用途|
|---|---|
|FROM|base image|
|RUN|执行命令|
|ADD|添加文件|
|COPY|拷贝文件|
|CMD|执行命令|
|EXPOSE|暴露端口|
|WORKDIR|指定路径|
|MAINTAINER|维护者|
|ENV|设定环境变量|
|ENTRYPOINT|容器入口|
|USER|指定用户|
|VOLUME|mount point|
#### 镜像分层
Dockerfile中每一行都产生一个新层。
``` javascript
FROM alpine:latest  4e38e38c8ce0
MAINTAINER xbf  fb1aabf4427b
CMD echo 'hello docker' 3df065bgdff6
```
镜像分层的好处是当多个dockerfile中有5个镜像分层相同时变可以减少压力
## Volume
提供独立于容器之外的持久化存储
## Registry
镜像仓库
## docker-compose
多容器app
## 理解资料
https://segmentfault.com/a/1190000008557309
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

# openshift
红帽出品，基于容器化技术和google的k8s技术之上加固的商业技术。  
docker容器管理的要求：

|要求|含义|
|---|---|
|调度|我的容器该在哪里运行|
|生命周期管理和健康检查|如何保证容器可以在不同环境下都正常运行|
|服务发现|我的容器现在正在哪里运行？提供哪些服务|
|监控|我的容器发生了什么|
|认证授权|谁可以对我的容器做哪些事情|
|聚合|如何管理由多个容器组成的服务|
|扩展性|动态的调整容器的规模|

