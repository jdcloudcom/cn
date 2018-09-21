# 京东云缓存Redis接口


## 简介
缓存Redis相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createCacheInstance**|POST|创建一个指定配置的缓存Redis实例</br>规格性能：创建缓存Redis实例的规格，分为主从版和集群版两种规格。每种规格都有最大连接数，内网带宽上限，CPU处理能力，规格代码等信息，具体可查看：<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a></br>可用区：可用区是指在同一地域下，电力、网络等基础设施互相独立的物理区域。一个地域包含一个或多个可用区，同一地域下的多个可用区可以彼此连通。地域可用区详细信息可查询：<a href="https://www.jdcloud.com/help/detail/2222/isCatalog/1">地域可用区详情</a></br>私有网络：简称VPC，自定义的逻辑隔离网络空间，支持自定义网段划分、路由策略等。具体信息可查询：<a href="https://www.jdcloud.com/help/detail/1509/isCatalog/1">私有网络VPC详情</a></br>子网：子网是所属VPC IP地址范围内的IP地址块，简称subnet，在VPC下创建子网，同一VPC下子网的网段不可以重叠，不同VPC下子网的网段可以重叠。具体信息可查询：<a href="https://www.jdcloud.com/help/detail/1510/isCatalog/1">子网subnet详情</a></br>|
|**deleteCacheInstance**|DELETE|删除按配置计费、或包年包月已到期的单个缓存Redis实例，包年包月未到期不可删除</br>只有处于运行<b>running</b>或者错误<b>error</b>状态的可以删除，其余状态不可以删除</br>白名单用户不能删除包年包月已到期的云主机</br>|
|**describeCacheInstance**|GET|查询单个缓存Redis实例详情|
|**describeCacheInstances**|GET|查询缓存Redis实例列表及其实例信息，可分页查询，查询指定页码，指定分页大小和指定过滤条件|
|**describeInstanceClass**|GET|查询某区域下的实例规格列表|
|**describeUserQuota**|GET|查询账户配额信息|
|**modifyCacheInstanceAttribute**|PATCH|修改缓存Redis实例的资源名称、描述，二者至少选一|
|**modifyCacheInstanceClass**|POST|变更缓存Redis实例配置，只能变更运行状态的实例配置，变更配置的规格不能与之前的相同</br>预付费用户，从集群版变配到主从版，新规格的内存大小要大于老规格的内存大小，从主从版到集群版，新规格的内存大小要不小于老规格的内存大小</br>|
|**resetCacheInstancePassword**|POST|重置缓存Redis实例密码，支持免密操作|
