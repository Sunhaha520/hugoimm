---
title: Coze，免费强大的GPTs
date: 2024-02-24T08:21:06+0800
tags:
  - 折腾
feature: https://i0.hdslb.com/bfs/article/45b3554bb379f0e9b6d1f9cde578c930514080334.jpg
---
### 开端
最近看到不少大佬开始折腾字节推出的新AI产品Coze，作为很早就知道这个产品的菜鸟，我自然也要跟风掺乎一下。  
我是从去年12月份开始使用这款产品的，刚上线的时候只支持国外用户使用，字节也大方地为老外们提供了免费的GPT4，这真的是不得不吐槽国内一些公司对内对外真的是两幅面孔。  
因为不支持国内直接使用，字节提供的官方对接平台也仅局限于国外的一些社交软件(Discord,Telegram等)，由于过于想体验一下免费的GPT4，于是我在第一时间就部署体验了一下。  

![ceshicoze.webp](https://r2.xiaoayu.eu.org/2024/02/998d0fb91c218da3957f67306dce666e.webp)

可以看出，GPT4有的功能他都有，甚至包括一些实用的插件，可以说字节确实花了大价钱，让老外们狂嗦了一把。  
当然，作为国内第一的宇宙厂，自然也不会忘记我们国内用户，今年年前，我忽然发现字节推出了国内版本的Coze，甚至网址也玩起了文字游戏：  
- 外国官网：<https://coze.com>
- 国内官网：<https://coze.cn>  

个人感觉字节还是花价钱的，毕竟重开了一个新域名，可能用cn.coze.com成本更低。  
对比国外版本，国内的Coze对接平台可是相当得友好，支持自家的飞书，鹅厂的微信公众号和微信客服号，这为国内使用这款产品带来了不少便利。  
当然，便利是要付出代价的，国外原汁原味的GPT4直接砍掉了，用了一个叫云雀的大模型，虽然同样支持一些插件，但是在使用的效果来看还是挺拉跨。效果可见我对接的微信客服账号：  

![weixincoze.jpg](https://i0.hdslb.com/bfs/article/6ee40fd0a81c127431098b80b209d43c514080334.jpg)
可以看出，回答的质量远不如GPT4，生成图片的质量也远远低于官方的Dell-e。  
那么就真的就没有办法体验一下老外特供版的Coze吗？

### 进阶之路
对于国内版的Coze，我只能说可以用，既免费又方便，已经很不错了。但是我就想用国外特供，没别的想法，就因为他要比国内的版本强大，洋人能用的，我为什么不能用？  
这似乎并没有过去太久，直到不久前我看到国外版Coze官方文档更新，他竟然支持Slack部署应用了，就是说你可以把他部署集成到你的Slack办公区中随时使用。Slack是一款办公软件，有点像国内的飞书和钉钉，之前用过Claude的朋友对他也应该非常熟悉，不需要特殊网络就可以在我们的地区直接使用，这使得我们国内用户快速使用国外版Coze成为可能。  
### 部署过程
部署过程我就直接抄写Coze官方文档了。
#### 创建一个 Slack 应用[​](https://www.coze.com/docs/zh_cn/publish/slack.html#%E6%AD%A5%E9%AA%A4%E4%B8%80-%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AA-slack-%E5%BA%94%E7%94%A8)

首先，需要创建一个 Slack 应用并获取应用的配置信息。

1. 打开 [YourApps](https://api.slack.com/apps) 页面，并使用 Slack 账号登录。
    
2. 单击 **Create New App**。如果你是首次创建，单击 **Create an App**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/46b0b27b8bf7417fb8cf90fcbc2371fc~tplv-10qhjjqwgv-image.image)
    
3. 在 **Create an app** 页面, 选择 **From scratch**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/78dea91916b74415bc197d1aadd403c9~tplv-10qhjjqwgv-image.image)
    
4. 在 **Name app & choose workspace** 页面，输入应用名，并为这个应用选择一个关联的空间。
    
5. 查看并同意 Slack API 服务条款，然后单击 **Create App**。
    
    创建应用程序后，你将进入 **Basic Information** 页面。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/2bfededd95b64b6a93378d56b7d02437~tplv-10qhjjqwgv-image.image)
    
6. 转到基本信息页面的 **App Credentials** 部分，然后复制并保存 **Client ID** 和 **Client Secret** 以及 **Signing Secret**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/82401abb8a964a73ab7998acf7b2e318~tplv-10qhjjqwgv-image.image)
    

#### 添加权限[​](https://www.coze.com/docs/zh_cn/publish/slack.html#%E6%AD%A5%E9%AA%A4%E4%BA%8C-%E6%B7%BB%E5%8A%A0%E6%9D%83%E9%99%90)

创建好 Slack 应用后，你需要为创建的应用添加相关权限。

1. 在左侧面板，选择 **OAuth & Permissions。**
    
2. 在 **Scopes** 区域，单击 **Bot Token Scopes** 选项下的 **Add an OAuth Scope** 按钮，添加以下权限：
    
    - app_mentions:read
    - channels:history
    - chat:write
    - commands
    - groups:history
    - im:history
    - mpim:history
    - users:read
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/595192ca83604475bed4c3e54eb675a0~tplv-10qhjjqwgv-image.image)
    
3. 向上滑动到 **OAuth Tokens for Your Workspace** 区域，然后单击 **Install Workspace**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/c255be2c5ab94720b70153859a30eaf8~tplv-10qhjjqwgv-image.image)
    
4. 在弹出的页面中审核创建的应用要申请的 Slack workspace 权限，然后单击 **Allow**。
    
5. 复制并保存 **Bot User OAuth Token**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/e05e7282fa204b0a83fb370b09fa2da3~tplv-10qhjjqwgv-image.image)
    

#### 配置 Bot[​](https://www.coze.com/docs/zh_cn/publish/slack.html#%E6%AD%A5%E9%AA%A4%E4%B8%89-%E9%85%8D%E7%BD%AE-bot)

完成权限配置后，你需要返回 Coze 平台为 Bot 配置 Slack 发布渠道。

1. 登录 [Coze](https://www.coze.com/home)。
    
2. 从左侧 **My Workspace** 区域，选择一个团队空间。
    
3. 在选定的团队空间中，单击目标 Bot 或创建 Bot。
    
4. 在 Bot 编排页面，单击 **Publish**。
    
5. 找到 Slack 渠道，然后单击 **Configure**。
    
    ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/19899c78518449819fe593a8da69809a~tplv-10qhjjqwgv-image.image)
    
6. 复制并保存 **OAuth2 Redirect URL**、**Event Request URL** 和 **Slash Request URL**。
    
7. 输入以下 Slack 配置信息：
    
    |**配置项**|**说明**|
    |---|---|
    |**Token**|Slack 应用的 Bot User OAuth Token。  <br>在已创建 Slack 应用的 **OAuth & Permissions** 页面中获取 **Bot User OAuth Token** 的值。|
    |**Client ID**|Slack 应用的 Client ID。  <br>可以在已创建 Slack 应用的 **Basic Information** 页面获取。|
    |**Client Secret**|Slack 应用的 Client Secret。  <br>可以在已创建 Slack 应用的 **Basic Information** 页面获取。|
    |**Signing Secret**|Slack 应用的 Signing Secret。  <br>可以在已创建 Slack 应用的 **Basic Information** 页面获取。|
    
8. 单击 **Save** 保存配置。
    

#### 配置 Slack 应用[​](https://www.coze.com/docs/zh_cn/publish/slack.html#%E6%AD%A5%E9%AA%A4%E5%9B%9B-%E9%85%8D%E7%BD%AE-slack-%E5%BA%94%E7%94%A8)

在获取到 **OAuth2 Redirect URL**、**Event Request URL** 和 **Slash Request URL** 后，你需要配置 Slack 应用。

1. 打开 [YourApps](https://api.slack.com/apps) 页面，找到已创建的应用。
    
2. 添加重定向 URL：
    
    1. 单击 **OAuth & Permissions**。
        
    2. 在 **Redirect URLs** 区域，单击 **Add New Redirect URL**，然后输入之前复制的重定向URL，再单击 **Add**。
        
    3. 单击 **Save URLs**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/d4d5ce8e9b6d4be7be876cfff46bcc9a~tplv-10qhjjqwgv-image.image)
        
3. 为 Slack 应用配置要订阅的 Bot 事件。Slack 会通过指定的请求 URL 向 Bot 发送订阅的事件活动。
    
    1. 单击 **Event Subscriptions**，并开启 **Enable Events** 功能。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/bfefd50a0e2a4330b7ae87c028751f27~tplv-10qhjjqwgv-image.image)
        
    2. 在 **Request URL** 输入框内输入之前复制的 Event Request URL。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/e8cff0014d9048b0995cb299844b935d~tplv-10qhjjqwgv-image.image)
        
    3. 展开 **Subscribe to bot events** 配置面板，然后单击 **Add Bot User Event**，添加要订阅的时间，例如：`app_mentions` 和 `message.im`。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/7500599a524148c187e7cb245f10bb80~tplv-10qhjjqwgv-image.image)
        
    4. 单击 **Save Changes**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/a057892ead0a402e8e2d17097e096d6b~tplv-10qhjjqwgv-image.image)
        
4. 配置 Slash Commands，允许用户使用 Slash 命令给 Bot 发送消息：
    
    1. 单击 **Slash Commands**，然后单击 **Create New Command**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/305892d909b940d7816a41417a263c3a~tplv-10qhjjqwgv-image.image)
        
    2. 完成配置，并单击 **Save**。
        
        Request URL 是从 Coze 的 Slack 发布配置中复制的 **Slash Request URL**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/8ce081d8cf6c4cdf86ee02ec1e807e6f~tplv-10qhjjqwgv-image.image)
        
5. 允许用户向你的 Bot 发送消息。
    
    1. 单击 **App Home**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/c184c3106cf04f429e35a5065a581d32~tplv-10qhjjqwgv-image.image)
        
    2. 在 **Show Tabs** 部分，选择 **Messages Tab** 下的 **Allow users to send Slash commands and messages from the messages tab** 复选框。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/be538ac578cf43328fb9ca137294ce77~tplv-10qhjjqwgv-image.image)
        
6. （可选）如果你想将这个机器人分发给其他 workspace 使用，需要完成以下操作：
    
    1. 单击 **Manage Distribution**，展开 **Remove Hard Coded Information** 配置面板。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/ac07a2d2e031497095952b93b9c96105~tplv-10qhjjqwgv-image.image)
        
    2. 阅读信息后，勾选 **I’ve reviewed and removed any hard-coded information** 复选框。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/5ae76ef4af5e4b82805b0ef07d3b5dbb~tplv-10qhjjqwgv-image.image)
        
    3. 单击 **Activate Public Distribution**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/5d66586d136f4ca1bc38e81526e26f1c~tplv-10qhjjqwgv-image.image)
        
    4. 复制生成的 **Sharable URL**。
        
        ![图片](https://p16-arcosite-va.ibyteimg.com/tos-maliva-i-10qhjjqwgv-us/2eb26eab0b1f4540b46a05f757d317aa~tplv-10qhjjqwgv-image.image)
        
    5. 在生成的 Sharable URL 最后添加 _`&state={app_id}`_ 。
        
        _`{app_id}`_ 是 Slack 应用的 ID。
        
        `https://slack.com/oauth/v2/authorize?client_id=4878914704467.6568343811620&scope=app_mentions:read,channels:history,chat:write,commands,groups:history,im:history,mpim:history,users:read&user_scope=`_`&`__**`state={app_id}`**_
        

#### 发布并测试 Bot[​](https://www.coze.com/docs/zh_cn/publish/slack.html#%E6%AD%A5%E9%AA%A4%E4%BA%94-%E5%8F%91%E5%B8%83%E5%B9%B6%E6%B5%8B%E8%AF%95-bot)

1. 返回 [Coze](https://www.coze.com/home)。
2. 进入待发布的 Bot，然后单击 **Publish**。
3. 输入 Change log，并找到 Slack 渠道，然后单击 **Publish**。
4. 单击 **Open in Slack** 跳转到 Bot 开始聊天。

### 一些体会

![1.png](https://i0.hdslb.com/bfs/article/bca984a5dd89547f66ed93c622b1139b514080334.png)

首先在我看来，**GPTs 并不算 agent**，优雅的说，可以算是agent的雏形。

Agent 应该是有能力主动思考和行动的智能体。当用户提出需求时，agent 有能力自行感知环境、形成记忆、规划和决策行动，甚至与别的 agent 合作实现任务。而用户每 Prompt 一次才被动回复的 GPTs，还没有达到 agent 的标准。事实上，**国内很多厂商做的都还不是 agent（智能体），只是炒了一波概念**。

严谨的说，**Coze做出来的智能体，比 GPTs 更加接近真正的 agent**，也让大众更低门槛的具象的能感受到 agent 的结构与结果。在扣子中，[LLM](https://www.zhihu.com/search?q=LLM&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A3391298531%7D)被弱化成了比较小的一环，并加持了插件、工作流、知识库、定时任务等等工具，别人有的我要有，别人没的我更要有。

OpenAI是要做AGI的，而扣子更像是字节内部的一个基础设施。过多的插件反而会增加用户的使用门槛，最理想的情况下，就是用户通过自然语言提出需求，GPT就能真实解决。但字节这边不一样，扣子对于字节而言就像是个武器库，或者说是[幻兽帕鲁里](https://www.zhihu.com/search?q=%E5%B9%BB%E5%85%BD%E5%B8%95%E9%B2%81%E9%87%8C&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A3391298531%7D)的工作台，在有需要时，能够**低门槛、多选择、可视化**的搭建针对特定场景功能的智能体。
