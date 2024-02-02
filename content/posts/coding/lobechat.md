---
title: Lobechat+Copilot部署私人智能助手
date: 2024-02-02T21:02:37+0800
tags:
  - 折腾
feature: https://i0.hdslb.com/bfs/article/92d091d1b13fb9a7e6616d8367f5560e514080334.jpg
---
### 前言
最近回老家了，本来想写一篇用fly部署memos的教程，奈何银行比较忙，信用卡一直没有办下来，再加上老家真的太冷，我是真的不想掏出手敲键盘打字写教程😢。</br>
昨天靠着电热毯和空调，给自己的电脑装了个Linux mint，把Hugo写作迁移到了这个Linux上，顺便又折腾了一下微软的Copilot和常年霸榜Github的开源项目Lobechat，体验一下就发现非常好用，索性就写个教程吧。
### 部署Go-Proxy-BingAI

据说，微软的Copilot提供免费的GPT-4服务，对于白嫖党来说这是个非常好的选择。但是因为地区问题，我们并不能使用微软提供的Copilot服务，所以我自己打算做个逆向然后建个镜像站，但是还没动手，就在Github上发现了这个项目：<https://github.com/Harry-zklcdc/go-proxy-bingai>。<br>
Go-Proxy-BingAI项目是基于微软 New Bing 定制的微软 BingAI 演示站点，基本兼容 BingAI 所有功能, **支持 OpenAI 格式 API 调用**，一键部署, 国内可用, 无需登录即可畅聊。特别是支持OpenAI格式API调用真的是太实用了。此项目支持的模型如下：
