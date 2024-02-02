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
|模型名称|说明|
|---|---|
|dall-e-3|画图模型, 目前仅有|
|Precise|精准模式, 联网搜索|
|Balanced|平衡模式, 联网搜索|
|Creative|创造模式, 联网搜索|
|Precise-offline|精准模式, 不联网搜索|
|Balanced-offline|平衡模式, 不联网搜索|
|Creative-offline|创造模式, 不联网搜索|
|Precise-g4t|GPT4-Turbo 精准模式, 联网搜索|
|Balanced-g4t|GPT4-Turbo 平衡模式, 联网搜索|
|Creative-g4t|GPT4-Turbo 创造模式, 联网搜索|
|Precise-g4t-offline|GPT4-Turbo 精准模式, 不联网搜索|
|Balanced-g4t-offline|GPT4-Turbo 平衡模式, 不联网搜索|
|Creative-g4t-offline|GPT4-Turbo 创造模式, 不联网搜索|


下面我们将借助Huggingface免费部署这个项目！
Note

此教程主要是用于部署 BingAI 本体 + 人机验证服务器

#### 1. 注册 🤗HuggingFace 账号

具体注册方法请出门右拐隔壁百度 or Google

#### 2. 复制空间

登录账户后, 点击下面按钮</br>
[![部署到HuggingFace]()](https://huggingface.co/spaces/Harry-zklcdc/go-proxy-bingai?duplicate=true&visibility=public)</br>
☝🏻 这是个按钮, ☝🏻 这真的是个按钮

然后点击下面的 「Duplicate Space」按钮

![](https://i0.hdslb.com/bfs/article/e8482051aa8780582ac978c60f867175514080334.png)



接下来会跳转到一个新的地址

![](https://i0.hdslb.com/bfs/article/1e89c799a5ed5e57c09b56f795f2f49f514080334.png)

待上面的 「Building」 变成「Running」之后, 即可使用

#### 3.获取空间链接

点击右上角的「三个点」, 然后点击「Embed this Space」

![](https://i0.hdslb.com/bfs/article/7d3c86e6d188716f9b804026ca83d74c514080334.png)
![](https://i0.hdslb.com/bfs/article/16879d7048f4766df918a60dfe95b4e3514080334.png)


出现的链接地址即访问的链接，点击右侧「Copy」按钮, 复制链接，到浏览器打开即可
更多部署方式请参考官方文档：<https://github.com/Harry-zklcdc/go-proxy-bingai/wiki>
### 部署LobeChat
如果在 Vercel 上免费部署该服务，可以按照以下步骤进行操作：<br>
1. 点击下方按钮开始部署： 直接使用 GitHub 账号登录即可
2. 绑定自定义域名（可选）：Vercel 分配的域名 DNS 在某些区域被污染了，绑定自定义域名即可直连。<br>
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Flobehub%2Flobe-chat&envDescription=Find%20your%20OpenAI%20API%20Key%20by%20click%20the%20right%20Learn%20More%20button.&envLink=https%3A%2F%2Fplatform.openai.com%2Faccount%2Fapi-keys&project-name=lobe-chat&repository-name=lobe-chat)<br>
部署完成后，你便可进入LobeChat！

### 环境变量
对于Go-Proxy-BingAI，我建议在huggingface中设置变量`APIKEY`，这样别人就无法使用你搭建的api。<br>
示例：`APIKEY=sk-xxxxxxxxxxxxxx`<br>
对于LobeChat,可去vercel中设置环境变量，变量如下：


![](https://i0.hdslb.com/bfs/article/0380e322e526ccf0db5e162bcff9aa3d514080334.png)

- `CUSTOM_MODELS`填写如下:
```txt
-all,+Creative-g4t,+Balanced-g4t,+Precise-g4t,+Creative,+Balanced,+Precise,+Creative-g4t-offline,+Balanced-g4t-offline,+Precise-g4t-offline,+Creative-offline,+Balanced-offline,+Precise-offline
```

- `ACCESS_CODE`自己设置，用于访问LobeChat用，防止他人使用。
- `OPENAI_API_KEY`填写Go-Proxy-BingAI项目部署中设置的变量`APIKEY`
- `OPENAI_PROXY_URL`填写huggingface部署的域名+/api/v1，例如我的就是以下链接：<br>
https://zhenyu1-go-proxy-bingai.hf.space/api/v1


### 效果展示

![](https://i0.hdslb.com/bfs/article/b010d94814a55540f2b2c4c0548cb8c5514080334.png)

可以看到，给出几个典问题，它都可以顺利通过，同时LobeChat中内置了许多“角色”，大大提高了可玩性，插件功能自测，有些确实不行。