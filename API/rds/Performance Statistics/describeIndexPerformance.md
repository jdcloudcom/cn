# describeIndexPerformance


## 描述
索引性能统计</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeIndexPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**db**|String|False||需要查询的数据库名，多个数据库名之间用英文逗号分隔，默认所有数据库|
|**pageNumber**|Integer|False||显示数据的页码，取值范围：[1,1000)，页码超过总页数时，显示最后一页，用于查询列表的接口|
|**pageSize**|Integer|False||每页显示的数据条数，默认为50，取值范围：[1,100]，只能为10的倍数|
|**queryType**|String|True||查询类型，不同的查询类型按照相应的字段从高到低返回结果。支持如下类型：Missing：缺失索引Size：索引大小，单位KBUpdates：索引更新次数Scans：表扫描次数Used：最少使用|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**indexPerformanceResult**|[IndexPerformanceResult[]](##IndexPerformanceResult)|当queryType为Missing时，该字段为空当queryType为其他值时，返回IndexPerformanceResult|
|**missingIndexResult**|[MissingIndexResult[]](##MissingIndexResult)|当queryType为Missing时，返回结果集为MissingIndexResult当queryType为其他值时，该字段为空|
|**pageNumber**|Integer|当前页码|
|**pageSize**|Integer|每页显示的数据条数|
|**totalCount**|Integer|总记录数|
### <a name="IndexPerformanceResult">IndexPerformanceResult</a>
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
### <a name="MissingIndexResult">MissingIndexResult</a>
|名称|类型|描述|
|---|---|---|
|**avgUserImpact**|Number|实现此缺失索引后，用户查询可能获得的平均百分比收益。 该值表示如果实现此缺失索引，则查询成本将按此百分比平均下降。|
|**db**|String|数据库名|
|**equalityColumns**|String|构成相等谓词的列的逗号分隔列表，谓词的形式如下：table.column =constant_value|
|**includedColumns**|String|构成不等谓词的列的逗号分隔列表，例如以下形式的谓词：table.column > constant_value“=”之外的任何比较运算符都表示不相等。|
|**inequalityColumns**|String|用于查询的涵盖列的逗号分隔列表,即创建索引的SQL语句中，Include后的字段|
|**table**|String|表名|
|**userScans**|Integer|由可能使用了组中建议索引的用户查询所导致的扫描次数。|
|**userSeeks**|Integer|由可能使用了组中建议索引的用户查询所导致的搜索次数。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```

```

## 返回示例
无
