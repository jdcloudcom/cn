# Initiate Multipart Upload

## 描述
该操作将会开启分片上传并返回上传ID。该上传ID用于关联特定的分段上传的所有分片。您可以在后续每次执行分片上传请求中指定此上传ID；也可以在最后的请求中指定此上传ID完成分片上传。

## 请求
### 语法
```
POST /ObjectName?uploads HTTP/1.1
Host: <bucket>.s3.<region>.jdcloud-oss.com
Date: <date>
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
```
### 请求参数
无请求参数
### 请求Header

名称|描述|需要
---|---|---
Cache-Control|在整个请求/响应链中指定缓存行为。<br>Type: String<br>Default: None|否
Content-Disposition|指定返回的Object该以何种形式展示；更详细描述请参照RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Encoding|它的值表示消息主体进行了何种方式的内容编码转换，用来告知客户端应该怎样解码才能获取在 Content-Type 中标示的媒体类型内容；更详细描述请访问RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Length|Object的大小，单位为byte；更详细描述请参照RFC2616。<br>Type: String<br>Default: None<br>Constraints: None|是
Content-MD5|对报文主体进行MD5算法获得128位二进制数，在通过Base64编码写入Content-MD5。可用于数据完整性检查。<br>Type: String<br>Default: None<br>Constraints: None|否
Content-Type|表示请求中的MIME类型。<br>Type: String<br>Default: binary/octet-stream<br>Valid Values: MIME types<br>Constraints: None|否
Expect|客户端使用Expect告知OSS，期望出现某种特定的行为。若OSS无法做出回应而发生错误时，请求报文主体将不会发送。<br>Type: String<br>Default: None<br>Valid Values: 100-continue<br>Constraints: None|否
Expires|Object缓存过期时间。<br>Type: String<br>Default: None<br>Constraints: None|否
x-amz-storage-class| Object存储类型，如果未指定，默认为标准存储。<br>Type: Enum<br>Default: STANDARD<br>Valid Values: STANDARD、GLACIER、REDUCED_REDUNDANCY|否

### 请求元素
无请求元素

## 响应
### 响应Header
无特殊Header

### 响应元素

名称|描述
---|---
InitiateMultipartUploadResult|响应集合。<br>Type: Container<br>Children: Bucket, Key, UploadId<br>Ancestors: None
Bucket|执行分片上传所在的Bucket名称<br>Type: String<br>Ancestors: InitiateMultipartUploadResult
Key|执行分片上传的Object。<br>Type: String<br>Ancestors: InitiateMultipartUploadResult
UploadID|分片上传ID。<br>Type: String<br>Ancestors: InitiateMultipartUploadResul

## 示例
### 请求示例
```
POST /example-object?uploads HTTP/1.1
Host: oss-example.s3.<region>.jdcloud-oss.com
Date: Mon, 1 Nov 2010 20:34:56 GMT
Authorization: <authorization string>
```
### 响应示例
```
HTTP/1.1 200 OK
x-amz-request-id: 656c76696e6727732072657175657374
Date:  Mon, 1 Nov 2010 20:34:56 GMT
Content-Length: 197
Connection: keep-alive
Server: JDCloudOSS

<?xml version="1.0" encoding="UTF-8"?>
<InitiateMultipartUploadResult xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
  <Bucket>example-bucket</Bucket>
  <Key>example-object</Key>
  <UploadId>VXBsb2FkIElEIGZvciA2aWWpbmcncyBteS1tb3ZpZS5tMnRzIHVwbG9hZA</UploadId>
</InitiateMultipartUploadResult>
```
