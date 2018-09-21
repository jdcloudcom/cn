# JDCLOUD 流数据总线 API


## 简介
提供流数据总线topic操作的相关接口。


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addTopic**|POST|创建topic时，topicModel中只需要传topic参数，另外两个参数可为空|
|**createConsumerGroup**|POST|创建consumerGroupName|
|**deleteConsumerGroup**|DELETE|删除consumerGroupName|
|**deleteTopic**|DELETE|删除topic|
|**describeTopic**|GET|查询指定主题,如果已归档会返回归档信息|
|**getConsumerGroupList**|GET|查看指定主题的所有消费组|
|**getTopicList**|GET|查询topic列表，返回topic的集合|
|**updateTopic**|PUT|此接口可以用来更新主题，创建归档，修改归档，删除归档，传入不同的参数可以实现不同的功能。修改归档只需要修改相应归档的参数，删除归档只需要把归档参数置为空即可|
