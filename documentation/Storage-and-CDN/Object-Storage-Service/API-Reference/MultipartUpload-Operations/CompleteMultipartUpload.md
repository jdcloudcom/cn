# CompleteMultipartUpload

该操作用来完成Multipart Upload，合并其包含的所有Part，并在云存储中产生一个新的Object。

当用户初始化Multipart Upload并上传了所有相关的Part之后，你可以通过该操作完成整个Multipart Upload。收到该请求后，云存储根据每一个Part Number的顺序，将已经上传的所有的Part合并成一个Object。你必须保证你提供了完整有效的Part列表：所有的Part按照 PartNumber升序排列，不能有无法识别的Part，不能有遗漏的Part。目前，客户端与服务端在http body中以json格式交互。 

**请求语法**
```
POST   /ObjectName?uploadId= UploadId HTTP/1.1
Host: BucketName. s.jcloud.com
Content-Length: Size
Date: GMT   Date     
Authorization:   signatureValue#请参照“访问控制”
 
{
      "Part": [
          {
              "PartNumber": PartNumber,
              "ETag": " ETag"
          },
 
. . . . . . ,
                                
          {
              "PartNumber": PartNumber,
              "ETag": " ETag"
          }
    ]
}
```

**请求参数**

|名称|描述|
|-|-|
|Part|保存已经上传Part信息的集合。<br>类型：List|
|PartNumber|Part编号。<br>类型：int|
|Etag|Part成功上传后，OSS返回的ETag值。<br>类型：字符串|

**响应元素**

|名称|描述|
|-|-|
|Bucket|Bucket名称<br>类型：字符串|
|Key|新创建Object的名字<br>类型：字符串|
|Etag|所有Part MD5相加，然后计算总的MD5<br>类型：字符串|

细节分析

1.Complete Multipart Upload时，检查用户提交的Partlist中的每一个Part号码和Etag。所以在上传Part时，客户端除了需要记录Part号码外，还需要记录每次上传Part成功后，服务器返回的ETag值。

2.OSS处理Complete Multipart Upload请求时，一般会很快完成，但是在这段时间内，如果客户端和OSS之间的链接断掉，OSS仍会继续将请求做完。

3.用户提交的Part List中,Part号码可以是不连续的。例如第一块的Part号码是1；第二块的Part号码是5。

4.OSS处理Complete Multipart Upload请求成功后，该Upload ID就会变成无效。

**请求示例**

```
POST   /multipart.data?uploadId=9FFFFF35C1535F7B HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Content-Length: 187
Date: Wed, 12 Jul 2017   12:47:57 GMT  
Authorization: jingdong qbS5QXpLORrvdrmb:/Qq9QFSIEzaPPL5YgAkbHoXkTKc=
 
{
      "Part": [
          {
              "PartNumber": 1,
              "ETag": "9223eed2740a549634ac58688d33b614"
          },
          {
              "PartNumber": 2,
              "ETag": "aa286070fe65d16d39fb8997143ea564"
          },
          {
              "PartNumber": 3,
              "ETag": "3b586f704fcd6b714fde125aeffc3e74"
          }
    ]
}       
```

**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jul 2017   12:47:58 GMT
Content-Type:   application/json;charset=UTF-8
Content-Length: 83
Connection: keep-alive
x-jss-request-id:   B7C62B29F77E2132
X-Trace:   200-1499863677959-0-0-20-58-58
 
{"Bucket":"youhe","Key":"multipart.data","ETag":"4e456c2fc34928a3e2fa202acf71870a"}
```
