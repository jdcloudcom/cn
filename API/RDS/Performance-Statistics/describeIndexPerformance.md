# describeIndexPerformance


## 描述
根据用户定义的查询条件，获取索引性能的统计信息，并提供缺失索引及索引创建建议。用户可以根据这些信息查找与索引相关的性能瓶颈，并进行优化。<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeIndexPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**db**|String|False| |需要查询的数据库名，多个数据库名之间用英文逗号分隔，默认所有数据库|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,1000)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为50，取值范围：[1,100]，只能为10的倍数，用于查询列表的接口|
|**queryType**|String|True| |查询类型，不同的查询类型按照相应的字段从高到低返回结果。<br>支持如下类型：<br>Missing：缺失索引<br>Size：索引大小，单位KB<br>Updates：索引更新次数<br>Scans：表扫描次数<br>Used：最少使用<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**indexPerformanceResult**|IndexPerformanceResult[]|当queryType为Missing时，该字段为空<br>当queryType为其他值时，返回IndexPerformanceResult|
|**missingIndexResult**|MissingIndexResult[]|当queryType为Missing时，返回结果集为MissingIndexResult<br>当queryType为其他值时，该字段为空|
|**pageNumber**|Integer|当前数据的页码|
|**pageSize**|Integer|每页显示的数据条数|
|**totalCount**|Integer|总记录条数|
### IndexPerformanceResult
|名称|类型|描述|
|---|---|---|
|**db**|String|数据库名|
|**index**|String|索引名|
|**lastUserScan**|String|最近表扫描时间，格式为YYYY-MM-DD hh:mm:ss|
|**lastUserSeek**|String|最近索引搜索时间，格式为YYYY-MM-DD hh:mm:ss|
|**lastUserUpdate**|String|最近索引更新时间，格式为YYYY-MM-DD hh:mm:ss|
|**sizeKB**|Integer|索引大小，单位KB|
|**table**|String|表名|
|**userScans**|Integer|服务器启动以来，累计表扫描次数|
|**userSeeks**|Integer|服务器启动以来，累计索引搜索次数|
|**userUpdates**|Integer|服务器启动以来，累计索引更新次数|
### MissingIndexResult
|名称|类型|描述|
|---|---|---|
|**avgUserImpact**|Number|实现此缺失索引后，用户查询可能获得的平均百分比收益。 该值表示如果实现此缺失索引，则查询成本将按此百分比平均下降。|
|**db**|String|数据库名|
|**equalityColumns**|String|构成相等谓词的列的逗号分隔列表，谓词的形式如下：<br>table.column =constant_value|
|**includedColumns**|String|构成不等谓词的列的逗号分隔列表，例如以下形式的谓词：<br>table.column > constant_value<br>“=”之外的任何比较运算符都表示不相等。|
|**inequalityColumns**|String|用于查询的涵盖列的逗号分隔列表,即创建索引的SQL语句中，Include后的字段|
|**table**|String|表名|
|**userScans**|Integer|由可能使用了组中建议索引的用户查询所导致的扫描次数。|
|**userSeeks**|Integer|由可能使用了组中建议索引的用户查询所导致的搜索次数。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
