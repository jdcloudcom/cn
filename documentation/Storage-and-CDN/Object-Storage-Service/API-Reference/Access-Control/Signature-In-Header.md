# 在Header中包含签名

用户可以在HTTP请求中增加 Authorization 的Header来包含签名（Signature）信息，表明这个消息已被授权。

## Authorization字段计算的方法
```
Authorization ="jingdong" + " " + AccessKey + ":" + Signature;
Signature =base64(HMAC-SHA1(AccessKeySecret, UTF-8-Encoding-Of( StringToSign ) ) )
StringToSign =HTTP-Verb + "\n"
                       + Content-MD5 + "\n"
                       + Content-Type + "\n"
                       + Date + "\n"
                      + CanonicalizedHeaders
                      + CanonicalizedResource;
```

注意：

1.当 Content-Type，Content-MD5不存在时，由空字符串代替。

2.您的AccessKey和AccessKeySecret可以登录到京东云的控制台，在【AccessKey管理】中查看。AccessKeySecret表示签名所需要的秘钥

3.HTTP-Verb表示HTTP 请求的Method，主要有PUT，GET，POST，HEAD，DELETE等

4.\n表示换行符

5.Content-MD5表示请求内容数据的MD5值，对消息内容（不包括头部）计算MD5值获得128比特位数字，对该数字进行base64编码而得到。该请求头可用于消息合法性的检查（消息内容是否与发送时一致），如”3fe8ebd7f5996651fa46c4aefe24b6af”，也可以为空。

6.Content-Type表示请求内容的类型，如”text/plain”，也可以为空

7.Date表示此次操作的时间，且必须为GMT格式，如”Sun, 09 Jul 2017 06:08:40 GMT”

8.CanonicalizedHeaders表示以x-jss-为前缀的http header的字典序排列

9.CanonicalizedResource表示用户想要访问的OSS资源，其中Date和CanonicalizedResource不能为空；如果请求中的Date时间和OSS服务器的时间差15分钟以上，OSS服务器将拒绝该服务，并返回HTTP 403错误。

## 构建CanonicalizedHeaders的方法

所有以 x-jss- 为前缀的HTTP Header被称为CanonicalizedHeaders。它的构建方法如下：

1.将所有以 x-jss- 为前缀的HTTP请求头的名字转换成小写。

2.将上一步得到的所有HTTP请求头按照名字的字典序进行升序排列。

3.删除请求头和内容之间分隔符两端出现的任何空格。

如x-jss-server-side-encryption:  false转换成：x-jss-server-side-encryption:false

1.将每一个头和内容用\n分隔符分隔拼成最后的CanonicalizedHeaders。

2.如果没有以x-jss-为前缀的HTTP请求头，则CanonicalizedHeaders为空字符串""。

注意:

1.CanonicalizedHeaders可以为空，无需添加最后的\n。

2.如果只有一个，则如x-jss-server-side-encryption:false\n注意最后的\n。

3.如果有多个，注意最后的”\n”。

## 构建CanonicalizedResource的方法

用户发送请求中想访问的OSS目标资源被称为CanonicalizedResource。它的构建方法如下：

1.将CanonicalizedResource置成空字符串"" 。

2.放入要访问的OSS资源 /BucketName/ObjectName（无ObjectName则CanonicalizedResource为”/BucketName“，如果同时也没有BucketName则为“/”）。

示例：

关于MultipartUpload操作中ListParts的API，此时的CanonicalizedResource为：/BucketName/ObjectName?uploadId=UploadId。

说明：

多个query 将会以&拼接，并拼接在path?后面。例如：PUT   /ObjectName?uploadId=UploadId&partNumber=PartNumber

支持的query签名字段如下：
```
SUB_RESOURCES："lifecycle", "location", "logging", "partNumber", "policy", "uploadId", "uploads", "versionId", "versioning", "versions", "website", "acl"

RESPONSE_HEARDES："contentType", "contentLanguage", "cacheControl","contentDisposition", "contentEncoding"
```
 
## 计算签名头规则
签名的字符串必须为UTF-8格式。含有中文字符的签名字符串必须先进行UTF-8编码，再与 AccessKeySecret计算最终签名。

1.签名的方法用RFC 2104中定义的HMAC-SHA1方法，其中Key为AccessKeySecret。

2.Content-Type 和 Content-MD5 在请求中不是必须的，但是如果请求需要签名验证，空值的话以空字符串代替代替。

签名示例

假如:

AccessKey是”qbS5QXpLORrvdrmb”，

AccessKeySecret是”1MYaiNh3NeN9SuxaqFjSrc7I49rWKkQCxpl9eLNZ”

请求
```
PUT /sign.txt   HTTP/1.1
  Content-Type: text/plain
  Content-MD5: 0c791a8c18017c7ad1675936d12bae5d
  x-jss-server-side-encryption: false
  Date: Thu, 13 Jul 2017 02:37:31 GMT
  Authorization: jingdong qbS5QXpLORrvdrmb: xvj2Iv7WcSwnN26XYnTq/c2YBQs=
  Content-Length: 20
  Host: oss.cn-north-1.jcloudcs.com
```
签名字符串计算公式
```
Signature =   base64(hmac-sha1(AccessKeySecret,
  HTTP-Verb + “\n” 
  + Content-MD5 + “\n”
  + Content-Type + “\n” 
  + Date + “\n”

+ CanonicalizedHeaders
  + CanonicalizedResource))
```
签名字符串
```
PUT\n

0c791a8c18017c7ad1675936d12bae5d\n

text/plain\n

Thu, 13 Jul 2017 02:37:31   GMT\n

x-jss-server-side-encryption:false\n

/oss-test/sign.txt
```
可用以下方法计算签名(Signature):

JAVA示例代码:
```
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import org.apache.commons.codec.binary.Base64;
 
String secretKey = "1MYaiNh3NeN9SuxaqFjSrc7I49rWKkQCxpl9eLNZ";
String signString = "PUT\n0c791a8c18017c7ad1675936d12bae5d\ntext/plain\nThu, 13 Jul 2017 02:37:31 GMT\n 
                     x-jss-server-side-encryption:false\n/oss-test/sign.txt";
SecretKeySpec signingKey = new SecretKeySpec(secretKey.getBytes("UTF-8"),"HmacSHA1");
Mac mac = Mac.getInstance("HmacSHA1");
mac.init(signingKey);
byte[] rawHmac = mac.doFinal(signString.getBytes("UTF-8"));
String signature =  new String(Base64.encodeBase64(rawHmac), "UTF-8");
```
签名(Signature)计算结果应该为xvj2Iv7WcSwnN26XYnTq/c2YBQs=，因为

Authorization = “jingdong “ + AccessKey + “:” + Signature所以最后Authorization为 “jingdong qbS5QXpLORrvdrmb: xvj2Iv7WcSwnN26XYnTq/c2YBQs=”然后加上Authorization头来组成最后需要发送的消息：
```
PUT /sign.txt   HTTP/1.1
  Content-Type: text/plain
  Content-MD5: 0c791a8c18017c7ad1675936d12bae5d
  x-jss-server-side-encryption: false
  Date: Thu, 13 Jul 2017 02:37:31 GMT
  Authorization: jingdong qbS5QXpLORrvdrmb: xvj2Iv7WcSwnN26XYnTq/c2YBQs=
  Content-Length: 20
  Host: oss.cn-north-1.jcloudcs.com
```
细节分析:

1.如果传入的AccessKey不存在或inactive，返回403 Forbidden。错误码：InvalidAccessKey。

2.传入请求的时间必须在京东云对象存储服务器当前时间之后的15分钟以内，否则返回403 Forbidden。错误码：RequestTimeTooSkewed。

3.若用户请求头中Authorization值的格式不对，返回400 Bad Request。错误码：InvalidToken。

京东云对象存储所有的请求都必须使用HTTP 1.1协议规定的GMT时间格式。其中，日期的格式为：Wed, 22 May 2017 05:29:49 GMT
