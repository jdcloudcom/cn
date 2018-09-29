#  Post object
PostObject使用HTML表单上传文件到指定bucket。

基于浏览器利用HTTP POST直传文件到对象存储的Bucket中，可以降低延迟。Post Object的消息实体通过多重表单格式（multipart/form-data）编码，在Put Object操
作中参数通过HTTP请求头传递，在Post操作中参数则作为消息实体中的表单域传递。此接口兼容S3,仅支持OSS的兼容S3服务域名
，[参见服务器域名](../../API-Reference-S3-Compatible/Regions-And-Endpoints.md)。

请求语法

```
POST / HTTP/1.1
Host: <bucket>.s3.<region>.jcloudcs.com
Content-Length: length
Content-Type: multipart/form-data; boundary=your_boundary
 
--your_boundary
Content-Disposition: form-data; name="key"
 
object_key
--your_boundary
Content-Disposition: form-data; name="X-Amz-Credential"
 
<your accessKey>/<date>/<region>/s3/aws4_request
--your_boundary
Content-Disposition: form-data; name="X-Amz-Algorithm"
 
AWS4-HMAC-SHA256
--your_boundary
Content-Disposition: form-data; name="X-Amz-Date"
 
date
--your_boundary 
Content-Disposition: form-data; name="Policy"
 
base64Encoded_policy
--your_boundary
Content-Disposition: form-data; name="X-Amz-Signature"
 
signature
--your_boundary
Content-Disposition: form-data; name="file"; filename=<filename>
Content-Type: content_type
 
file_content
--your_boundary
Content-Disposition: form-data; name="submit"
Upload to OSS
--your_boundary--
```
Header特别提示:

|名称|描述|必须|
|-|-|-|
|Content-Type|标准的http header，但类型必须为multipart/form-data，并指定boundary，<br>例如：Content-Type: multipart/form-data; boundary=your_boundary|是|
#### 表单域
|名称|类型|描述|必须|
|-|-|-|-|
|Cache-Control|字符串|标准的http header，参考PutObject，将记为object元数据信息,<br>默认值：无|否|
|Content-Type|字符串|标准的http header，参考PutObject，将记为object元数据信息,<br>默认值：无|否|
|Content-Disposition|字符串|标准的http header，参考PutObject，将记为object元数据信息,<br>默认值：无|否|
|Content-Encoding|字符串|标准的http header，参考PutObject，将记为object元数据信息,<br>默认值：无|否|
|Expires|字符串|标准的http header，参考PutObject，将记为object元数据信息,<br>默认值：无|否|
|key|字符串|上传的object名字。支持变量${filename}（仅支持变量${filename}），例如指定key为bucket/${filename}，此时您上传了一个名为test.jpg的图片，那么oss保存的key为：bucket/test.jpg,<br>默认值：无|是|
|policy|字符串|用于限制本次请求为经过UTF-8编码和Base64编码的JSON,<br>默认值：无|对于需要签名的请求来说是必须的|
|success_action_redirect|字符串|当上传成功时client跳转地址，如果success_action_redirect没有被指定，或者指定了但是OSS没有解析成功，那么OSS将按照success_action_status的设置进行返回（默认返回204）如果上传文件失败，那么OSS将会返回error并不做跳转,<br>默认值：无|否|
|success_action_status|字符串|指定了上传文件成功时返回的状态码，前提是success_action_redirect 没有被指定，如果值为200或204，OSS返回内容为空。如果值为201，则返回的状态码为201，http body 内容为xml格式的object相关信息<br>默认值：204<br>有效值：200，201，204（默认）|否|
|x-amz-algorithm|字符串|签名算法，值为：AWS4-HMAC-SHA256<br>默认值：无<br>仅支持AWS4-HMAC-SHA256|对于需要签名的请求来说是必须的|
|x-amz-credential|字符串|如果使用S3 API，则格式为：<your-access-key-id>/<date>/<region>/s3/aws4_request例子：AKIAIOSFODNN7EXAMPLEYYYYYYYYYYYY/20180601/cn-north-1/s3/aws4_request<br>默认值：无|对于需要签名的请求来说是必须的|
|x-amz-date|字符串|ISO8601时间格式，例如：20180601T000000Z，policy中x-amz-date属性的值应该与它相同。注意，此时计算签名的时间为20180601<br>默认值：无|对于需要签名的请求来说是必须的|
|x-amz-signature|字符串|签名字符串<br>默认值：无|对于需要签名的请求来说是必须的|
|x-amz-storage-class|字符串|Object的存储类型<br> 默认值：STANDARD（标准存储）<br>有效值：STANDARD（标准存储）和REDUCED_REDUNDANCY（低冗余存储）|否|
|file|字符串|文件或文本内容，此属性必须放在form最后，否则file后的属性将被忽略，不支持多个文件同时上传<br>默认值：无|是|
 
#### 响应
 
#### 响应元素（Response Elements）
 
 当且仅当返回码为201时，有以下返回
 
|名称|类型|描述|
|-|-|-|
|PostResponse|容器|object存储的bucket name 子节点：Bucket，Key，Etag|
|+Bucket|字符串|object存储的bucket name 父节点：PostResponse|
|+Key|字符串|object name 父节点：PostResponse|
|+Etag|字符串|在每个Object生成的时候被创建，Post请求创建的Object，可以用于检查该Object内容是否发生变化 父节点：PostResponse|
|+Location|字符串|新创建Object的URL,注意：location中的key将进行urlencode 父节点：PostResponse|

#### 细节分析：
1.进行Post操作要求对bucket有写权限，如果bucket为public-read-write，可以不上传签名信息，否则要求对该操作进行签名验证，如果post form中没有提供足够的签名请求所需要的属性，那么本次请求将被视为匿名请求。

2.如果POST请求中包含Header签名信息或URL签名信息，OSS不会对它们做检查。(即PostObject只以Form中为准)

3.form中缺少必要属性。例如：缺少key， 返回400 InvalidArgument ; 缺少file，返回400 IncorrectNumberOfFilesInPostRequest

4.form 属性不区分大小写，例如：x-amz-signature 和 X-Amz-Signature等价，但是表单域的值为大小写敏感的。

5.form 大小限制20K（不包含file大小）,否则返回400， MaxPostPreDataLengthExceeded

6.Post请求的body总长度不允许超过5G。若文件长度过大，会返回错误码：EntityTooLarge。

7.key的value如果指定变量（仅支持变量${filename}），此时上传的文件名含有路径，即"/" 或"\"，那么${filename}将会被替换为最后一个"/" 或"\"之后的部分。例如：上传的文件名为：C:\Program Files\directory1\file.txt，那么key属性中${filename}将会被替换为file.txt

8.OSS不识别的属性将会被忽略，但是form里面的属性也需要在policy里面进行限制，否则将返回403 AccessDenied。

9.如果用户表单域中指定Content-MD5（请求头中的MD5不会被验证），OSS会计算body的Content-MD5并检查一致性，如果不一致，将返回BadDigest错误码。

10.当form 中包含success_action_redirect时，跳转目标地址为：url + ?bucket=<yourBucket>&key=<yourKey>&ETag=etag.此处query部分将进行urlencode

11.表单和policy必须使用UTF-8编码，policy为经过UTF-8编码和base64编码的JSON。

12.由于目前没有版本管理，如果用户上传同名文件将会被覆盖。
#### 示例：
#### 请求示例：

```
POST / HTTP/1.1
Host: testBucket.s3. cn-north-1.jcloudcs.com
Content-Length: length
Content-Type: multipart/form-data; boundary=123456789000
--123456789000
Content-Disposition: form-data; name="key"
test.txt
--123456789000
Content-Disposition: form-data; name="X-Amz-Credential"
AKIAIOSFODNN7EXAMPLEYYYYYYYYYYYY/20180601/cn-north-1/s3/aws4_request
--123456789000
Content-Disposition: form-data; name="X-Amz-Algorithm"
AWS4-HMAC-SHA256
--123456789000
Content-Disposition: form-data; name="X-Amz-Date"
20180601T000000Z
--123456789000
Content-Disposition: form-data; name="Policy"
eyJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJ5b3VoZS10ZXN0In0sWyJzdGFydHMtd2l0aCIsIiRrZXkiLCJwb3N0LyJdLHsic3VjY2Vzc19hY3Rpb25fc3RhdHVzIjoiMjAxIn0seyJ4LWFtei1jcmVkZW50aWFsIjoiQUtJQUkyTUtVS0ZFUjRMNEJaNFEvMjAxODA3MTUvdXMtd2VzdC0xL3MzL2F3czRfcmVxdWVzdCJ9LHsieC1hbXotYWxnb3JpdGhtIjoiQVdTNC1ITUFDLVNIQTI1NiJ9LHsieC1hbXotZGF0ZSI6IjIwMTgwNzE1VDAzNTcyN1oifSxbImNvbnRlbnQtbGVuZ3RoLXJhbmdlIiwiMCIsIjkiXV0sImV4cGlyYXRpb24iOiIyMDE4LTA3LTMwVDEyOjAwOjAwLjAwMFoifQ==
--123456789000
Content-Disposition: form-data; name="X-Amz-Signature"
1b336b54bb3c7800f2137ee5b2d5d7ee676376800d388a17004ec2bee607897a
--123456789000
Content-Disposition: form-data; name="file"; filename=”d:/ test.txt”
Content-Type: text/plain
wrwe
--123456789000
Content-Disposition: form-data; name="submit"
Upload to OSS
--123456789000--

```

#### 返回示例：
```
<?xml version="1.0" encoding="utf-8"?>
<PostResponse>
  <Bucket>testBucket</Bucket>
  <Key>test.txt</Key>
  <ETag>"1b6be8aac90401fe1cd5e4dd1c4b138f"</ETag>
  <Location>http://s3.cn-north-1.jcloudcs.com/testBucket/test.txt</Location>
</PostResponse>
```

#### Post Policy
Post请求的policy表单域用于验证请求的合法性，可以控制post请求的权限。 policy为一段经过UTF-8和base64编码的JSON文本，声明了Post请求必须满足的条件。虽然对于public-read-write的bucket上传时，post表单域为可选项，强烈建议您使用该域来限制Post请求。
policy示例：

```
{ "expiration": "2018-12-01T12:00:00.000Z",
  "conditions":
    {"bucket": "myBucketName" },
    ["starts-with", "$key", "user/yuyu/"],
  ]
}

```

Post policy中必须包含expiration和condtions。

##### expiration
post请求policy的过期时间，时间格式为ISO8601 GMT。例如：”2018-06-01T12:00:00.000Z”，指定Post请求必须发生在2018年6月1日12点之前。

##### Conditions
Conditions是一个列表，可以用于指定Post请求的表单域的合法值。Policy中支持的conditions项见下表：

|名称|描述|
|-|-|
|bucket|object上传到的bucket名字<br>支持exact matching匹配类型|
|content-length-range|上传内容的最大长度和最小长度限制<br>支持content-length-range匹配类型|
|Cache-Control<br>Content-Type<br>Content-Disposition<br>Content-Encoding<br>Expires|标准的http header，参考PutObject<br>支持exact matching和starts-with匹配类型|
|key|上传object的名字<br>支持exact matching和starts-with匹配类型|
|success_action_redirect|上传成功后跳转的url地址<br>支持exact matching和starts-with匹配类型|
|success_action_status|当上传文件成功但success_action_redirect没有被指定时返回的状态码<br>支持exact matching匹配类型|
|x-amz-algorithm|签名算法，值为：AWS4-HMAC-SHA256码<br>支持exact matching匹配类型|
|x-amz-credential|如果使用S3 API，则格式为：<your-access-key-id>/<date>/<region>/s3/aws4_request<br>例子：AKIAIOSFODNN7EXAMPLEYYYYYYYYYYYY/20180601/cn-north-1/s3/aws4_request<br>支持exact matching匹配类型|
|x-amz-date|ISO8601时间格式，例如：20180601T000000Z注意，此时计算签名的时间为20180601<br>支持exact matching匹配类型|
|x-amz-storage-class|Object的存储类型，默认值是”STANDARD”（标准存储）。支持”STANDARD”（标准存储）和”REDUCED_REDUNDANCY”（低冗余存储）两种存储类型<br>支持exact matching匹配类型|
 
 ###### Conditions匹配方式
 
|匹配方式|描述|
|-|-|
|精确匹配|form 属性必须准确匹配该值<br>例如{"bucket":   "example-bucket"},则要求文件只能上传到名为"example-bucket"的bucket。<br>另一种写法：[ "eq", "$bucket",   "example-bucket" ]|
|Starts With|form 属性必须以指定值为前缀, <br>例如：["starts-with",   "$key", "OSS/"] 指定了上传的文件名必须以OSS/为前缀|
|匹配任意值|用于允许指定form属性的值为任何内容, 使用Starts With 并赋值为空（””）<br>例如：["starts-with",   "$success_action_redirect", ""] 允许form中success_action_redirect可以为任何值|
|指定文件大小|只支持content-length，可以逗号分隔最小值和最大值<br>例如["content-length-range",   1048579, 10485760],限制了上传内容大小为1M~10M|

###### 转义字符
于在 Post policy 中 $ 表示变量，所以如果要描述 $，需要使用转义字符\$。除此之外，JSON 将对一些字符进行转义。下表描述了 Post policy 中需要进行转义的字符。

|转义字符|描述|
|:---|:-|
|\\/|斜杠|
|\\|反斜杠|
|\\$|美元符|
|\\b|空格|
|\\f|换页|
|\\n|换行|
|\\r|回车|
|\\t|水平制表符|
|\\uxxxx|Unicode 字符|

##### Post policy细节分析
1.policy中expiration和condition元素是必须的，否则policy验证失败，算作匿名请求。

2.上传的form里面除了x-amz-signature, file, policy, x-ignore-*，其他属性必须要在policy中进行限制.否则将算作匿名访问

3.若policy 格式不符合规范，如输入无效的Condition Match Type等，都将当做匿名请求来处理。

4.policy conditions（除content-length-range）校验未通过或者form里面没有找到对应的属性都将算作匿名访问，content-length-range验证不通过会返回EntityTooLarge，EntityTooSmall

###  计算Signature
对于需要验证的Post请求，HTML表单中必须包含policy和signature（X-Amz-Signature）信息。policy控制请求中那些值是允许的。计算signature的具体流程为：

1.创建一个 UTF-8 编码的 policy。

2.将 policy 进行 base64 编码，该值将作为签名计算的StringToSign字段。

3.将第二步得到字符串和其他签名所需信息，如AccessKeySecret等使用HMAC-SHA256算法进行签名计算。

4.将最后的结果进行16进制编码。

#### 表单上传样例：
以下例子提供了如何使用POST policy 和表单完成上传一个文件到OSS。

##### Policy样例
```
{
	"expiration": "<expiration> example:2018-08-30T12:00:00.000Z",
	"conditions": [
		{"bucket": "<your bucket>"},
		["starts-with", "$key", "<your objectKey prefix>"], 
		{"Content-Type": "<type> example:image/jpeg"}, 
		{"X-Amz-Credential": "<your accessKey>/<date> example:20180709/<region>/s3/aws4_request"}, 
		{"X-Amz-Algorithm": "AWS4-HMAC-SHA256"}, 
		{"X-Amz-Date": "<date> example:20180709T053727Z"}
	]
}

```
##### form样例

```
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  </head>
  <body>

  <form action="http://<your bucket>.s3.<region>.jcloudcs.com/" method="post" enctype="multipart/form-data">
    // Key to upload: 
    <input type="input"  name="key" value="<your objectKey>" />
    Content-Type: 
	<input type="input"  name="Content-Type" value="<type> example:image/jpeg" />
    <input type="text"   name="X-Amz-Credential" value="<your accessKey>/<date> example:20180709/<region>/s3/aws4_request" />
    <input type="text"   name="X-Amz-Algorithm" value="AWS4-HMAC-SHA256" />
    <input type="text"   name="X-Amz-Date" value="<date> example:20180709T053727Z" />
	<input type="hidden" name="Policy" value='<base64 policy>' />
    <input type="hidden" name="X-Amz-Signature" value="<signature>" />
    // File: 
    <input type="file"   name="file" /> 
    <!-- The elements after this will be ignored -->
    <input type="submit" name="submit" value="Upload to Amazon S3" />
  </form>
  
</html>

``` 

说明：您需要替换有效的bucket 名称，dates, credential, policy, 和signature才能成功的上传文件到OSS。
