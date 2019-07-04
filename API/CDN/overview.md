# JDCLOUD CDN Operation And Query API


## 简介
API related to CDN instances


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**batchCreate**|POST|创建点播加速域名|
|**batchCreateLiveDomain**|POST|创建直播域名|
|**batchDeleteDomainGroup**|POST|批量删除域名组|
|**createCacheRule**|POST|添加缓存规则|
|**createDomain**|POST|创建点播加速域名|
|**createDomainGroup**|POST|创建域名组|
|**createLiveDomainPrefecthTask**|POST|创建直播预热任务|
|**createRefreshTask**|POST|创建刷新预热任务|
|**createRefreshTaskForCallback**|POST|创建刷新预热回调任务|
|**createRefreshTaskForCallbackV2**|POST|创建刷新预热回调任务|
|**deleteCacheRule**|DELETE|删除缓存规则|
|**deleteDomain**|DELETE|删除加速域名|
|**deleteForbiddenStream**|POST|删除禁播流|
|**deleteHttpHeader**|PUT|删除httpHeader|
|**getAllUpperNodeIpList**|GET|获取所有上层节点的ip|
|**getDomainDetail**|GET|查询加速域名详情|
|**getDomainList**|GET|查询加速域名接口|
|**getDomainListByFilter**|POST|通过标签查询加速域名接口|
|**getSslCertDetail**|GET|查看证书详情|
|**getSslCertList**|GET|查看证书列表|
|**operateIpBlackList**|PUT|设置ip黑名单状态|
|**operateLiveDomainIpBlackList**|POST|开启或关闭ip黑名单|
|**operateShareCache**|POST|泛域名共享缓存|
|**previewCertificate**|POST|预览证书|
|**queryAccesskeyConfig**|GET|查询url鉴权|
|**queryAreaIspList**|GET|查找地域运营商列表|
|**queryDefaultHttpHeaderKey**|GET|查询默认http header头部参数列表|
|**queryDomainConfig**|GET|查询域名配置信息|
|**queryDomainGroupDetail**|GET|查询域名组详情|
|**queryDomainGroupList**|GET|查询域名组接口|
|**queryDomainLog**|GET|查询日志|
|**queryDomainsLog**|POST|批量域名查询日志|
|**queryDomainsNotInGroup**|GET|查询未分组域名|
|**queryFollowRedirect**|GET|查询回源302跳转信息|
|**queryFollowSourceProtocol**|GET|查询协议跟随回源|
|**queryHttpHeader**|GET|查询http header头|
|**queryIpBlackList**|GET|查询ip黑名单|
|**queryLiveDomainApps**|GET|查询直播域名app列表|
|**queryLiveDomainDetail**|GET|查询直播域名详情|
|**queryLivePrefetchTask**|POST|查询直播预热任务|
|**queryLiveStatisticsAreaDataGroupBy**|POST|分地区及运营商查询统计数据|
|**queryLiveStatisticsData**|POST|查询统计数据|
|**queryLiveTrafficGroupSum**|POST|查询统计数据并进行汇总加和|
|**queryMixStatisticsData**|POST|查询统计数据|
|**queryMixStatisticsWithAreaData**|POST|分地区及运营商查询统计数据|
|**queryMixTrafficGroupSum**|POST|查询统计数据并进行汇总加和|
|**queryMonitor**|GET|查询源站监控信息|
|**queryOnlineBillingType**|GET|设置线上计费方式|
|**queryOssBuckets**|GET|查询oss存储域名|
|**queryPushDomainORAppOrStream**|GET|查询用户推流域名app名/流名|
|**queryRefreshTask**|GET|查询刷新预热任务|
|**queryRefreshTaskById**|GET|根据taskId查询刷新预热任务|
|**queryRefreshTaskByIds**|POST|根据taskIds查询刷新预热任务|
|**queryStatisticsData**|POST|查询统计数据|
|**queryStatisticsDataGroupByArea**|POST|分地区及运营商查询统计数据|
|**queryStatisticsDataGroupSum**|POST|查询统计数据并进行汇总加和|
|**queryStatisticsTopIp**|POST|查询TOP IP|
|**queryStatisticsTopUrl**|POST|查询TOP Url|
|**queryUserAgent**|GET|设置userAgent信息|
|**setAccesskeyConfig**|POST|设置url鉴权|
|**setFollowRedirect**|POST|设置回源302跳转|
|**setFollowSourceProtocol**|POST|设置协议跟随回源|
|**setHttpHeader**|POST|添加httpHeader|
|**setHttpType**|POST|设置http协议|
|**setIgnoreQueryString**|POST|设置忽略参数|
|**setIpBlackList**|POST|设置ip黑名单|
|**setLiveDomainAccessKey**|POST|设置URL鉴权|
|**setLiveDomainBackSource**|POST|设置直播域名回源信息|
|**setLiveDomainBackSourceHost**|POST|设置直播域名回源host|
|**setLiveDomainIpBlackList**|POST|设置直播域名ip黑名单|
|**setLiveDomainRefer**|POST|设置域名refer防盗链|
|**setMonitor**|POST|设置源站监控信息|
|**setOnlineBillingType**|POST|设置线上计费方式|
|**setProtocolConvert**|POST|设置转协议|
|**setRange**|POST|设置range参数|
|**setRefer**|POST|设置域名refer|
|**setSource**|POST|设置源站信息|
|**setUserAgentConfig**|POST|设置userAgent信息|
|**setVideoDraft**|POST|设置视频拖拽|
|**startDomain**|POST|启动加速域名|
|**stopDomain**|POST|停止加速域名|
|**stopMonitor**|POST|停止源站监控|
|**updateCacheRule**|PUT|修改缓存规则|
|**updateDomainGroup**|POST|更新域名组|
|**uploadCert**|POST|上传证书|
