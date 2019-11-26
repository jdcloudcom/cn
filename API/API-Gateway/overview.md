# API网关


## 简介
API网关相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**authorizedApiGroupList**|GET|查询所有已授权api分组列表|
|**batchOffline**|POST|批量下线|
|**bindGroupAuth**|POST|绑定分组|
|**bindGroupKey**|POST|绑定分组|
|**bindGroupPolicy**|POST|绑定|
|**checkApiNameExist**|POST|创建API时，检查API名称是否重复,返回重复的apiId,如果没有返回空|
|**checkAuthExist**|POST|检查accessAuth是否重复|
|**checkGroupNameExist**|POST|检查分组名称是否重复,返回重复的apiGroupId,如果没有返回空|
|**checkKeyExist**|POST|检查AccessKey是否重复|
|**checkPin**|POST|校验pin是否存在|
|**checkPolicyName**|PATCH|检查策略名是否重复|
|**checkRevisionExist**|POST|检查版本号是否重复,返回重复的版本号,如果没有返回空|
|**createAccessAuth**|POST|创建访问授权|
|**createAccessKey**|POST|创建密钥|
|**createApiGroup**|POST|创建API分组|
|**createApis**|POST|创建api|
|**createBackendConfig**|POST|开通后端配置|
|**createKey**|POST|创建key|
|**createRateLimitPolicy**|POST|创建流控策略|
|**createRevision**|POST|创建修订版本|
|**createSubscriptionKey**|POST|创建密钥|
|**createUserDomain**|POST|添加用户域名|
|**deleteAccessAuth**|DELETE|删除访问授权|
|**deleteAccessKey**|DELETE|删除密钥|
|**deleteApi**|DELETE|删除api|
|**deleteApiByName**|DELETE|删除api|
|**deleteApiGroup**|DELETE|删除单个API分组|
|**deleteBackendConfig**|DELETE|删除后端配置|
|**deleteRateLimitPolicy**|DELETE|删除单个流控策略|
|**deleteRevision**|DELETE|删除单个修订版本|
|**deleteSubscriptionKey**|DELETE|删除密钥|
|**deleteUserDomain**|DELETE|删除用户域名接口|
|**deploy**|POST|发布版本|
|**describeApiGroup**|GET|查询API分组详情|
|**describeApiGroups**|GET|查询分组|
|**describeBackendConfig**|GET|查询backendConfig|
|**describeBackendConfigs**|GET|查询指定环境下的所有后端配置|
|**describeDeployment**|GET|查询该版本的部署详情|
|**describeDeployments**|GET|查询部署列表|
|**describeIsDeployApiGroups**|GET|查询分组|
|**describeRevisions**|GET|查询修订版本列表|
|**getRevisionIds**|GET|查询分组内全部修订版本号|
|**modifyApiGroupAttribute**|PUT|修改API分组信息|
|**modifyRevision**|PATCH|修改单个修订版本|
|**offline**|POST|下线|
|**queryAccessAuth**|GET|查询单个访问授权|
|**queryAccessAuths**|GET|查询访问授权列表|
|**queryAccessKey**|GET|查询单个密钥|
|**queryAccessKeys**|GET|查询密钥列表|
|**queryApi**|GET|查询单个api|
|**queryApis**|GET|查询api列表|
|**queryAuthGroupList**|GET|查询可绑定部署列表|
|**queryBindGroupAuth**|GET|查询已绑定详情|
|**queryBindGroupKey**|GET|查询绑定分组详情|
|**queryBindGroupPolicy**|GET|查询绑定部署详情|
|**queryKeyGroupList**|GET|查询可绑定部署列表|
|**queryKeyInfo**|GET|查询key详情|
|**queryKeys**|GET|查询key列表|
|**queryPolicyGroupList**|GET|查询可绑定部署列表|
|**queryRateLimitPolicies**|GET|查询流控策略列表|
|**queryRateLimitPolicy**|GET|查询单个流控策略|
|**queryRevision**|GET|查询某版本对应的api|
|**querySubscriptionKey**|GET|查询单个密钥|
|**querySubscriptionKeys**|GET|查询密钥列表|
|**queryUcAccessKeys**|GET|查询密钥列表|
|**queryUserDomains**|GET|查询domian列表|
|**resetKey**|PUT|重置key的acesskey和secretkey|
|**updateAccessAuth**|PATCH|更新访问授权|
|**updateAccessKey**|PATCH|更新密钥|
|**updateApi**|PUT|修改api|
|**updateApiByName**|PUT|修改api|
|**updateBackendConfig**|PATCH|修改后端配置|
|**updateKey**|PATCH|修改key信息|
|**updateRateLimitPolicy**|PATCH|修改流控策略|
|**updateSubscriptionKey**|PATCH|更新密钥|
