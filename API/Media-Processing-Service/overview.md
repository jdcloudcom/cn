# 媒体处理 API


## 简介
媒体处理相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**countImageStyle**|GET|图片样式总数|
|**createImageStyle**|POST|添加图片样式|
|**createThumbnailTask**|POST|创建截图任务，创建成功时返回任务ID。本接口用于截取指定时间点的画面。|
|**deleteImageStyle**|DELETE|删除图片样式|
|**getImageStyle**|GET|图片样式详情|
|**getNotification**|GET|获取截图通知|
|**getThumbnailTask**|GET|根据任务ID获取截图任务。|
|**listImageStyle**|GET|图片样式列表|
|**listThumbnailTask**|GET|查询截图任务，返回满足查询条件的任务列表。|
|**setNotification**|PUT|设置媒体处理通知, 在设置Notification时会对endpoint进行校验, 设置时会对endpoint发一条SubscriptionConfirmation(x\-jdcloud\-message\-type头)的通知, 要求把Message内容进行base64编码返回给系统(body)进行校验|
|**updateImageStyle**|PUT|修改图片样式|
