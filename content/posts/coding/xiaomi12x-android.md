---
title: 小米12X类原生体验
date: 2024-01-16T00:00:06+0800
tags:
  - 折腾
feature: https://i0.hdslb.com/bfs/article/eadb3688ef8d0e4dcbd906d886d62e72514080334.jpg
---

### 引言

自从手机买来之后，我的小米12X一直使用原厂系统，但是最近发生的一件事，让我对这手机系统的安全性产生了怀疑。</br>
为了体验流畅和用的舒心，我为小米12x上刷入了Paranoid Android Topaz，Paranoid Android是一款接近原生的Android操作系统，为用户提供了流畅和纯净的体验。本文将从刷入过程到使用体验来聊聊没有本土化的安卓系统在国内表现究竟如何。

### 刷入准备

> 小米12x在刷入Paranoid Android最新版安卓13后没有什么大的Bug。

#### 准备工作
在开始刷机之前，有几项准备工作需要完成：
1. **最新平台工具**：确保你的电脑上安装了最新的Android平台工具（Platform-Tools）。
2. **谷歌USB驱动**：安装适用于Android的谷歌USB驱动程序。
3. **解锁Bootloader**：确保你的小米12x的Bootloader已经解锁。

#### 下载资源

你可以从GitHub上获取最新的Paranoid Android Topaz构建版本。请注意，除非内核特别声明支持Paranoid Android且包含谷歌移动服务（GMS），否则不支持自定义内核。</br>

**下载地址**：https://github.com/mickaelmendes50/android_device_xiaomi_psyche/releases

### 推荐固件

为了最佳体验，建议在MIUI V14.0.4.0或更新版本的基础上进行刷机。

### 刷机步骤

#### Fastboot包(*-image.zip)

1. **进入Bootloader模式**：将手机连接到电脑，并重启至Bootloader模式。
2. **刷入系统**：在电脑的命令提示符或终端中输入以下命令：
   ```bash
   fastboot update --skip-reboot aospa-topaz-beta-*-image.zip
   ```
3. **恢复出厂设置**：刷机完成后，进入恢复模式，并进行出厂设置。这一步骤仅在首次刷入Paranoid Android时需要。

#### Recovery包 (*.zip)

1. **下载并刷入vendor_boot.img**：首先下载vendor_boot.img，并使用以下命令刷入：
   ```bash
   fastboot flash vendor_boot vendor_boot.img
   ```
2. **通过ADB刷入系统**：重启手机至恢复模式，选择“从ADB更新”，然后在电脑上执行：
   ```bash
   adb sideload aospa-topaz-beta-*.zip
   ```
3. **恢复出厂设置**：与Fastboot包相同，完成后需要进行出厂设置。

### Root

1. 下载aospa-topaz-*-image.zip；
2. 从aospa-topaz-*-image.zip提取"boot.img"；
3. 下载magisk.apk，在手机中安装；
4. 拷贝"boot.img"到手机内存；
5. 使用magisk对"boot.img"进行修补；
6. 拷贝magisk修补后的"boot.img"到电脑内存；
7. 手机从关机后按"音量键-"和"电源键"进入fastboot；
8. 使用命令fastboot flash boot $magisk修补后的"boot.img"文件路径；
9. 使用命令fastboot reboot；
10. magisk会显示环境需要修复，按提示重启即可。

### Magisk与LSPosed模块

![](https://i0.hdslb.com/bfs/article/2adf83b0d9a8f3cfd20938a2d69d314a514080334.jpg)


- **米窗**:类原生无小窗，这是解决这个问题的最优解，配合Xposed Edge Pro可以实现极致的小窗体验，据说有的类原生逆向出了小窗。
- **微X模块**:薅羊毛集赞，防撤回，抢红包必备。
- **HMSPush**:类原生没有推送系统，而华为的推送做的相当不错，不喜欢华为推送的也可以使用小米推送。
- **lconify**:类原生美化模块，让单调的类原生界面丰富多彩。
- **NFC卡模拟**：非常好用，解决类原生没有门禁卡模拟，支持熄屏刷卡。
- **Pixelify GPhotos**:白嫖谷歌相册无限空间。
- **TGramhooks**：解除下载截图限制，你的电报你做主。
- **Thanox**：类原生后台管理系统，和毒瘤说拜拜。
- **Xposed Edge Pro**:强大的安卓手势，各种自定义。
- **XposedSmsCode**:自动填充验证码工具。
- **GMS Doze**：谷歌打盹，防止谷歌全家桶后台耗电。
- **Moto本地化模块**：替换难用的原生电话短信等，电话有录音，拦截，小部件日历都漂亮。
- **QuickSwitch**:桌面替换，换掉自定义少的桌面，我用Lawnchair非常好用，目前安卓13，14都在测试阶段。

### 美化结果

![](https://i0.hdslb.com/bfs/article/481f0678dabd0ce84190d196f6e49751514080334.jpg)

类原生美化出来也不比国产UI差，简洁又好看，暂且叫他XiaomiPlus哆啦爱梦定制版。

### 日常使用体验

相较于其他第三方系统，他的Bug较少，指纹之类的全部正常，就是自动调光有些问题，偶尔闪瞎眼。

下面我总结一下日常使用场景：

- **相机**：自带小米的徕卡相机，我感觉拍出来不好看，所以我用谷歌相机，配置使用98合一，应有竟有。
- **乘车**：NFC不能直接刷卡乘车，门禁借用第三方可行，不过对我影响不大，我喜欢用乘车码。
- **开门**：借助第三方工具，可以模拟。
- **指纹支付**：可用模块，不过我喜欢打按键🤪
- **推送**：遥遥领先，华为No1，很稳定。