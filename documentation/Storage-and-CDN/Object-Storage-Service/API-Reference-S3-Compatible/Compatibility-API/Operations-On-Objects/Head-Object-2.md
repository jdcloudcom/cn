# Head Object

## 描述
该操作将返回Object的元数据，需有Object的READ权限。

## 请求

### 语法
```
HEAD /ObjectName HTTP/1.1
Host: <bucket>.s3.<region>.jdcloud-oss.com 
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
Date: <date>
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

注意：
+ 如果If-Match与If-Unmodified-Since同时在请求中，若If-Match为ture，If-Unmodified-Since为false，OSS将会返回 200 OK
+ 如果If-None-Match与If-Modified-Since同时在请求中，若If-None-Match为false，If-Modified-Since为true，OSS将会返回403 Not Modified

### 请求元素
无请求元素

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
HEAD /my-image.jpg HTTP/1.1
Host: oss-example.s3.<region>.jdcloud-oss.com
Date: Wed, 28 Oct 2009 22:32:00 GMT
Authorization: <authorization string>
```
### 响应示例
```
HTTP/1.1 200 OK
x-amz-request-id: 318BC8BC143432E5
Date: Wed, 28 Oct 2009 22:32:00 GMT
Last-Modified: Sun, 1 Jan 2006 12:00:00 GMT
ETag: "fba9dede5f27731c9771645a39863328"
Content-Length: 434234
Content-Type: text/plain
Connection: close
Server: JDCloudOSS
```





