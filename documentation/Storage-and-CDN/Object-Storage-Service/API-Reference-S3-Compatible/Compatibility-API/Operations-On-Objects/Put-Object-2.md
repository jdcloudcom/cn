# Put Object

## 描述
该操作可将一个object上传到bucket中，要求操作者有bucket的WRITE权限。

您可以使用Content-MD5 来确保数据完整性，OSS将根据提供的MD5校验Object，若不匹配，则返回错误。另外，您也可以在上传object计算MD5，并与返回的ETag进行比对。

## 请求
### 语法
```
PUT /ObjectName HTTP/1.1
Host: <bucket>.s3.<region>.jdcloud-oss.com
Date: <date>
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
```

### 请求元素
无请求元素

### 请求Header
该操作可使用以下请求Header以及通用的请求Header（请参阅常见请求Header）；Header大小不超过8KB。

名称|描述|必须
---|---|---
Cache-Control|指定该Object被下载时的网页的缓存行为；更详细描述请参照RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Disposition|指定返回的Object该以何种形式展示,长度限制为100个字节；更详细描述请参照RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Encoding|它的值表示消息主体进行了何种方式的内容编码转换，用来告知客户端应该怎样解码才能获取在 Content-Type 中标示的媒体类型内容；更详细描述请访问RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Length|Object的大小，单位为byte；更详细描述请参照RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|是
Content-MD5|对报文主体进行MD5算法获得128位二进制数，再通过Base64编码写入Content-MD5。可用于数据完整性检查。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Type|表示请求中的MIME类型。<br>Type: String<br>Default: binary/octet-stream<br>Valid Values: MIME types<br>Constraints: None|否
Expect|客户端使用Expect告知OSS，期望出现某种特定的行为。若OSS无法做出回应而发生错误时，请求报文主体将不会发送。<br>Type: String<br>Default: None<br>Valid Values: 100-continue<br>Constraints: None|否
Expires|Object缓存过期时间。<br>Type: String<br>Default: None<br>Constraints: None|否
x-amz-storage-class| Object存储类型，如果未指定，默认为标准存储。<br>Type: Enum<br>Default: STANDARD<br>Valid Values: STANDARD、 GLACIER、REDUCED_REDUNDANCY  |否

## 响应
### 响应Header
无特殊Header

### 响应元素
无特殊响应元素

## 示例
### 请求示例
```
PUT /my-image.jpg HTTP/1.1
Host: oss-example.s3.<region>.jdcloud-oss.com 
Date: Wed, 12 Oct 2009 17:50:00 GMT
Authorization: <authorization string>
Content-Type: text/plain
Content-Length: 11434
Expect: 100-continue
[11434 bytes of object data]
```
### 响应示例
```
HTTP/1.1 100 Continue

HTTP/1.1 200 OK
x-amz-request-id: 0A49CE4060975EAC
Date: Wed, 12 Oct 2009 17:50:00 GMT
ETag: "1b2cf535f27731c974343645a3985328"
Content-Length: 0
Connection: close
Server: JDCloudOSS
```
