# 使用FMLE工具推流

## 1. 下载软件

首先打开软件下载地址，通过下面的链接下载软件，软件分为32位和64位两个版本，请根据需要自己选择合适的版本。

<http://www.adobe.com/go/fmle32_win>

<http://www.adobe.com/go/fmle32_mac>

## 2. 安装软件

打开下载的安装包软件，双击运行安装包，在弹出的安装窗口中，根据提示点击下一步，完成软件安装，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle安装软件.png)

## 3. 软件使用设置说明

双击打开软件，软件界面比较简单，主要分为以下几个模块，主要有视音频格式设置、推流信息配置、视音频预览如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle设置说明.png)

### 3.1 预览模块设置

在预览模块中，可以选择要预览的内容，包括输入内容预览、输出内容预览、、音频预览，可以根据需要选择性勾选这三个选项，同时还可以对窗口的大小比例进行调整，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle预览模块设置.png)

### 3.2 视频和音频格式设置

在推流之前我们需要先设置视音频格式的参数，模块左边为视频格式设置，右边为音频格式设置，可通过勾选视频和音频前面的框，来选择使用音频、视频或者音视频同时。视频配置中我们可以对视频输入设备、帧率、码率、编码方式、输入分辨率、输出分辨率等进行修改，音频配置中我们可以对音频输入设备、音频格式、音频采样频率、音频码率、省道类型等进行修改，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle视频和音频设置.png)

### 3.3 推流信息设置

推流信息模块中我们可以对推流地址、推流流名、文件保存等进行设置，其中推流地址分为主地址和备用地址，备用地址为选填，没有的话为空就可以，填写完成后，可点击“Connect”按钮，测试一下是否连接成功，如果提示失败，请检查一下填写的内容是够正确，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle推流信息设置.png)

### 3.4 推流开始

设置完以上信息后，点击软件界面最下方的“Start”按钮开始推流，如需停止点击“Stop“按钮。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/fmle推流开始.png)

## 4. 总结

FMLE 多种操作系统都可以正常使用，单独音频、单独视频
录制、直播使用相对比较简单，建议在直播过程中关掉预览功能，这样可以降低系统资源的消耗，但不支持抓屏等功能，建议在需要抓屏或者音视频同时直播的情况下
还是使用OBS，性能相比FMLE会更好，设置选项也更多些。
