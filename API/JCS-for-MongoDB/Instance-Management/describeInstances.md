# describeInstances


## 描述
查询实例信息

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |instanceId - 实例ID, 精确匹配<br>instanceName - 实例名称, 模糊匹配<br>instanceStatus - mongodb状态，精确匹配，支持多个.RUNNING：运行, ERROR：错误 ,BUILDING：创建中, DELETING：删除中, RESTORING：恢复中, RESIZING：变配中<br>chargeMode - 计费类型，精确匹配<br>|
|**pageNumber**|Integer|False| |页码；默认为1，取值范围：[1,∞)|
|**pageSize**|Integer|False| |分页大小；默认为10；取值范围[1, 100]|
|**sorts**|Sort[]|False| |createTime - 创建时间,asc（正序），desc（倒序）<br>|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### Sort
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**direction**|String|False| |排序条件的方向|
|**name**|String|False| |排序条件的名称|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**dbInstances**|DBInstance[]| |
|**pageNumber**|Integer| |
|**totalCount**|Integer| |
### DBInstance
|名称|类型|描述|
|---|---|---|
|**accountName**|String|默认用户名|
|**azId**|String[]|可取区ID，依次为主、从、隐藏节点所在可用区|
|**backupRetentionPeriod**|Integer|自动备份保留时间|
|**charge**|Charge|计费信息|
|**createTime**|String|创建时间|
|**dBName**|String|默认库名|
|**engine**|String|数据库类型|
|**engineVersion**|String|数据库版本|
|**instanceCPU**|Integer|CPU核数|
|**instanceClass**|String|实例规格代码|
|**instanceDomain**|String|域名|
|**instanceId**|String|实例ID|
|**instanceMemoryGB**|Integer|内存，单位GB|
|**instanceName**|String|实例名称|
|**instancePort**|String|应用访问端口|
|**instanceStatus**|String|实例状态.RUNNING：运行, ERROR：错误 ,BUILDING：创建中, DELETING：删除中, RESTORING：恢复中, RESIZING：变配中|
|**instanceStorageGB**|Integer|存储空间|
|**isSetSecurityIps**|Boolean|是否设置白名单，true：已设置，false：未设置|
|**preferredBackupWindow**|String|自动备份时间，如：00:00-02:00，表示0点到2点进行数据库自动备份|
|**preferredmaintenanceWindow**|String|系统维护时间，如：00:00-02:00，表示0点到2点进行系统维护|
|**replicaSetName**|String|副本集名称|
|**subnetId**|String|子网ID|
|**vpcId**|String|VPCID|
### Charge
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
