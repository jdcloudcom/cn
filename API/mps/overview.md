# 媒体处理 API


## 简介
媒体处理相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createThumbnailTask**|POST|创建截图任务|
|**getNotification**|GET|获取截图通知|
|**getThumbnailTask**|GET|获取截图任务|
|**listThumbnailTask**|GET|查询截图任务|
|**setNotification**|PUT|设置媒体处理通知, 在设置Notification时会对endpoint进行校验, 设置时会对endpoint发一条SubscriptionConfirmation(x-jdcloud-message-type头)的通知, 要求把Message内容进行base64编码返回给系统(body)进行校验|
