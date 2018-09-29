# UploadPart

上传一个Part到指定的Multipart Upload中。

**请求语法**

```
PUT   /ObjectName?uploadId=UploadId&partNumber=PartNumber HTTP/1.1
Date: GMT Date
Authorization: jingdong   qbS5QXpLORrvdrmb:AdBNNN+uUP+qRcPJn5m4ezrbRwI=
Content-Length: size
Host: BucketName.s-bj.jcloud.com
```
细节分析

1. 在上传Part之前，必须先完成Initiate Multipart Upload操作，操作完成后会得到标识符Upload Id，该标识符唯一标识一个Multipart Upload。

2. 在上传Part时应指定其关联事件的Upload Id，如果指定的Upload Id不存在，将返回404 Not Found错误，错误码：NoSuchUpload；如果未指定Upload Id，即Upload Id为空，将返回400 Bad Request错误，错误码：InvalidArgument。

3. Part Number的范围在1-10000之间，如果Part Number大于10000，将返回400 ,错误码：TooManyParts。

4. Part Number唯一标识一个Part，并指定该Part在MultipartUpload中的位置。在Upload Part时，如果使用了同一个Part Number，服务端会返回上传成功，并覆盖原来的Part。

5. 为了保证数据的传输的正确性，服务端会在Part上传成功后返回实际存储的Part的MD5值，放在响应的header的ETag字段中，用于客户端校验。

**请求示例**

```
PUT  /multiSS?uploadId=9B2BF313C3E998E9&partNumber=1 HTTP/1.1
Date: Wed, 12 Jul 2017   09:22:16 GMT
Authorization: jingdong   qbS5QXpLORrvdrmb:AdBNNN+uUP+qRcPJn5m4ezrbRwI=
Content-Length: 3
Host: oss-test.s-bj.jcloud.com
Connection: Keep-Alive
```

**返回示例** 

```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jul 2017   09:39:01 GMT
Content-Length: 0
Connection: keep-alive
x-jss-request-id:   999D38C52D6C2B58
ETag:   "202cb962ac59075b964b07152d234b70"
```
