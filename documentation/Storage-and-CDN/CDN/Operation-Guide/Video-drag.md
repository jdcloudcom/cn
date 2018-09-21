# 视频拖拽

在视频点播场景中，网民可根据观看内容拖拽，开启该功能时，CDN服务端会向请求客户端发送请求开始时间或者字节的视频内容

拖拽方式：字节和时间，字节拖拽需要源站支持range回源，时间拖拽url格式为：https://www.a.com/content.mp4?start=20&end=50（即从第20s开始播放，播放至50s时结束）

目前支持的文件格式为：MP4

点击“[域名列表](https://cdn-console.jdcloud.com/domainlist)”--选择相应的域名进入“[高级配置](https://cdn-console.jdcloud.com/detail/advanced?id=pid-test1.jcloud.com)”--“视频拖拽”可进行设置，变更位置也在此

![image.png](https://img1.jcloudcs.com/cms/381c8249-23ab-49db-b98c-e56537a2676f20180205110128.png)
