# Get Object

## 描述
该操作可以从OSS中取回Object,您必须对该Object有READ权限。如果该Object权限为公有读，则可在不进行签名认证的情况下取回Object。

注：支持通过x-amz-customize-back-source-url、x-amz-customize-back-source-param头指定数据拉取，指定后下载该对象时，将会拉取请求头提供的URL数据，并返回给用户。

## 请求
### 语法
```
GET /ObjectName HTTP/1.1
Host: <bucket>.s3.<region>.jcloudcs.com 
Date: <date>
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
Range:bytes=<byte_range>
```
### 请求参数
无请求参数

### 请求Header
除了共用的请求Header之外，该操作的实现还可以使用以下请求头，请求Header大小不超过8KB。

名称|描述|必须
---|---|---
Range|指定字节范围下载Object<br>Type: String<br>Default: None<br>Constraints: None|否
If-Modified-Since|若Object在指定时间后修改，则返回该Object，否则返回304（not modified）<br>Type: String<br>Default: None<br>Constraints: None|否
If-Unmodified-Since|若Object在指定时间后未修改，则返回该Object，否则返回412（precondition failed）。<br>Type: String<br>Default: None<br>Constraints: None|否
If-Match|如果ETag与指定的相同，则返回该Object，否则返回412（precondition failed）。<br>Type: String<br>Default: None<br>Constraints: None|否
IF-None-Match|如果ETag与指定的不同，则返回该Object，否则返回304（not modified）。<br>Type: String<br>Default: None<br>Constraints: None|否
x-amz-customize-back-source-url|回源地址，支持如 http://www.example.com:1000/path 格式。<br>Type：String<br>Default：None|否
x-amz-customize-back-source-param|base64编码的json字符串。参数同镜像回源设置。<br>Type：String<br>Default：None|否

注意：
+ 如果If-Match与If-Unmodified-Since同时在请求中，若If-Match为ture，If-Unmodified-Since为false，OSS将会返回 200 OK
+ 如果If-None-Match与If-Modified-Since同时在请求中，若If-None-Match为false，If-Modified-Since为true，OSS将会返回403 Not Modified

## 响应

### 响应Header

名称|描述
---|---
x-amz-storage-class|提供Object的存储类型信息。非标准存储情况下，OSS将会返回该Header
x-amz-restore|该对象的还原信息及副本生命周期

### 响应元素
无响应元素

## 示例
### 请求示例
```
GET /my-image.jpg HTTP/1.1
Host: oss-example.s3.<region>.jcloudcs.com 
Date: Mon, 3 Oct 2016 22:32:00 GMT
Authorization: <authorization string>
```
### 返回示例
```
HTTP/1.1 200 OK
x-amz-request-id: 318BC8BC148832E5
Date: Mon, 3 Oct 2016 22:32:00 GMT
Last-Modified: Wed, 12 Oct 2009 17:50:00 GMT
ETag: "fba9dede5f27731c9771645a39863328"
Content-Length: 434234

[434234 bytes of object data]
```
