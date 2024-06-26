# WordPress社区版服务实例部署文档

## 概述

WordPress是一款免费开源的网站内容管理系统（CMS），它可以帮助用户简单快捷地创建和管理自己的网站，包括博客、新闻网站、电子商务网站、社交网络等等。WordPress
有丰富的主题和插件库，使得用户可以轻松地为网站定制外观和功能。WordPress的易用性和可扩展性使其成为世界上最受欢迎的网站建设工具之一。

计算巢官方提供了WordPress社区版服务，您无需自行配置云主机，即可在计算巢上快速部署WordPress服务、从而方便地基于WordPress简单快捷地搭建自己的网站。

本文向您介绍如何开通计算巢上的WordPress社区版服务，以及部署流程和使用说明。


## 计费说明

WordPress在计算巢上的费用主要涉及：

- 所选vCPU与内存规格
- 系统盘类型及容量
- 公网带宽
- 数据库配置

计费方式包括：

- 按量付费（小时）
- 包年包月

预估费用在创建实例时可实时看到。

## 部署架构

WordPress社区版有单机版和多节点部署两种架构。

## RAM账号所需权限
| 权限策略名称 | 备注 |
| --- | --- |
| AliyunECSFullAccess | 管理云服务器服务（ECS）的权限 |
| AliyunVPCFullAccess | 管理专有网络（VPC）的权限 |
| AliyunROSFullAccess | 管理资源编排服务（ROS）的权限 |
| AliyunRDSFullAccess | 管理云数据库服务(RDS)的权限 |
| AliyunSLBFullAccess | 管理负载均衡服务(SLB)的权限 |
| AliyunComputeNestUserFullAccess | 管理计算巢服务（ComputeNest）的用户侧权限 |
| AliyunCloudMonitorFullAccess | 管理云监控（CloudMonitor）的权限 |


## 部署流程

### 部署步骤

单击[部署链接](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?spm=5176.24779694.0.0.3a9c4d22RcCr2Q&ServiceId=service-bfee880fa3bf45c1a989)，进入服务实例部署界面，根据界面提示，填写参数完成部署。

### 部署参数说明
您在创建服务实例的过程中，需要配置服务实例信息。下文介绍stable-diffusion服务实例输入参数的详细信息。

| 参数组    | 参数项    | 示例                   | 说明                                                                                   |
|--------|--------|----------------------|--------------------------------------------------------------------------------------|
| 选择模板   | 模板选择   | 多节点版                 | 模板架构类型                                                                               |
| 服务实例名称 |        | test                 | 实例的名称                                                                                |
| 资源组和地域 | 资源组    | 默认资源组                | 创建的服务实例位于的资源组                                    <br/><br/><br/><br/><br/><br/><br/>   <br/> |
| 资源组和地域 | 地域     | 华东1（杭州）              | 选中服务实例的地域，建议就近选中，以获取更好的网络延时。                                      <br/>              |
| 付费类型配置 | 付费类型   | 按量付费 或 包年包月          |
| ECS实例配置 | 实例类型   | ecs.gn6i-c4g1.xlarge | 实例规格，可以根据实际需求选择                                                                      |
| ECS实例配置 | 系统盘空间  | 40                   | 系统盘大小，可以根据实际需求选择                                                                     |
| ECS实例配置 | 流量付费类型 | PayByTraffic         | 流量付费类型，可以根据实际需求选择                                                                    |
| ECS实例配置 | 流量公网带宽 | 10                   | 流量公网带宽，可以根据实际需求选择                                                                    |
| ECS实例配置 | 实例密码   | *******              | 设置实例密码。长度830个字符，必须包含三项（大写字母、小写字母、数字、()`!@#$%^&*-+={}[]:;'<>,.?/ 中的特殊符号）            |
| 负载均衡配置 | 负载均衡实例规格| slb.s2.small         | 负载均衡实例规格，可以根据实际需求选择                                                                  |
| 数据库配置  | 实例系列   | 高可用版                 | RDS实例系列，可以根据实际需求选择                                                    <br/>     <br/> |
| 数据库配置  | 实例规格   | mysql.n2.medium.1    | RDS实例规格，可以根据实际需求选择                                                 <br/><br/>        |
| 数据库配置  | 实例存储   | 50                   | RDS实例大小，可以根据实际需求选择                                                                   |
| 数据库配置  | 数据库名   | wordpress            | WordPress数据库名                                                                        |
| 数据库配置  | 数据库账号  | wpuser               | WordPress数据库账号                                                                       |
| 数据库配置  | 数据库密码  | ********             | 设置实例密码。长度830个字符，必须包含三项（大写字母、小写字母、数字、()`!@#$%^&*-+={}[]:;'<>,.?/ 中的特殊符号）       |
| WordPress配置 | WordPress 监听端口号| 8080                 | WordPress网站监听端口号                                                 |
| 可用区配置  | 部署区域   | 可用区I                 | 地域下的不同可用区域                                                                           |
| 选择已有基础资源配置 | VPC ID | vpc-xxx              | 选择专有网络的ID。                                                                           |
| 选择已有基础资源配置 | 交换机ID  | vsw-xxx              | 选择交换机ID。若找不到交换机, 可尝试切换地域和可用区                                                         |



### 验证结果

1. 查看服务实例。服务实例创建成功后，部署时间大约需要6分钟。部署完成后，页面上可以看到对应的服务实例。 
![img.png](img.png)
2. 通过服务实例访问WordPress,进入到对应的服务实例后，可以在页面上WordPress的登录网址。
![img_1.png](img_1.png)
![img_2.png](img_2.png)

### 使用WordPress

请访问WordPress官网了解如何使用WordPress：[WordPress使用文档](https://wordpress.com/zh-cn/support/getting-started-with-wordpress-com/)
