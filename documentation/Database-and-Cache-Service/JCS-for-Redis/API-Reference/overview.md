
# 缓存Redis相关接口

为了方便您理解OpenAPI相关的基本概念和参数，建议您先查看OpenAPI使用入门。

- 版本：v1

接口名称|请求方式	|功能描述
---|:--:|---:
createCacheInstance	|POST|	创建一个指定配置的缓存Redis实例
deleteCacheInstance|	DELETE|	删除单个缓存Redis实例
describeCacheInstance|	GET|	查询缓存Redis实例详情
describeCacheInstances|	GET|	查询缓存Redis实例列表
describeInstanceClass|	GET	|查询某区域下的实例规格列表
describeUserQuota|	GET	|查询账户配额信息
modifyCacheInstanceAttribute|	PATCH|	修改缓存Redis实例的资源名称、描述，二者至少选一
modifyCacheInstanceClass|	POST|	变更缓存Redis实例配置
resetCacheInstancePassword	|POST|	重置缓存Redis实例密码
