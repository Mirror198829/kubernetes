# docker
## 简介
docker：开源项目，它可以将任何应用以轻量级的形式打包、发布、运行  
可以粗糙的理解为轻量级的虚拟机。开挂的chroot  
Docker与传统虚拟化方式不同在于，只在操作系统层实现虚拟化，只虚拟操作系统而不虚拟内核。
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
# kubernetes
google出品
