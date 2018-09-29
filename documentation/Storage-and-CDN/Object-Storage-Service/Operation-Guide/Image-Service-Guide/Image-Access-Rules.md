# 图片处理访问规则

图片服务都是使用标准的HTTP的GET请求来访问的，所有的处理参数也在URL的QueryString中。

## 通过处理参数来请求缩略图

1.用户请求图片处理接口

（a）老接口：在原文件地址后连接“?img/处理参数”

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?img/s/200/300

（b）新接口：在原文件地址后连接“?x-oss-process=img/处理参数”

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=img/s/200/300

2.请求原始图片

（a）文件直接下载方式

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg

（b）图片处理参数方式

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=img/o

3.图片处理操作支持顺序队列

按顺序将图片处理指令接成处理队列，以“/”分割每个任务名及附属参数，后台按顺序依次执行。

例如：

原始图片地址：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg

处理方式：依次进行缩放，居中裁剪操作

对应图片处理结果地址：

http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=img/s/200/300/cc/200/260

4.处理队列中，前后执行顺序会影响最终结果。

5.单请求最大处操作个数上限<=100，重复操作累计计数。

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=img/s/200/300/cc/200/260中

缩放s，剧中裁剪cc，记为两个操作。

6.处理参数总长不超过1024字节

例如：http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=img/s/200/300/cc/200/260中

处理参数部分为img/s/200/300/cc/200/260

## 通过Style（样式）来请求缩略图

图片处理可将用户的图片处理操作和参数保存成一个别名（如：Stylename），即样式。利用样式功能后，原本一系列操作，只需要用一个很短的URL就能实现相同的效果。

（a）老接口

http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?imgalias/stylename

（b）新接口

http://downloads.oss.cn-north-1.jcloudcs.com/lena.jpg?x-oss-process=imgalias/stylename

## 图片参数处理规范说明

图片处理含以下关键词imgalias,img,imginfo,imgexif,x-oss-process=imgalias,x-oss-process=img,x-oss-process=imginfo,x-oss-process=imgexif

* 在参数图片处理参数合法情况下，上述关键字只能出现一个
       
     例如：
      
     oss.cn-north-1.jcloudcs/bucket/key.jpg?imgalias/style&img/s/100/200    (非法)
       
     oss.cn-north-1.jcloudcs/bucket/key.jpg?imgalias/style&x-oss-process=imgalias/style2   (非法)
       
     oss.cn-north-1.jcloudcs/bucket/key.jpg?imgalias/style   (合法)
       
* imgalias, img, x-oss-process=imgalias, x-oss-process=img参数必须跟有具体参数

    例如：
    
    oss.cn-north-1.jcloudcs/bucket/key.jpg?imgalias/   （非法）

* RequestQuery 的KV没有明确顺序

    例如：
    
    oss.cn-north-1.jcloudcs/bucket/key.jpg?aaa=bb&imgalias/style    (合法)

* RequestQuery 大小写敏感（KV都大小写敏感）

    例如：
    
    oss.cn-north-1.jcloudcs/bucket/key.jpg?imgalias/style    (合法)

    oss.cn-north-1.jcloudcs/bucket/key.jpg?Imgalias/style    (正常访问原图)
