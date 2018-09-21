# jke


## 简介
k8s 集群服务相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createCluster**|POST|\- 创建集群</br>\- 证书</br>  \- 关于kubernetes的证书，默认生成，不需要用户传入。</br>\- nodegroup</br>  \- cluster必须与nodeGroup进行绑定</br>  \- cluster支持多nodegroup</br>  \- 状态</br>    \- pending,reconciling,deleting状态不可以操作更新接口</br>    \- running，running_with_error状态可以操作nodegroup所有接口</br>    \- error状态只可以查询，删除</br>    \- delete状态的cluster在十五分钟内可以查询，十五分钟后无法查询到</br>\- 状态限制</br>  \- pending,reconciling,deleting状态不可以操作更新接口</br>  \- running状态可以操作cluster所有接口</br>  \- error状态只可以查询，删除</br>  \- delete状态的cluster在十五分钟内可以查询，十五分钟后无法查询到</br>|
|**createNodeGroup**|POST|创建k8s的nodeGroup</br>要求集群状态为running</br>|
|**deleteCluster**|DELETE|删除集群，以及集群的所有node节点，网络，云盘等所有资源。|
|**deleteNodeGroup**|DELETE|cluster 摘除 nodeGroup 并删除 nodeGroup|
|**describeCluster**|GET|查询单个集群详情。|
|**describeClusters**|GET|查询集群列表|
|**describeNodeGroup**|GET|查询单个节点组详情|
|**describeNodeGroups**|GET|查询节点组列表|
|**describeQuotas**|GET|查询(k8s 集群)配额|
|**describeServerConfig**|GET|查询(k8s 集群)服务配置信息|
|**modifyCluster**|PATCH|修改集群的 名称 和 描述。|
|**modifyNodeGroup**|PATCH|修改节点组的 名称 和 描述|
|**setNodeGroupSize**|POST|调整节点组实例数量|
