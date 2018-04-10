---
title:  "Reference Material"
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
### Docker

Docker is the world's leading software containerization platform. 

Docker is the company driving the container movement and the only container platform provider to address every application across the hybrid cloud. Today’s businesses are under pressure to digitally transform but are constrained by existing applications and infrastructure while rationalizing an increasingly diverse portfolio of clouds, datacenters and application architectures. Docker enables true independence between applications and infrastructure and developers and IT ops to unlock their potential and creates a model for better collaboration and innovation.

```md
![Docker]({{ site.url }}{{ site.baseurl }}/assets/images/louis/docker01.png)
```
- [Docker 官网](https://www.docker.com/)
- [Docker 入门教程](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
- [Docker 微服务教程](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)
- [Docker 安装 (Ubuntu)](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

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

### Kubernetes
### Python
### CloudML
### TensorFlow
 
## 技术博客


