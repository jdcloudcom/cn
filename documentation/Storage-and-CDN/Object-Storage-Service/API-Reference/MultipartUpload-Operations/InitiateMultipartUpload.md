# InitiateMultipartUpload

## MultipartUpload简介

除了通过PUT Object接口上传文件到OSS以外，OSS还提供了另外一种上传模式：Multipart Upload。用户可以在如下的应用场景内（但不仅限于此），使用Multipart Upload上传模式，如：

1.需要支持断点上传。

2.上传大文件（如500MB大小的文件）。

3.网络条件较差，和OSS的服务器之间的链接经常断开。

上传文件之前，无法确定上传文件的大小。

## InitiateMultipartUpload             

描述：使用Multipart Upload模式传输数据前，必须先调用该接口初始化一个新的Multipart Upload事件。用户通过该UploadId来进行Multipart Upload相关的操作，包括上传Multipart Upload所属的Part，合并所有Part，终止Multipart Upload，列出已上传的Part等。

**请求语法**

```
POST  /ObjectName?uploads HTTP/1.1
Host: BucketName.s.jcloud.com
x-jss-storage-class: STANDARD or REDUCED_REDUNDANCY       
Date: GMT  Date     
Authorization:  signatureValue#请参照"访问控制"     
```

**请求参数**

|名称|描述|
|-|-|
|x-jss-storage-class|Object的存储类型，默认值是"STANDARD"（标准存储）<br>支持"STANDARD"（标准存储）和"REDUCED_REDUNDANCY"（低频访问型）两种存储类型<br>注意：目前"REDUCED_REDUNDANCY"（低频访问型）仅华北机房支持<br>类型：字符串<br>默认值："STANDARD"（标准存储）|

**请求Header：**

|名称|描述|
|-|-|
|x-jss-server-side-encryption|指定上传该Object每个part时的服务器端是否加密<br>类型：boolean<br>合法值：true,false|

**响应元素**

|名称|描述|
|-|-|
|Bucket|初始化一个Multipart Upload事件的Bucket名称。<br>类型：字符串|
|Key|初始化一个Multipart Upload事件的Object名称。<br>类型：字符串|
|UploadId|唯一标示此次Multipart Upload事件的ID。<br>类型：字符串| 

细节分析

1.该操作计算认证签名的时候，需要加"?uploads"到CanonicalizedResource中。

2.初始化Multipart Upload请求，并不会影响已经存在的同名object。

3.服务器收到初始化Multipart Upload请求后，会返回一个json格式的请求体。该请求体内有三个元素：Bucket，Key和UploadID。请记录下其中的UploadID，以用于后续的Multipart相关操作。

4.初始化Multipart Upload请求时，若设置了x-jss-server-side-encryption Header，则在上传的每个part时，服务端会自动对每个part进行加密存储。

**请求示例**
```
POST /multipart.data?uploads   HTTP/1.1
Host: oss-example.s-bj.jcloud.com
x-jss-storage-class:   STANDARD      
Date: Wed, 12 Jul 2017 07:45:27   GMT  
Authorization: jingdong qbS5QXpLORrvdrmb:wYoTTKpqU1mZu4Dy3IlTRbCUx0w=   
```

**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jul 2017   07:45:27 GMT
Content-Type:   application/json;charset=UTF-8
Content-Length: 71
Connection: keep-alive
x-jss-request-id:   9891344770AD7F37
X-Trace: 200-1499845527038-0-0-18-46-46
 
{"Bucket":"youhe","Key":"multipart.data","UploadId":"9E417328F6B89F0B"}
```
