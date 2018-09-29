# 直播播放

## **1.播放地址获取**

登录直播控制台，进入“域名管理”页面，选择要查看播放地址的一组域名，点击右侧的“管理”进入域名“基本信息”页面

![](https://github.com/jdcloudcom/cn/blob/edit/image/live-video/%E6%8E%A8%E6%B5%81%E5%9C%B0%E5%9D%80-%E8%8E%B7%E5%8F%96%E6%8E%A8%E6%B5%81%E5%9C%B0%E5%9D%80.png)

在“播放信息”一栏可以查看和复制播放地址，播放地址是按一定规则拼接，其中应用名“APPName”和流名“StreamName”用户推流时自定义，应用名（APPName）、流名（StreamName）目前仅支持英文、数字、“-”、"_",长度需要在1-50字符之间，客户需要根据想要观看的推流时定义的应用名和流名按规则拼接出播放地址

![](https://github.com/jdcloudcom/cn/blob/edit/image/live-video/%E5%9F%9F%E5%90%8D%E7%AE%A1%E7%90%86-%E8%8E%B7%E5%8F%96%E6%92%AD%E6%94%BE%E5%9C%B0%E5%9D%80.png)

## **2.播放地址说明**

**原画地址**

播放地址由域名（Domain）、应用名（APPName）、流名（StreamName）三部分组成，其中域名为客户添加的播放域名，应用名和流名为变量，应用名（APPName）、流名（StreamName）目前仅支持英文、数字、“-”、"_",长度需要在1-50字符之间，在推流时自定义，客户想要观看某一路对应的流可根据需要拼接播放地址。

rtmp:// 播放域名/应用名/流名

http:// 播放域名/应用名/流名.flv

http:// 播放域名/应用名/流名.m3u8

**示例**

播放域名为ccc.ddd.com，客户想要观看的应用名称为
app1，流名为1，对应的rtmp、hls、hdl三种协议的播放地址为：

rtmp:// ccc.ddd.com/app1/1

http:// ccc.ddd.com/app2/1.flv

http:// ccc.ddd.com/app3/1.m3u8

**转码流播放地址**

当客户设置了转码模板，开启转码功能后，转码流的播放地址是由原画地址加上转码模板id组成，不同的转码模板id拼接后对应转码后的播放地址，拼接规则如下

rtmp:// 播放域名/应用名/流名_模板id

http:// 播放域名/应用名/流名_模板id.flv

http:// 播放域名/应用名/流名_模板id.m3u8

**支持的转码模板参数**

| **模板名称** | **模板 ID** | **分辨率** | **码率（kbps）** |
|--------------|-------------|------------|------------------|
| 流畅         | lld         | 640\*360   | 200              |
| 标清         | lsd         | 854\*480   | 400              |
| 高清         | lhd         | 1280\*720  | 800              |

**示例**

播放域名为ccc.ddd.com，设置的转码模板为流畅，对应的模板id为lld，原画的播放地址为：

rtmp:// ccc.ddd.com/app1/1

http:// ccc.ddd.com/app1/1.flv

http:// ccc.ddd.com/app1/1.m3u8

对应的rtmp、hls、hdl三种协议的转码后播放地址为：

rtmp:// ccc.ddd.com /app1/1_lld

http:// ccc.ddd.com /app1/1_lld.flv

http:// ccc.ddd.com /app1/1_lld.m3u8
