---
title: 使用koyeb免费部署Memos服务
date: 2024-01-19T17:37:26+0800
tags:
  - 折腾
feature: https://i0.hdslb.com/bfs/article/7d7ba1695bcfc604b3be171a6bbc67a5514080334.jpg
---
### 关于Memos和Koyeb

**Koyeb**:一个开发人员友好的无服务器平台，可以直接部署docker容器，默认有每个月5美元的免费额度，支持开一个512m内存的容器。</br>
**Koyeb官网**：<https://www.koyeb.com/>  
**Memos**:「一个具有知识管理和社交网络的开源、自我托管的备忘录中心」。这是一个类似私人微博的产品，支持标签、过滤、搜索、多账户，可以自用也可以和朋友一起使用，用来碎片化的记录信息。</br>
**Memos项目地址**:<https://github.com/usememos/memos>

### 搭建教程
1.首先，进入Memos项目地址页面，Fork一份Memos到自己的仓库下。
![](https://i0.hdslb.com/bfs/article/890408e8ece9249597356dd8429da49f514080334.png)


2.登录Koyeb官网，直接用Github账号登录，授权访问仓库。

![](https://i0.hdslb.com/bfs/article/4cf8061789e3f2010ebb8556801c285b514080334.png)

3.创建应用

![](https://i0.hdslb.com/bfs/article/516607180f1eb6a1b0fc1d5b93016475514080334.png)
4.填写配置，部署应用

![](https://i0.hdslb.com/bfs/article/702dc61f47779c88a79ed8d3f0308475514080334.png)
1. 选中Github然后选中刚刚fork的仓库；
2. `bulider`选择`Dockerfile`；
3. `service type`选择`Web Serivice`;

![](https://i0.hdslb.com/bfs/article/2fe0147bcb85a0a3dfa2e8871abfee4a514080334.png)
1. 确定套餐为Free；
2. 选择一个国家或者地区，美国和德国差不多；
3. 点击`Advanced`添加端口信息为5230，最后点击下面的Apply就开始部署了。


![](https://i0.hdslb.com/bfs/article/a7c8ef3be02fe4ac16c4f9409eb4ddeb514080334.png)

### 部署成功
Koyeb会给你一个域名，这个域名具有SSL，可以直接调用到网站的说说页面。
