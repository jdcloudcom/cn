# ListMultipartUploads

List Multipart Uploads可以列出指定Bucket下还未完成的MultipartUpload，请求时可以通过一些查询条件来限制返回的结果。该操作最多返回10000个Multipart Upload。如果符合查询条件的结果超过10000个。超过10000个Multipart Upload，会返回 400错误，错误码返回 TooManyMultipartUploads。

**请求语法**
```
GET /BucketName?uploads HTTP/1.1
Host: BucketName.s-bj.jcloud.com
Date: GMT Date
Authorization: signatureValue
```

**请求参数**

|名称|描述|
|-|-|
|prefix|限定返回的object key必须以prefix作为前缀。注意使用prefix查询时，返回的key中仍会包含prefix。<br>类型：字符串|

**响应元素**

|名称|描述|
|-|-|
|Bucket|Bucket名称<br>类型：字符串|
|Key|初始化Multipart Upload事件的Object名字<br>类型：字符串|
|UploadId|Multipart Upload事件的ID<br>类型：字符串|
|Initiated|Multipart Upload事件初始化的时间<br>类型：日期|
|Enable-Encryption|是否对上传的内容进行加密<br>有效值：TRUE(进行加密)，FALSE(不进行加密)<br>类型：枚举字符串|
|StorageClass|Object的存储类型，默认值是"STANDARD"（标准存储）<br>支持"STANDARD"（标准存储）和"REDUCED_REDUNDANCY"（低频访问型）两种存储类型<br>注意：目前"REDUCED_REDUNDANCY"（低频访问型）仅华北机房支持<br>类型：字符串<br>默认值："STANDARD"（标准存储）|

细节分析

1."max-uploads"参数最大值为10000。

2.返回的结果按照Key和UploadId的字典序排序。  

**请求示例**

```
GET   /?uploads HTTP/1.1
Date:   Wed, 12 Jul 2017 13:58:14 GMT
Authorization:   jingdong   298718BEDE59FF1B2E96A3152937D37B:YVbn+CqITQzQNRWzVKcxPq3V0PY=
Host: oss-test.s-bj.jcloud.com
Connection:   Keep-Alive
```

**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jul 2017   13:58:14 GMT
Content-Type:   application/json;charset=UTF-8
Content-Length: 714
Connection: keep-alive
x-jss-request-id:   A9E0EE26B6EF677E
 
{"Bucket":"oss-test","Prefix":null,"Upload":[{"Key":"oss-test-mul1","UploadId":"97D11DAE98672320",
"Initiated":"Wed,   12 Jul 2017 13:58:02 GMT","Enable-Encryption":"false","Summary":null,"StorageClass":"STANDARD"},
{"Key":"oss-test-mul2","UploadId":"8238F7E35F3FFCFE","Initiated":"Wed,   12 Jul 2017 13:58:02   GMT",
"Enable-Encryption":"false","Summary":null,"StorageClass":"STANDARD"},{"Key":"oss-test-mul3",
"UploadId":"90895A4BB2A635DF","Initiated":"Wed,   12 Jul 2017 13:58:02   GMT",
"Enable-Encryption":"false","Summary":null,"StorageClass":"STANDARD"},
{"Key":"oss-test-mul4","UploadId":"857A7712C57EA243","Initiated":"Wed,   12 Jul 2017 13:58:02   GMT",
"Enable-Encryption":"false","Summary":null,"StorageClass":"STANDARD"}]}
```
