# describeTopic


## 描述
查询指定主题,如果已归档会返回归档信息

## 请求方式
GET

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/topic

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**topic**|TopicModel| |
### TopicModel
|名称|类型|描述|
|---|---|---|
|**parameterList**|Object[]|归档相关的具体参数，需要对归档进行新建，更新，删除，修改对应参数值即可。<br>ossFlag，bucketName，directory，objectName 这四个参数值与ossFlag有关，若ossFlag为false，后面三个可为空，若为true，后面三个为异常数据保存位置，按需要填写即可。<br> 1）如果归档到数据计算服务需要传database，table，type，example，delimiter，targetColumn，analysisColumn，partsTargetColumn，partsAnalysisColumn。<br>2）如果归档到JFS需要传bucket，prefix，infix。<br>3）如果归档到京东云 Elasticsearch需要传host，port，indexType，idType，indexName，indexReferField，timestampFieldFormat，timestampIndexFormat，typeName，idReferField，noResolve，username，password。<br> 4）如果归档到mysql，则需要传host，database，table，username，password，type，example，delimiter。 <br>5)如果要归档到京东云数据库则需要传rdsId，database，table，username，password，type，example，delimiter。|
|**target**|Target| |
|**topic**|Topic| |
### Target
|名称|类型|描述|
|---|---|---|
|**cycle**|Integer|进行归档任务的时间周期|
|**name**|String|需要归档的目的地|
|**recordSize**|Integer|当达到这个数据量时开始归档|
### Topic
|名称|类型|描述|
|---|---|---|
|**archived**|Integer|是否归档（0：未归档，1：已归档）|
|**id**|Integer|主题id|
|**lifecycle**|Integer|数据写入后的保留时间|
|**name**|String|流数据总线中topic的名字|
|**partitionNum**|Integer|分区|
|**remark**|String|备注|
|**shardNum**|Integer|流数据总线shard的数量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT FOUND|
