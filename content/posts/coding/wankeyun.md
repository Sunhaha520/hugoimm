---
title: 玩客云的最后归宿：NAS？建站？都要！
date: 2023-10-06T00:00:06+0800
tags:
  - 折腾
feature: https://i0.hdslb.com/bfs/article/d130eeba0c555cdbcae292e70df3e505514080334.jpg
---
### 刷Armbian固件

首先，先给出所需要的固件，玩客云armbian固件下载地址：[https://github.com/hzyitc/armbian-onecloud/releases](https://github.com/hzyitc/armbian-onecloud/releases)

注意：casaos还不能支持最新版的底包，所以我们需要下载之前的老版本。在下载页面上往下拉，**找到6.1.9这个版本**。我们需要去下载带mini和burn字样的刷机包。mini代表最小安装包，**burn代表线刷包**。

至于如何刷机，各位可以参考以下教程：

[玩客云刷机 Armbian](https://zhuanlan.zhihu.com/p/593474799)

---

### 刷入CasaOS

首先，**ssh远程连接刷好armbian的玩客云**，执行以下操作：

#### 检查时间

首先我们需要检查系统时间

```bash
date -R
```

如果时区及时间不对。执行下面的操作：

```bash
cp /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime
```

再次检查时间：

```bash
date -R
```

### 添加软件源

此步骤**视情况而定**，我所在地区不用添加软件源就成功安装，如果和我一样可以成功安装，**此步并不需要**。

```bash
nano /etc/apt/sources.list
```

然后在打开的文件下面添加以下内容：

```xml
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free
```

### 安装CasaOS

然后去终端执行以下命令，casaos的安装**只要这一条代码就可以**：

```bash
wget -qO- https://get.casaos.io | bash
```

如果你的网络不好，可以执行这个国内源代码试试（注意使用了国内源的一键安装以后是无法自动升级casaos系统的）：

```bash
curl -fsSL cn-get.casaos.io | bash
```

<aside>
💡 卡在安装这步的，主要还是网络问题。

</aside>

然后就可以用浏览器访问你的CasaOS了，**浏览器输入玩客云IP地址即可**。

![https://cdn.dribbble.com/userupload/10771601/file/original-b2a8b67455d819fd613eeaf74fb93ce3.webp](https://cdn.dribbble.com/userupload/10771601/file/original-b2a8b67455d819fd613eeaf74fb93ce3.webp)

---

### 安装Alist

在最新版的CasaOS中，Alist可以直接在应用商店安装，**但是我发现并不是最新版，所以我还是推荐手动安装**。

在ssh里运行这一段命令，安装alist的docker镜像：

```bash
docker run -d --restart=always -v /etc/alist:/opt/alist/data -p 5244:5244 -e PUID=0 -e PGID=0 -e UMASK=022 --name="alist" xhofe/alist:latest
```

然后用以下命令查看Alist，也可以知道密码：

```bash
docker exec -it alist ./alist admin
```

最后在浏览器中输入**IP加端口号5244**便可进入Alist

![https://cdn.dribbble.com/userupload/10771602/file/original-4ebceacf2807575f1c7b7bbd4e0d3903.webp](https://cdn.dribbble.com/userupload/10771602/file/original-4ebceacf2807575f1c7b7bbd4e0d3903.webp)

后期我会出我的Alist美化教程。以下是Alist官方文档：

[Home](https://alist.nn.ci/zh/)

---

未完待续……

后期教程即将呈现