# 容器服务


## 简介
容器服务相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**associateElasticIp**|POST|容器绑定公网IP 绑定的是主网卡、主内网IP对应的弹性IP|
|**createContainers**|POST|创建一台或多台指定配置的实例|
|**createSecret**|POST|创建 secret|
|**deleteContainer**|DELETE|删除单个实例|
|**deleteSecret**|DELETE|删除 secret|
|**describeContainer**|GET|查询容器详情|
|**describeContainers**|GET|查询容器列表|
|**describeQuota**|GET|查询资源的配额|
|**describeSecret**|GET|查询 secret 详情|
|**describeSecrets**|GET|查询secret列表|
|**disassociateElasticIp**|POST|容器解绑公网IP 解绑的是主网卡、主内网IP对应的弹性IP|
|**getLogs**|GET|查询容器日志|
|**modifyContainerAttribute**|PATCH|修改容器属性|
|**startContainer**|POST|启动单个实例|
|**stopContainer**|POST|停止单个实例|
