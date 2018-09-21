# 签名算法 #
## 步骤1：创建标准请求串并加密 ##
要开始签名过程，请以规范格式创建一个包含请求信息的字符串。这样可以确保当京东云收到请求时，可以计算出和您计算出的相同签名。 

以下示例显示了创建规范请求的伪代码。

示例规范请求伪代码

 

	CanonicalRequest =
	  HTTPRequestMethod + '\n' +
	  CanonicalURI + '\n' +
	  (CanonicalQueryString or '') + '\n' +
	  CanonicalHeaders + '\n' +
	  SignedHeaders + '\n' +
	  Lowercase(HexEncode(Hash(RequestPayload or '')))


在此伪代码中：

HTTPRequestMethod即HTTP协议请求方式，如POST、GET等。

CanonicalURI即请求路径。

CanonicalQueryString为请求查询字符串。要构建规范查询字符串，首先按字符代码升序对参数名进行排序，然后对每个参数名称和值进行URI编码。接着通过从排序列表中的第一个参数名称开始构建规范查询字符串。对于每个参数，附加URI编码的参数名称，后跟等号字符（=），后跟URI编码的参数值。对没有值的参数使用空字符串。在每个参数值之后附加&符号，除了列表中的最后一个值。

CanonicalHeaders为需要参与签名的请求头及值。要创建规范HTTP请求头列表，请将所有 HTTP header 名称转换为小写，并删除前导空格和尾随空格。通过用字符代码升序对请求头记性排序 ，然后遍历请求头名称来构建规范HTTP请求头列表。使用:分隔名称和值，并添加换行符。

SignedHeaders用于告知京东云，请求头中的哪些是签名过程的一部分，京东云可以忽略哪些（例如，由代理添加的任何附加标头）。注意host, x-jdcloud-date, x-jdcloud-nonce必须包含在内。

最后，需要把body中的payload做SHA256哈希后，表示为小写十六进制字符串。如果有效负载为空，则使用空字符串作为散列函数的输入。

 

POST示例请求

 
	POST
	/v1/regions/cn-north-1/instances 

	content-type:application/json
	host:vm.jdcloud-api.com
	x-jdcloud-date:20180404T034307Z
	x-jdcloud-nonce:ed558a3b-9808-4edb-8597-187bda63a4f2 	

	content-type;host;x-jdcloud-date;x-jdcloud-nonce
	eadd64d9bd63436404495b9a2cd0a5b4c59b01332a88d81da27815824b3c4280
 

GET示例请求

	GET
	/v1/regions/cn-north-1/metrics/cpu_util/metricData
	serviceCode=vm&startTime=2018-04-04T06%3A01%3A46Z
	content-type:application/json
	host:vm.jdcloud-api.com
	x-jdcloud-date:20180404T061302Z
	x-jdcloud-nonce:ed558a3b-9808-4edb-8597-187bda63a4f2 
	
	content-type;host;x-jdcloud-date;x-jdcloud-nonce
	eadd64d9bd63436404495b9a2cd0a5b4c59b01332a88d81da27815824b3c4280
 

## 签名步骤2：生成待签名字符串 ##
要创建字符串进行签名，请连接规则请求的算法，日期和时间，凭据范围和摘要，如以下伪代码所示：

 
	StringToSign =
    Algorithm + \n +
    RequestDateTime + \n +
    CredentialScope + \n +
    HashedCanonicalRequest

其中，
 

Algorithm固定为JDCLOUD2-HMAC-SHA256是算法。

日期与x-jdcloud-date HTTP请求头中的格式一致，为YYYYMMDD'T'HHMMSS'Z'，此值必须与之前任何步骤中使用的值相匹配。

CredentialScope格式为”{时间}/{地域编码}/{产品线}/jdcloud2_request\n”，例如20180130/cn-north-1/vpc/jdcloud2_request\n

HashedCanonicalRequest是步骤1生成的标准请求进行SHA256哈希后，表示为小写十六进制字符串。

例如：

	JDCLOUD2-HMAC-SHA256
	20180404T061302Z
	20180404/cn-north-1/monitor/jdcloud2_request
	5d7d08a5b792a63ad0bd820cff95ff41c6dbcf4bd7bae9e371be0ff891740ee7
 

## 签名步骤3：计算签名 ##
计算的伪代码

	kSecret = your secret access key
	kDate = HMAC("JDCLOUD2" + kSecret, Date)
	kRegion = HMAC(kDate, Region)
	kService = HMAC(kRegion, Service)
	kSigning = HMAC(kService, "jdcloud2_request")


其中HMAC(key, data)代表以二进制格式返回输出的HMAC-SHA256函数。散列过程中使用的日期格式为 YYYYMMDD。Region表示地域编码，Service表示产品线名称。

最终生成一个签名串，如：

	9b2026198d3acbf99da395e23a994ed369a0d70f5b4a5d7567dd0caf3009656d

 

## 签名步骤4：向请求中添加签名信息 ##
计算签名后，需要将签名的结果作为Authorization请求头将其添加到请求中。

以curl命令调用方式的例子：

	curl -X GET -H "x-jdcloud-date:20180404T061302Z" -H "x-jdcloud-nonce:ed558a3b-9808-4edb-8597-187bda63a4f2" -H "Authorization:JDCLOUD2-HMAC-SHA256 Credential=C61249XXXXXXXXXXXXXXXXXX/20180404/cn-north-1/monitor/jdcloud2_request, SignedHeaders=content-type;host;x-jdcloud-date;x-jdcloud-nonce, Signature=9b2026198d3acbf99da395e23a994ed369a0d70f5b4a5d7567dd0caf3009656d" -H "Content-Type:application/json" "http://vm.jdcloud-api.com/v1/regions/cn-north-1/metrics/cpu_util/metricData?serviceCode=vm&startTime=2018-04-04T06:01:46Z"
