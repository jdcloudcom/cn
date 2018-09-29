# getMonitor


## 描述
查看主域名的监控项的配置以及状态

## 请求方式
GET

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/monitor

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |当前页数，起始值为1，默认为1|
|**pageSize**|Integer|False| |分页查询时设置的每页行数|
|**searchValue**|String|False| |查询的值|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer|当前页面网站监控项的个数|
|**dataList**|Monitor[]|当前页面的网站监控项的列表|
|**totalCount**|Integer|所有网站监控项的个数|
|**totalPage**|Integer|所有网站监控项的页数|
### Monitor
|名称|类型|描述|
|---|---|---|
|**alarmLimit**|Integer|连续几次触发报警|
|**canRecover**|Boolean|现在是否可以恢复|
|**canSwitch**|Boolean|现在是否可以切换|
|**clusters**|String|机房探测点的集合|
|**domainName**|String|主域名|
|**hostStatus**|Integer|主机状态，0正常，1异常|
|**hostValue**|String|监控对象|
|**id**|Integer|监控项ID|
|**ipBackup01**|String|备用地址1|
|**ipBackup01Status**|Integer|备用地址1的状态，0正常，1异常|
|**ipBackup01Type**|Integer|备用地址1的类型，1为ip 2为域名|
|**ipBackup02**|String|备用地址2|
|**ipBackup02Status**|Integer|备用地址2的状态，0正常，1异常|
|**ipBackup02Type**|Integer|备用地址1的类型，1为ip 2为域名|
|**manualBackup**|String|手动切换的地址|
|**manualBackupStatus**|Integer|手动切换的地址的状态，0正常，1异常|
|**manualBackupType**|Integer|手动切换的地址的类型，1为ip 2为域名|
|**monitorEnable**|Integer|监控状况 开启监控 2，暂停监控 4|
|**monitorFreq**|Integer|监控频率，单位s|
|**monitorPort**|Integer|监控端口|
|**monitorRule**|Integer|不做任何修改0，强制暂停解析记录1，自动切换到备用地址2|
|**monitorUri**|String|监控路径|
|**notifyEmail**|String|邮箱地址|
|**notifyEmailEnable**|Integer|不发送邮件0， 发送邮件1|
|**notifyMsgBarEnable**|Integer|不发送通知栏 0， 发送通知栏 1|
|**notifySms**|String|手机号码|
|**notifySmsEnable**|Integer|不发送短信 0， 发送短信 1|
|**protocol**|Integer|https 0，https 1|
|**stopRecoverRule**|Integer|0自动恢复 1手动恢复|
|**subDomainName**|String|子域名|
|**switchRecoverRule**|Integer|0自动恢复至主host 1手动恢复至主host|
|**type**|Integer|1为A记录，2为CNAME|
|**usedType**|Integer|使用记录，host_value 0，ip_backup_01 1，ip_backup_02 2，cname_backup 3|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
