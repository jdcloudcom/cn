# 云存储API


## 简介
云存储API，主要包含查询Bucket列表，创建Bucket, 删除Bucket，查询Bucket是否存在, 更多API见：https://www.jdcloud.com/help/detail/1901/isCatalog/1


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**deleteBucket**|DELETE|删除一个bucket</br>|
|**deleteImgProtected**|DELETE|关闭原图保护</br>|
|**getimgProtectedCondition**|GET|获取当前bucket的原图保护配置</br>|
|**headBucket**|HEAD|查询bucket是否存在</br>|
|**listBuckets**|GET|列出当前用户的所有bucket</br>|
|**moveObject**|PUT|moveobject</br>|
|**putBucket**|PUT|创建bucket</br>|
|**putImgProtected**|PUT|创建原图保护</br>|
|**updateBucketMaxCount**|POST|更新bucket最大数量</br>|
