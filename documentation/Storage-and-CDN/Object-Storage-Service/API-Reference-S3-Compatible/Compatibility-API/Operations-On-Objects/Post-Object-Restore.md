# POST Object restore

## 描述

该操作可以对存储类型为 GLACIER 的对象还原临时副本。还原时支持指定临时副本的生命周期，即在指定的时间段后，OSS会删除该临时副本。该操作不影响被还原的源对象。

还原已归档对象时，可以指定以下还原选项：
- Expedited：快速还原
- Standard：标准还原
- Bulk：批量还原

## 请求

### 请求语法
```
POST /ObjectName?restore HTTP/1.1
Host: <BUCKET_NAME>.s3.<REGION>.jdcloud-oss.com
Date: date
Authorization: authorization string

 request body 
```

### 请求参数
无请求参数

### 请求Header
无特殊Header

### 请求元素
请求Body的XML示例：
```
<RestoreRequest>
   <Days>2</Days> 
   <GlacierJobParameters>
     <Tier>Bulk</Tier>
   </GlacierJobParameters> 
</RestoreRequest> 
```

名称|描述|必须
-|-|-
RestoreRequest|取回信息的集合。<br>类型: Container |是
Days|取回的临时副本的生命周期。从Glacier恢复对象的最小天数为1。当对象副本达到指定生命周期后，OSS会将其从存储桶中删除。<br>类型：Positive Integer（正整数）<br>父标签：RestoreRequest|是
GlacierJobParameters|Glacier取回任务参数的集合。<br>类型：Container<br>父标签：RestoreRequest|否
Tier|还原选项，默认为Standard。<br>类型：Enum<br>有效值：Expedited、Standard、Bulk <br>父标签：GlacierJobParameters|否

## 响应

### 响应Header
无特殊Header
### 响应元素
无响应元素
### 特殊错误
Error Code|描述|HTTP Status Code
-|-|-
RestoreAlreadyInProgress|对象还原已经在处理中。|409 Conflict

## 示例
该请求从归档存储中还原photo1.jpg的副本，还原选项为Expedited，且该副本的生命周期为2天。
```
POST /photo1.jpg?restore HTTP/1.1
Host: <BUCKET_NAME>.s3.<REGION>.jdcloud-oss.com
Date: Mon, 22 Oct 2012 01:49:52 GMT
Authorization: authorization string
Content-Length: content length

<RestoreRequest>
  <Days>2</Days>
  <GlacierJobParameters>
    <Tier>Expedited</Tier>
  </GlacierJobParameters>
</RestoreRequest>
```
若该Bucket中没有还原对象的副本，OSS将会启动还原任务，并返回202 Accepted响应。
```
HTTP/1.1 202 Accepted
x-amz-request-id: 9F341CD3C4BA79E0
Date: Sat, 20 Oct 2012 23:54:05 GMT
Content-Length: 0
Server: JDCloudOSS
```

