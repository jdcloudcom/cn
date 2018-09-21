# ListParts

该操作用来列出一个Multipart Upload中已经上传的Part。

**请求语法**

```
GET   /ObjectName?uploadId=UploadId HTTP/1.1
Host: BucketName. s.jcloud.com
Date: GMT   Date     
Authorization:   signatureValue#请参照“访问控制”
```
**请求参数**

|名称|描述|必要|
|-|-|-|
|uploadId|Multipart Upload事件的ID。<br>类型：字符串<br>默认值：无|是|

**响应元素**

|名称|描述|
|-|-|
|Bucket|Bucket名称<br>类型：字符串
|Key|Object名称<br>类型：字符串|
|UploadId|Upload事件ID<br>类型：字符串|
|StorageClass|Object的存储类型，默认值是"STANDARD"（标准存储）。<br>支持"STANDARD"（标准存储）和"REDUCED_REDUNDANCY"（低频访问型）两种存储类型类型：字符串默认值："STANDARD"（标准存储）|
|Part|保存Part信息的集合。<br>类型：List|
|PartNumber|标示Part的数字。<br>类型：Ingeter|
|LastModified|Part上传的时间。<br>类型：字符串|
|ETag|已上传Part内容的ETag。<br> 类型：字符串|
|Size|已上传Part大小。<br>类型：long|

细节分析

1.该操作必须指定UploadId，返回的Part数量最大为10000。

2.在OSS的返回结果按照Part号码升序排列。

3.由于网络传输可能出错，所以不推荐用List Part出来的结果（Part Number和ETag值）来生成最后Complete Multipart的Part列表。

**请求实例**

```
GET   /multipart.data?uploadId=9E417328F6B89F0B HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Date: Tue, 11 Jul 2017   12:40:40 GMT    
Authorization: jingdong   qbS5QXpLORrvdrmb:Ihjb1BaIk2pNGk11OCqBogLLL4c= 
```

**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 11 Jul 2017   12:40:40 GMT
Content-Type:   application/json;charset=UTF-8
Content-Length: 466
Connection: keep-alive
Vary: Accept-Encoding
Vary: Accept-Encoding
x-jss-request-id:   9206E7FB00121B2F
X-Trace:   200-1499776840209-0-0-19-45-45
 
{
      "Bucket": "youhe",
      "Key": "multipart.data",
      "UploadId": "9E417328F6B89F0B",
      "Part": [
          {
              "PartNumber": 1,
              "LastModified": "Tue, 11 Jul 2017 12:39:15 GMT",
              "ETag": "72cfb19c8e2791bd502ce951ebc64ad8",
              "Size": 204800
          },
          {
              "PartNumber": 2,
              "LastModified": "Tue, 11 Jul 2017 12:39:28 GMT",
              "ETag": "a2a8ab7bd93851a715c8137ea5d4c720",
              "Size": 409600
          },
          {
              "PartNumber": 3,
              "LastModified": "Tue, 11   Jul 2017 12:39:42 GMT",
              "ETag": "b0721b50ee0cb102eb1f0d8216c94848",
              "Size": 614400
          }
    ],
      "StorageClass": "STANDARD"
}
```
