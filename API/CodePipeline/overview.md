# 流水线


## 简介
流水线相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**manualAction**|POST|查询多个指定流水线执行及状态信息|
|**stopPipelineInstance**|POST|停止流水线的一次执行|
|**getPipelineInstance**|GET|查询流水线执行结果及状态信息|
|**getPipelineInstances**|GET|查询流水线执行历史列表|
|**getPipelineInstancesByUuids**|GET|根据条件查询流水线执行历史|
|**createPipeline**|POST|新建流水线任务|
|**deletePipeline**|DELETE|删除一个流水线任务|
|**getPipeline**|GET|根据uuid获取流水线任务的配置信息|
|**getPipelines**|GET|查询获取流水线任务列表，并显示最后一次执行的状态或结果信息|
|**startPipeline**|POST|根据uuid启动一个流水线任务|
|**updatePipeline**|PUT|更新流水线任务|
