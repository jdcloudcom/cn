# addTopic


## 描述
创建topic

## 请求方式
POST

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/topic

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**topicModel**|[AddTopic](##AddTopic)|True|||

### <a name="AddTopic">AddTopic</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parameterList**|Object[]|False||归档相关的具体参数|
|**target**|[Target](##Target)|False|||
|**topic**|[Topic](##Topic)|False|||
### <a name="Target">Target</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cycle**|Integer|False||进行归档任务的时间周期|
|**name**|String|False||需要归档的目的|
|**recordSize**|Integer|False||当达到这个数据量时开始归档|
### <a name="Topic">Topic</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**archived**|Integer|False||是否归档（0：未归档，1：已归档）|
|**lifecycle**|Integer|False||数据写入后的保留时间|
|**name**|String|False||流数据总线中topic的名字|
|**remark**|String|False||备注|
|**shardNum**|Integer|False||流数据总线shard的数量|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**message**|String|状态信息|
|**status**|Boolean||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|ERROR|

## 请求示例
POST
```

```

## 返回示例
无
