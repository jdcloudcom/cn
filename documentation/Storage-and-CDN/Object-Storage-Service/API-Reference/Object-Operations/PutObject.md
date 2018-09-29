# PutObject

操作用来上传一个新的Object到指定的Bucket中

**请求语法**

```
PUT /ObjectName HTTP/1.1
Content-Length:ContentLength
Content-Type: ContentType
Content-MD5: Content-MD5
Host: BucketName. s.jcloud.com
x-jss-server-side-encryption:   true or false      
x-jss-storage-class: STANDARD   or REDUCED_REDUNDANCY
Date: GMT  Date     
Authorization: signatureValue#请参照"访问控制"
```

**请求Header**

|名称|描述|
|-|-|
|Content-MD5|上传数据的MD5值，用于校验传输过程中，用户的数据是否被修改<br>类型：字符串<br>默认值：无|
|x-jss-server-side-encryption|指定jss创建object时的服务器端是否加密<br>类型：boolean<br>合法值：true,false|
|x-jss-storage-class|Object的存储类型，默认值是"STANDARD"（标准存储）。<br>支持"STANDARD"（标准存储）和"REDUCED_REDUNDANCY"（低频访问型）两种存储类型<br>注意：目前"REDUCED_REDUNDANCY"（低频访问型）仅华北机房支持<br>类型：字符串<br>默认值："STANDARD"（标准存储）|
|Cache-Control|指定该Object被下载时的网页的缓存行为；更详细描述请参照RFC2616。<br>类型：字符串<br>默认值：2592000|

细节分析

1.建议使用put object上传数据的最大长度不超过5GB。更大的文件建议采取分块上传。

2.该操作为原子操作，即操作要么成功，要么失败，且不存在只更新部分数据的情况。

3.存在相同key的情况下，会直接替换原有文件。

4.客户端可以通过HTTP 头Content-MD5进行端到端验证来保证上传数据的完整性。在上传之前，客户端自己计算出上传数据的Content-MD5值，并将其与数据一起上 传至云存储。云存储接收到数据之后，会重新计算收到数据的Content-MD5值，并与客户端提供的Content-MD5进行比对，只有在 Content-MD5匹配的情况下，才会将数据保存至云存储，否则服务端会返回错误使上传操作失败。

5.如果请求头中的“Content-Length”值小于实际请求体（body）中传输的数据长度，OSS将会上传文件失败，已上传数据将被丢弃。

6.如果Head中没有加入Content length参数，会返回400 Length Required错误。错误码：MissingContentLength

7.如果试图添加的Object所在的Bucket不存在，返回404 Not Found错误。错误码：NoSuchBucket。

8.如果传入的Object key长度大于1022字节，返回400 Bad Request。错误码：InvalidArgument

**请求示例**

```
PUT /example.jpg HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Content-Length: 13
Content-Type: text/plain
Content-MD5: 6457646542258052f767868fd686d74d 
x-jss-server-side-encryption:   false 
Date: Tue, 11 Jul 2017   07:13:32 GMT    
Authorization: jingdong   qbS5QXpLORrvdrmb:cQ63NndHAoEBmjZHehSuNWG/Jns=
```
**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 11 Jul 2017   07:13:32 GMT
Content-Length: 0
Connection: keep-alive
x-jss-request-id:   8E4FC95C05EC1A4C
ETag:   "6457646542258052f767868fd686d74d"
X-Trace:   200-1499757212162-0-0-20-50-50
```
**请求示例（未设置Content-Type和Content-MD5）：**

```
PUT /example.jpg HTTP/1.1
Host:   oss-example.s-bj.jcloud.com
x-jss-server-side-encryption:   true  
Date: Thu, 13 Jul 2017   02:12:02 GMT    
Authorization: jingdong     qbS5QXpLORrvdrmb:S2ZHyLfdZml/bRjD/TEQ+ftJXBA=
```
**返回示例（未设置Content-Type和Content-MD5）：**

```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 13 Jul 2017   02:12:13 GMT
Content-Length: 0
Connection: keep-alive
x-jss-request-id: 9457B50779BA6947
ETag: "77abd5a162ef88440102129fffbb404c"
X-Trace: 200-1499911919867-0-12790-12809-13303-13303
```
