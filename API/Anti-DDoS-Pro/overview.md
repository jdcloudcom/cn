# 京东云IP高防相关接口


## 简介
京东云IP高防相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**checkName**|GET|检测实例名称是否合法|
|**createForwardRule**|POST|添加非网站类规则|
|**createInstance**|POST|创建实例|
|**createWebRule**|POST|添加网站类规则|
|**deleteForwardRule**|DELETE|删除非网站规则|
|**deleteWebRule**|DELETE|删除网站规则|
|**describeAlarmConfig**|GET|查询告警配置|
|**describeAttackStatistics**|GET|查询攻击次数及流量峰值|
|**describeAttackTypeCount**|GET|查询各类型攻击次数|
|**describeCCAttackLogDetails**|GET|查询 CC 攻击日志详情|
|**describeCCAttackLogs**|GET|查询 CC 攻击日志|
|**describeCCDefaultThresholds**|GET|查询 CC 自定义默认阈值|
|**describeCCGraph**|GET|CC 防护流量报表|
|**describeCertInfo**|POST|查询证书预览信息|
|**describeDDoSAttackLogs**|GET|查询 DDos 攻击日志|
|**describeDDoSGraph**|GET|DDos 防护流量报表|
|**describeForwardRule**|GET|查询非网站类规则|
|**describeForwardRules**|GET|查询某个实例下的非网站转发配置|
|**describeFwdGraph**|GET|转发流量报表|
|**describeInstance**|GET|查询实例|
|**describeInstances**|GET|查询实例列表|
|**describeNameList**|GET|查询高防实例名称列表|
|**describeProtectionStatistics**|GET|查询高防实例防护统计信息|
|**describeVpcIpList**|GET|查询用户的京东云 IP 资源|
|**describeWebRule**|GET|查询网站类规则|
|**describeWebRules**|GET|查询某个实例下的网站类规则|
|**disableCCIpLimit**|POST|关闭 CC 防护每 IP 的限速|
|**disableCCObserverMode**|POST|关闭实例 CC 防护的观察者模式|
|**disableInstanceCC**|POST|关闭实例 CC 防护|
|**disableInstanceIpBlackList**|POST|禁用实例 IP 黑名单|
|**disableInstanceIpWhiteList**|POST|禁用实例 IP 白名单|
|**disableInstanceUrlWhiteList**|POST|禁用实例 Url 白名单|
|**disableWebRuleCC**|POST|网站类规则禁用CC|
|**downloadCCAttackLogDetails**|GET|下载 CC 攻击日志详情|
|**downloadCCAttackLogs**|GET|下载 CC 攻击日志|
|**downloadDDoSAttackLogs**|GET|下载 DDos 攻击日志|
|**enableCCIpLimit**|POST|开启 CC 防护每 IP 的限速|
|**enableCCObserverMode**|POST|开启实例 CC 防护的观察者模式|
|**enableInstanceCC**|POST|开启实例 CC 防护|
|**enableInstanceIpBlackList**|POST|启用实例 IP 黑名单|
|**enableInstanceIpWhiteList**|POST|启用实例 IP 白名单|
|**enableInstanceUrlWhiteList**|POST|启用实例 Url 白名单|
|**enableWebRuleCC**|POST|网站类规则开启CC|
|**modifyAlarmConfig**|POST|更新告警配置|
|**modifyCertInfo**|POST|编辑证书|
|**modifyEPB**|POST|更新实例弹性防护带宽|
|**modifyForwardRule**|PATCH|更新非网站类规则|
|**modifyInstanceCC**|POST|设置实例 CC 防护|
|**modifyInstanceIpBlackList**|POST|设置实例 IP 黑名单|
|**modifyInstanceIpWhiteList**|POST|设置实例 IP 白名单|
|**modifyInstanceName**|POST|修改实例名称|
|**modifyInstanceUrlWhiteList**|POST|设置实例 Url 白名单|
|**modifyWebRule**|PATCH|更新网站类规则|
|**setCCIpLimit**|POST|设置实例 CC 防护每 IP 限速|
|**switchForwardRuleOrigin**|POST|非网站类规则切换成回源状态|
|**switchForwardRuleProtect**|POST|非网站类规则切换成防御状态|
|**switchWebRuleOrigin**|POST|网站类规则切换成回源状态|
|**switchWebRuleProtect**|POST|网站类规则切换成防御状态|
