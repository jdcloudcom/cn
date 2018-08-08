# describeTopic


## 描述
查看指定主题

## 请求方式
GET

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/topic

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True|||


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**topic**|[AddTopic](##AddTopic)||
### <a name="AddTopic">AddTopic</a>
|名称|类型|描述|
|---|---|---|
|**parameterList**|Object[]|归档相关的具体参数|
|**target**|[Target](##Target)||
|**topic**|[Topic](##Topic)||
### <a name="Target">Target</a>
|名称|类型|描述|
|---|---|---|
|**cycle**|Integer|进行归档任务的时间周期|
|**name**|String|需要归档的目的|
|**recordSize**|Integer|当达到这个数据量时开始归档|
### <a name="Topic">Topic</a>
|名称|类型|描述|
|---|---|---|
|**archived**|Integer|是否归档（0：未归档，1：已归档）|
|**lifecycle**|Integer|数据写入后的保留时间|
|**name**|String|流数据总线中topic的名字|
|**remark**|String|备注|
|**shardNum**|Integer|流数据总线shard的数量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|ERROR|

## 请求示例
GET
```

```

## 返回示例
无
