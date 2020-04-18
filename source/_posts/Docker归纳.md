title: Docker归纳
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:

  - 容器
  - docker
  - image
  - container
  - swarm
  - k8s
categories:
  - docker
date: 2019-03-05 10:09:00

---

学习和使用docker已经有一段时间了，可是一直没有时间进行归纳总结；

想来最近项目稍闲，所以赶紧整理一下之前学到，并运用的一些docker知识，并作为后面自己的知识库进行运用；

### Docker的来由

任何的软件由来，都是由一个需求而得来的，如果这个需求是个特别痛点的需求，那么解决这个需求的软件就会发展得很好；

那么docker究竟解决了用户什么样的痛点需求呢？

> Docker 的出现一定是因为目前的后端在开发和运维阶段确实需要一种虚拟化技术解决开发环境和生产环境环境一致的问题。
>
> 通过 Docker 我们可以将程序运行的环境也纳入到版本控制中，排除因为环境造成不同运行结果的可能。

但是上述需求虽然推动了虚拟化技术的产生，但是如果没有合适的底层技术支撑，那么我们仍然得不到一个完美的产品。

因为之前学过了部分的Docker知识，但是一段时间不使用，有点生疏了，所以特地记录到博客中，至于刚才所说的Docker的一些核心技术和实现原理，留待后面进行分析了；

### Dockerfile

#### 简介

Dockerfile是由一系列命令和参数构成的脚本，**这些命令应用于基础镜像并最终创建一个新的镜像。**

**它们简化了从头到尾的流程并极大的简化了部署工作。**

Dockerfile从FROM命令开始，紧接着跟随者各种方法，命令和参数。其产出为一个新的可以用于创建容器的镜像。

**Dockerfile语法由两部分构成，注释和命令+参数**

#### Dockerfile命令

Dockerfile有十几条命令可用于构建镜像，下文将简略介绍这些命令。



##### ADD

ADD命令有两个参数，源和目标。它的基本作用是从源系统的文件系统上复制文件到目标容器的文件系统。如果源是一个URL，那该URL的内容将被下载并复制到容器中。

```powershell
Usage: ADD [source directory or URL] [destination directory]
ADD /my_app_folder /my_app_folder
```

