# 京东云IP高防相关接口


## 简介
京东云IP高防相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**ccGraph**|GET|转发流量报表|
|**createForwardRule**|POST|添加非网站类规则|
|**createInstance**|POST|创建实例|
|**createWebRule**|POST|添加网站类规则|
|**ddosGraph**|GET|ddos防护报表|
|**deleteForwardRule**|DELETE|删除某条非网站规则|
|**deleteWebRule**|DELETE|删除某条网站规则|
|**describeCcAttackLogDetails**|GET|查询cc攻击日志详情|
|**describeCcAttackLogs**|GET|查询cc攻击日志|
|**describeDDosAttackLogs**|GET|查询DDos攻击日志|
|**describeForwardRule**|GET|查询某条非网站类规则|
|**describeForwardRules**|GET|查询某个实例下的非网站转发配置|
|**describeInstance**|GET|查询实例|
|**describeInstances**|GET|查询实例列表|
|**describeWebRule**|GET|查询某条网站类规则|
|**describeWebRules**|GET|查询某个实例下的网站类规则|
|**disableCcIpLimit**|POST|关闭CC防护每ip的限速|
|**disableCcObserverMode**|POST|关闭实例CC防护的观察者模式|
|**disableInstanceCC**|POST|关闭实例CC防护|
|**disableInstanceIpBlackList**|POST|禁用实例ip黑名单|
|**disableInstanceIpWhiteList**|POST|禁用实例ip白名单|
|**disableInstanceUrlWhiteList**|POST|禁用实例url白名单|
|**disableWebRuleCC**|POST|网站类规则禁用CC|
|**enableCcIpLimit**|POST|开启CC防护每ip的限速|
|**enableCcObserverMode**|POST|开启实例CC防护的观察者模式|
|**enableInstanceCC**|POST|开启实例CC防护|
|**enableInstanceIpBlackList**|POST|启用实例ip黑名单|
|**enableInstanceIpWhiteList**|POST|启用实例ip白名单|
|**enableInstanceUrlWhiteList**|POST|启用实例url白名单|
|**enableWebRuleCC**|POST|网站类规则开启CC|
|**fwdGraph**|GET|转发流量报表|
|**modifyForwardRule**|PATCH|更新某条非网站类规则|
|**modifyInstanceCC**|POST|设置实例CC防护|
|**modifyInstanceIpBlackList**|POST|设置实例ip黑名单|
|**modifyInstanceIpWhiteList**|POST|设置实例ip白名单|
|**modifyInstanceName**|POST|修改实例名称|
|**modifyInstanceUrlWhiteList**|POST|设置实例url白名单|
|**modifyWebRule**|PATCH|更新某条网站类规则|
|**setCcIpLimit**|POST|设置实例CC防护每ip限速|
|**switchForwardRuleOrigin**|POST|非网站类规则切换成回源状态|
|**switchForwardRuleProtect**|POST|非网站类规则切换成防御状态|
|**switchWebRuleOrigin**|POST|网站类规则切换成回源状态|
|**switchWebRuleProtect**|POST|网站类规则切换成防御状态|
