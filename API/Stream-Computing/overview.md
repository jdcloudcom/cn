# JDCLOUD流计算API


## 简介
提供流计算操作的相关接口。


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addOrUpdateJob**|POST|添加或者更新job|
|**addOrUpdateStorage**|POST|创建或者更新storage|
|**createNamespace**|POST|创建namespace|
|**deleteJob**|DELETE|删除作业|
|**deleteNamespace**|DELETE|删除namespace,如果旗下关联有其他资源，不允许删除|
|**deleteStorage**|DELETE|删除指定输入|
|**describeJob**|GET|查询指定作业详情|
|**describeStorage**|GET|查询指定输入|
|**getJobList**|GET|查询指定应用下的所有job|
|**getStorageList**|GET|创建或者更新storage|
|**queryNamespaceDetail**|GET|查询某个应用详情|
|**queryNamespaces**|GET|查询租户下的应用列表|
|**startJob**|GET|运行job|
|**stopJob**|GET|停止作业运行job|
|**updateNamespace**|PUT|更新namespace|
