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
[![部署到HuggingFace](https://camo.githubusercontent.com/8a78fbeecb190a3c3654ee14fcd14fa01f9a75056eb3b1ba38ecd16fa9dfdec9/68747470733a2f2f68756767696e67666163652e636f2f64617461736574732f68756767696e67666163652f6261646765732f7261772f6d61696e2f6465706c6f792d6f6e2d7370616365732d6d642e737667)](https://huggingface.co/spaces/Harry-zklcdc/go-proxy-bingai?duplicate=true&visibility=public)</br>
☝🏻 这是个按钮, ☝🏻 这真的是个按钮

然后点击下面的 「Duplicate Space」按钮




接下来会跳转到一个新的地址

![image-20240129194816910](https://private-user-images.githubusercontent.com/21104213/300448928-de2ce50c-ef98-4c7c-ada9-5156b11d6aeb.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDY4ODg2NDUsIm5iZiI6MTcwNjg4ODM0NSwicGF0aCI6Ii8yMTEwNDIxMy8zMDA0NDg5MjgtZGUyY2U1MGMtZWY5OC00YzdjLWFkYTktNTE1NmIxMWQ2YWViLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAyMDIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMjAyVDE1MzkwNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTFhN2RjOGNiYjIxMWE1YmVlZDc0ZmYyMzhmMzFiNWQ3NjcyOGIxYjdkMzIyNzFhNzZiZTQ0NmE5YWVjNzUwY2EmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.XlAbp3Alny-V5JRzhlDwC0eJcbI3lXNeC9OGYE3PNc4)

待上面的 「Building」 变成「Running」之后, 即可使用

#### 3. 获取空间链接

点击右上角的「三个点」, 然后点击「Embed this Space」

![image-20240129195105123](https://private-user-images.githubusercontent.com/21104213/300448994-bb381f96-2317-4043-b3f4-b420fbd582c1.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDY4ODg2NDUsIm5iZiI6MTcwNjg4ODM0NSwicGF0aCI6Ii8yMTEwNDIxMy8zMDA0NDg5OTQtYmIzODFmOTYtMjMxNy00MDQzLWIzZjQtYjQyMGZiZDU4MmMxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAyMDIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMjAyVDE1MzkwNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWQzNWFkMTdlNThmYzZjZWQwZjBlY2Y5NzViNzFlYjRkYjUyZjBhZDkwOWY2ZWJmOGRjNDliYmZmMWExMzEzMjkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.dOUNHHkq6JXITZz0yUQfOWXmXDozzJ_iP0uwexciK2k) ![image-20240129195241664](https://private-user-images.githubusercontent.com/21104213/300449056-14cded04-1ebf-4ef4-a6c1-0ff8c73aadbb.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDY4ODg2NDUsIm5iZiI6MTcwNjg4ODM0NSwicGF0aCI6Ii8yMTEwNDIxMy8zMDA0NDkwNTYtMTRjZGVkMDQtMWViZi00ZWY0LWE2YzEtMGZmOGM3M2FhZGJiLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAyMDIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMjAyVDE1MzkwNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTZlYzY2ZGM2Y2E2MmE0MTJjZmIwYjVmYjQ4ZjhlN2Q4ZDJkYTUyZjAzYWVjOTMzYTkxOTgxMmRjOWI1MGYzNzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.A2T9EDz0tix3eUhLNNZOESCpkhZZsR5xcBcIWCTizA0)

出现的链接地址即访问的链接，点击右侧「Copy」按钮, 复制链接，到浏览器打开即可