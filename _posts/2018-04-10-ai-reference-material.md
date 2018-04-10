---
title:  "AI Reference Material"
last_modified_at: 2018-04-10T17:30:16-04:00
author: Louis
header:
  image: /assets/images/alab-header.jpg
categories: 
  - ALab
tags:
  - ALab
  - Study
toc: true
toc_label: "Reference Material"
---
# 人工智能技术参考资料

本材料包含利用人工智能技术来打造创新型产品的过程中所涉及到的各种技术，包括各种人工智能算法、大数据技术和将算法落地的各种工程技术。欢迎补充。

## 大数据相关
### Hadoop
### Spark
### Impala
### MongoDB

## 人工智能算法相关

### 机器学习
### 深度学习
### 图像
### NLP
### 强化学习

## 工具相关

要将人工智能算法真正落地，解决实际的业务问题，必须依赖工程技术，下面介绍常用的工程技术工具。

### Docker

Docker is the world's leading software containerization platform. 

![Docker]({{ site.url }}{{ site.baseurl }}/assets/images/louis/docker01.png)

- [Docker 官网](https://www.docker.com/)
- [Docker 入门教程](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
- [Docker 微服务教程](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)
- [Docker 安装 (Ubuntu)](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- [Docker Hub](https://hub.docker.com)

#### 更改image仓库的镜像网址

推荐使用国内的官方镜像：registry.docker-cn.com，修改方式如下：

1. 打开/etc/default/docker文件（需要sudo 权限），在文件底部加上一行：

```
DOCKER_OPTS="--registry-mirror=https://registry.docker-cn.com"
```

2. 修改文件：/etc/docker/daemon.json，内容为：

```
{
    "graph": "/mnt/docker-data",
    "registry-mirrors":["https://registry.docker-cn.com"]
}
```
3. 然后，重启Docker服务：

```
$ sudo service docker restart
```
#### Docker 常用命令

```
$ docker version
$ docker info
$ sudo usermod -aG docker $USER
$ sudo service docker start
$ sudo systemctl start docker

# image 文件,image 是二进制文件。实际开发中，一个 image 文件往往通过继承另一个 image 文件，加上一些个性化设置而生成
$ docker image ls
$ docker image rm [imageName]
$ docker image pull library/hello-world

# library 是image文件所在的组，由于Docker官方提供的image文件，都放在library组里面，所以它是默认组，可以省略
$ docker image pull hello-world

# 运行image文件
$ docker container run hello-world
$ docker container run -it ubuntu bash
$ docker container kill [containID]

# 容器文件
# image文件生成的容器实例，本身也是一个文件，称为容器文件。而且关闭容器，并不会删除容器文件，只是容器停止运行而已。

$ docker container ls
$ docker container ls -all
$ docker container rm [containerID]

# Dockerfile文件
# 这是一个文本文件，用来配置image，Docker根据dockerfile来生成二进制的image文件
# .dockerignore 文本文件，表示不要打包进入image文件
# 在项目的根目录下，新建Dockerfile

FROM node:8.4
COPY . /app
WORKDIR /app
RUN npm install --registry=https://registry.npm.taobao.org
EXPOSE 3000

# 创建image文件
# -t 用来指定image文件的名字，后面冒号指定标签
# 指定Dockerfile文件所在的目录的路径

$ docker image build -t koa-demo:0.0.1 .

# 生成容器
# -it参数表示容器的Shell映射到当前的Shell
# -p参数表示端口映射
# --rm 参数表示容器终止运行后自动删除容器文件

$ docker container run --rm -p 8000:3000 -it koa-demo /bin/bash

# CMD命令
# 写到Dockerfile文件里面的CMD命令，表示在容器启动以后，自动执行CMD命令
# RUN与CMD的区别：RUN命令在image文件的构建阶段执行，执行结果都会打包进入image文件；CMD命令则是在容器启动后执行；一个Dockerfile可以包含多个RUN，但是只能有一个CMD命令
# docker container run命令后的附件命令会覆盖CMD命令

# 发布image文件
# hub.docker.com，cloud.docker.com
$ docker login
# 为本地的image标注用户名和版本
$ docker image tag [imageName] [username]/[repository]:[tag]
$ docker image tag koa-demos:0.0.1 ruanyf/koa-demos:0.0.1
# 构建image文件
$ docker image build -t [username]/[repository]:[tag]
# 发布image文件
$ docker image push [username]/[repository]:[tag]

# 提交一个新的image，commit，用于通过差异性，创建一个新的image
$ docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]
-a, --author="" #作者
-m, --message="" # Commit message
-p, --pause=true # Pause container during commit

# 其他有用的命令
$ docker container start [containerID]
$ docker container stop [containerID]
$ docker container logs [containerID]
$ docker container exec -it [containerID] /bin/bash # 用于进入一个正在运行的docker容器
$ docker container cp [containerID]:[/path/to/file] # 从正在运行的Docker容器里面，将文件拷贝至本地

```
### Kubernetes
### Python
### CloudML

CloudML是小米提供的小米云深度学习服务，开发者可以在云端使用GPU训练模型，也可以一键部署模型服务。

- [CloudML文档](http://docs.api.xiaomi.com/cloud-ml/)
- [小米生态云深度学习服务器配置流程](http://192.168.0.150:8080/xwiki/bin/view/ALAB/%E5%B0%8F%E7%B1%B3%E7%94%9F%E6%80%81%E4%BA%91%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE%E6%B5%81%E7%A8%8B)
- [小米陈迪豪：TensorFlow 与深度学习平台实践](https://www.ctolib.com/topics-56412.html)
- [视觉是小米AI服务平台的未来](https://mp.weixin.qq.com/s/v8UkFOKYGZzyoyZ0WbtZFw)
- [AI平台服务 - 解智]({{ site.url }}{{ site.baseurl }}/assets/files/louis/cloudml-jiezhi-ai-platform-service.pdf)
- [深度学习云服务介绍 - 陈迪豪]({{ site.url }}{{ site.baseurl }}/assets/files/louis/cloudml-tobe-deep-learning-cloud-service-introduction.pdf)

### TensorFlow

![tensorflow]({{ site.url }}{{ site.baseurl }}/assets/images/louis/tensorflow01.jpg)

- [TensorFlow 官网](https://www.tensorflow.org/)
- [TensorFlow 机器学习速成课程](https://developers.google.com/machine-learning/crash-course/)


#### TensorFlow Serving

TensorFlow Serving 是一个用于提供机器学习模型服务的高性能开源库。它可以将训练好的机器学习模型部署到线上，使用 gRPC 作为接口接受外部调用，它支持模型热更新与自动模型版本管理。

- [TensorFlow Serving](https://www.tensorflow.org/serving/)
- [TensorFlow Serving Github](https://github.com/tensorflow/serving)
- [TensorFlow Serving Install Instructions](https://github.com/tensorflow/serving/blob/master/tensorflow_serving/g3doc/setup.md)
- [TensorFlow Serving Basic Tutorial](https://github.com/tensorflow/serving/blob/master/tensorflow_serving/g3doc/serving_basic.md)
- [how to deploy machine learning models with tensorflow - 1](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-1-make-your-model-ready-for-serving-776a14ec3198)
- [how to deploy machine learning models with tensorflow - 2](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-2-containerize-it-db0ad7ca35a7)
- [how to deploy machine learning models with tensorflow - 3](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-3-into-the-cloud-7115ff774bb6)

**安装时可能会遇到的问题**

在虚拟机ubuntu 16.04上面安装tensorflow serving的时候，安装好之后可能会出现错误，可用下面方法来解决：

[https://github.com/tensorflow/serving/issues/819](https://github.com/tensorflow/serving/issues/819)

```sh
$ apt-get install -y software-properties-common
$ add-apt-repository ppa:ubuntu-toolchain-r/test -y
```
```sh
$ apt-get update
$ apt-get upgrade
$ apt-get dist-upgrade
```
**TensorFlow SavedModel**

TensorFlow Serving所用的模型格式是SavedModel，需要理解SavedModel。

- [理解SavedModel](https://blog.csdn.net/thriving_fcl/article/details/75213361)
- [推荐一种TensorFlow模型格式](https://zhuanlan.zhihu.com/p/34471266?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)
- [TensorFlow SavedModel README](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/python/saved_model/README.md)
- [SignatureDef README](https://github.com/tensorflow/serving/blob/master/tensorflow_serving/g3doc/signature_defs.md)

 

## 技术博客


