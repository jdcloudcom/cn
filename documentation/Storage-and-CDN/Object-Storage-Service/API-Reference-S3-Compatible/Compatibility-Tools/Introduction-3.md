# 概述

大多基于AWS S3开发的工具在京东云存储上都可以使用。在使用这些工具的时候，一般来说您都要配置3个内容：accesskey、secretkey、endpoint。

## accesskey和secretkey

这两个值是用户身份的一个凭证，在验证签名时使用。您可以在京东云的控制台获取这两个值。

## endpoint

endpoint是用来指定服务域名的，目前不支持https，所以您只能设置为http。

下面我们将介绍一些常用的工具：sdk-python、sdk-java、sdk-php、CloudBerry。我们的介绍将帮助您快速入手，详细信息请参考相关的文档。
