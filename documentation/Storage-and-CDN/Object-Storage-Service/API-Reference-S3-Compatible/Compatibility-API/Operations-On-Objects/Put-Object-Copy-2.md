# Put Object-Copy

## 描述
创建一个已存在的Object的副本，该copy操作等同于先执行GET操作再执行PUT操作。可通过x-amz-copy-source头指定要复制的源Bucket及源Object。在OSS中可以操作的最大的单个Object为5G，超过5G，请使用分片上传Upload Part-Copy操作。要执行此操作，您需要有源Bucket的READ权限及目标Bucket的WRITE权限。

当OSS收到Put Object-Copy请求或OSS正在执行Copy时，该请求可能返回错误。如果在Copy执行之前发生错误，则会收到标准的OSS错误；如果在执行Copy的过程中发生错误，则Copy的错误会嵌入200 OK的响应中，所以200 OK响应的Copy结果可能是成功或失败。

## 请求
### 语法
```
PUT /destinationObject HTTP/1.1
Host: <destinationBucket>.s3.<region>.jdcloud-oss.com 
x-amz-copy-source: /source_bucket/sourceObject
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
Date: <date>
```
### 请求参数
无请求参数
### 请求Header
除公共请求Header，还可使用以下Header

名称|描述|必须
---|---|---
x-amz-copy-source|源Bucket和源Object名称，通过"/"分隔。<br>Type: String<br>Default: None<br>字符串必须使用URL编码|是
x-amz-storage-class|如果没有指定该header，存储类型默认为Standard标准存储。<br>Type: Enum<br>Default: STANDARD<br>Valid Values: STANDARD、GLACIER、REDUCED_REDUNDANCY|否

### 请求元素
无请求元素

## 响应
### 响应Header
除公共响应Header外，该操作还可使用以下Header

名称|描述
---|---
x-amz-storage-class|提供Object的存储类型信息。非标准存储情况下，OSS将会返回该Header

### 响应元素

名称|描述
---|---
CopyObjectResult|响应元素信息集合。<br>Type: Container<br>Ancestor: None
ETag|返回新Object的ETag。<br>Type: String<br>Ancestor: CopyObjectResult
LastModified|返回Object的最后修改时间。<br>Type: String<br>Ancestor: CopyObjectResult

## 示例
### 请求示例
```
PUT /my-second-image.jpg HTTP/1.1
Host: oss-example.s3.<region>.jdcloud-oss.com
Date: Wed, 28 Oct 2009 22:32:00 GMT
x-amz-copy-source: /bucket/my-image.jpg
Authorization: <authorization string>
```

### 响应示例
```
HTTP/1.1 200 OK
x-amz-request-id: 318BC8BC148832E5
Date: Wed, 28 Oct 2009 22:32:00 GMT
Connection: close
Server: JDCloudOSS

<CopyObjectResult>
   <LastModified>2009-10-28T22:32:00</LastModified>
   <ETag>"9b2cf535f27731c974343645a3985328"</ETag>
</CopyObjectResult>
```
