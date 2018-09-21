# 使用Xsplit工具推流

##1. 注册软件账号

首先打开软件下载页面，链接地址为<https://www.xsplit.com/download>，点击页面右上角的登录，在弹出的对话框中选择注册，根据提示注册激活账号。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit注册账号.png)

## 2. 下载软件

注册完成后，在下载页面点击DOWNLOAD链接，下载Xsplit软件，然后安装。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit下载软件.png)

安装完成后，打开软件输入注册时填写的用户名和密码登录，如果提示购买软件，可忽略，稍等几秒钟后点击右下角的Continue继续，如果确实需要更多设置也可以选择购买软件。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit注册软件-2.png)

## 3.设置直播区域及分辨率

### 3.1 直播区域设置

打开软件，点击“资源”菜单栏——屏幕捕获，然后鼠标点击桌面或者想直播的窗口内部，就选中直播区域了，
然后用鼠标在角落拉满置全屏，添加时点击桌面就是直播整个桌面的内容，点击一个窗口的内部就只直播这个窗口，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit直播区域设置.png)

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit直播区域设置2.png)

### 3.2 分辨率设置

点击软件右上角的分辨率选择菜单，选中与自己桌面分辨率一样或者相同比例的分辨率（分辨率后面括号里的比例，如1280x720-720P（16:9），这个的比例就是16:9），如果没有自己的分辨率或者相对应的比例，可以点击添加分辨率菜单中的自定义分辨率来添加，如果直播过程中机器感觉卡顿，按照比例缩小分辨率即可。

注：直播桌面分辨率一定要和桌面分辨率比例一致，不然直播画面无法拉到全屏，如果直播窗口，请把分辨率设置为和窗口一样大的比例。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit分辨率设置.png)

### 3.3 添加其他资源

点击软件的“资源”菜单，可添加文本，摄像头，媒体文件等，选着需要添加的资源，点击即可。

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit添加其他资源.png)

## 4. 添加推流信息

点击“输出”菜单栏中的“”建立新的输出”菜单项，在子菜单中点选“Custom
RTMP”项，在弹出的窗口中填写相关设置信息，如下图：

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/xsplit添加推流信息.png)

**Name**：频道名称或者叫APP名称，按照定义规则自定义填写

**Description**：描述，可选填

**RTMP URL**：直播推流地址，京东云分配的推流地址

**Stream Name**：推流流名，按照定义规则自定义填写

**编码**：视频编码格式，默认为x264

**比特率**：直播时视频码率，根据需求填写适当值

## 5. 开始直播

点击广播，点击刚才设置好名字的频道，之后软件上会出现红色字体提示正在直播，这个时候你的直播就正式开始了。
