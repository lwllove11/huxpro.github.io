---
layout:     post
title:      "SpringBoot 整合 Elasticsearch"
subtitle:   " \"springboot, elasticsearch\""
date:       2018-11-21 12:00:00
author:     "GuangWu"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - SpringBoot
    - Meta
---

> “Yeah It's on. ”


## 前言

### Elasticsearch简介:</br>
ElasticSearch是一个基于Lucene的搜索服务器。它提供了一个分布式多用户能力的全文搜索引擎，基于RESTful web接口。Elasticsearch是用Java开发的，并作为Apache许可条款下的开放源码发布，是当前流行的企业级搜索引擎。设计用于云计算中，能够达到实时搜索，稳定，可靠，快速，安装使用方便。
我们建立一个网站或应用程序，并要添加搜索功能，但是想要完成搜索工作的创建是非常困难的。我们希望搜索解决方案要运行速度快，我们希望能有一个零配置和一个完全免费的搜索模式，我们希望能够简单地使用JSON通过HTTP来索引数据，我们希望我们的搜索服务器始终可用，我们希望能够从一台开始并扩展到数百台，我们要实时搜索，我们要简单的多租户，我们希望建立一个云的解决方案。因此我们利用Elasticsearch来解决所有这些问题及可能出现的更多其它问题。

[直接看技术实现](#build) 



<p id = "build"></p>
---

## 正文

### Elasticsearch部署安装
#### 环境和包的版本
- centos7.2
- elasticsearch-5.5.1.zip
- elasticsearch-head-master.zip
- node-v8.12.0-linux-x64.tar.xz
- JDK1.8(自己安装)

#### Elasticsearch命令
- 前台运行:bin/elasticsearch
- 前台停止:ctrl+c
- 后台运行:bin/elasticsearch -d
- 后台停止:jps:kill -9 xxxx
#### Elasticsearch 安装
##### 建立一个elas用户
1. adduser elas
2. passwd elas
3. chown -R elas /root
4. su elas
##### 使用elas启动Elasticsearch
1. wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.5.1.zip
2. unzip elasticsearch-5.5.1.zip
3. cd elasticsearch-5.5.1/
4.修改config/elasticsearch.yml,增加一行:network.host: 0.0.0.0 
5. su elas
6. 启动命令:bin/elasticsearch

#### 安装elasticsearch-head
1. 下载head插件:https://github.com/mobz/elasticsearch-head
2. 解压到任意目录:unzip elasticsearch-head-master.zip
3. 安装nodejs
4. 进入nodejs目录执行命令：npm install -g grunt-cli，将grunt安装为全局命令。
5. 到head目录下下载包，执行命令：npm install
6. 到head插件目录，运行grunt server，启动head。连接9100端口
7. 修改elasticsearch配置文件：elasticsearch.yml，增加以下两句命令：http.cors.enabled: true http.cors.allow-origin: "*"
8. 访问http://localhost:9100/，即可看到head效果



## 后记

回顾这个博客的诞生，纯粹是出于个人兴趣。在知乎相关问题上回答并获得一定的 star 后，我决定把这个博客主题当作一个小小的开源项目来维护。

在经历 v1.0 - v1.5 的蜕变后，这个博客主题愈发完整，不但增加了诸多 UI 层的优化（opinionated）；在代码层面，更加丰富的配置项也使得这个主题拥有了更好的灵活性与可拓展性。而作为一个开源项目，我也积极的为其完善文档与解决 issue。

如果你恰好逛到了这里，希望你也能喜欢这个博客主题。

—— Hux 后记于 2015.10


