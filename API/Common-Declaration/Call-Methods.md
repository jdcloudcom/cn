# 调用方法 #
## 调用基础说明 ##

京东云OpenAPI使用Restful接口风格，要进行OpenAPI调用需要包含如下信息：请求协议，请求方式，请求地址，请求路径，请求头，请求参数，请求体。

为了您的数据安全，建议务必使用https协议。

京东云OpenAPI不同接口使用不同的HTTP方法，一般资源创建用POST请求，查询用GET请求，修改用PUT或PATCH请求，删除用DELETE请求。具体接口使用的HTTP方法，请参考API文档请求方式章节。

OpenAPI服务的地址和路径格式一般为：

	https://{product}.jdcloud-api.com/{API版本号}/regions/{地域ID}/{资源名称}/{资源ID(可选)}/{子资源名称(可选)}/{子资源ID(可选)}{:自定义动作(可选)}

具体每个接口的地址及路径请参考具体API文档请求地址章节。

HTTP请求头中需要包含公共请求头，请参考公共请求头。

请求参数和请求体的信息，请参考具体API文档请求参数章节。一般来说，GET、DELETE和HEADER的接口参数通过请求参数传递，POST、PUT和PATCH的接口参数通过请求体传递。

## 公共请求头 ##

名称|类型|必填|描述
:---|:---|:---|:---
x-jdcloud-algorithm | String | 是 | 用于创建请求签名的哈希算法，目前只支持 `JDCLOUD2-HMAC-SHA256`
x-jdcloud-date | String | 是 | 签名请求的日期和时间，遵循ISO8601标准，使用UTC时间，格式为YYYYMMDDTHHmmssZ。日期必须与`authorization`请求头中使用的日期相匹配。例如： `20180707T150456Z`
x-jdcloud-nonce | String | 是 | 随机生成的字符串，需要保证一段时间内的唯一性
x-jdcloud-security-token | String | 否 | 如果用户开启了mfa操作保护，该API接口又是需要保护的接口，调用时需要传此参数
authorization | String | 是 | 鉴权信息，由签名算法生成，生成的数据格式例如：JDCLOUD2-HMAC-SHA256    Credential=accessKey/20180226/cn-north-1/nc/jdcloud2_request,    SignedHeaders=content-type;host;x-jdcloud-date;x-jdcloud-nonce,    Signature=4432ad80f84a41d56f3d41b59918a0844b468d8c131fa7d7c993693f62cf43ef`



## 特殊请求参数说明 ##       

部分API接口中有使用一些特殊的请求参数，如云主机的describeInstances接口使用了filters参数，其使用方式如下：

参数名|使用场景|作用|示例
:---|:---|:---|:---
filters.N | 用在列表请求中，作为过滤条件 | 查询条件，用于查询接口，   格式为：Filters.N.查询条件，每个条件必含name,values,选填operator，默认eq，可选lt,   le, gt, gt, ne, in, like（API若无特殊说明，operator不用填写，都是默认eq） | 如根据名称、CIDR及cpus搜索：filters.1.name=name&filters.1.values.1=aaa&filters.2.name=CIDR&filters.2.values.1=192.168.1.0/24&filters.3.name=cpus&filters.3.operator=in&filters.3.values.1=2&filters.3.values.2=4；
Sorts.N | 用在列表请求中，作为排序条件  | 排序参数，格式为sorts.N | sorts.1.name=az&sorts.1.direction=asc&sorts.2.name=status&sorts.2.direction=desc；



## GET请求示例 ##        

下面以调用查询云主机列表接口为例，介绍如何产生一个GET类型OpenAPI调用。（直接构造OpenAPI调用较为繁琐，建议您直接使用京东云提供的SDK）

首先在云主机接口概览页，您可以看到云主机的请求地址，以及看到创建云主机的具体接口describeInstances。

然后在describeInstances页面，看到请求方式为GET，请求地址为/v1/regions/{regionId}/instances，同时还看到请求参数。regionId 通过地域编码查询得到。GET、DELETE、HEAD请求的所有参数都是以请求参数的形式传递。

最终生成的调用为：

	GET
	https://vm.jdcloud-api.com/v1/regions/cn-north-1/instances?pageNumber=1&pageSize=25

请求头:

	x-jdcloud-algorithm: JDCLOUD2-HMAC-SHA256
	x-jdcloud-date: 20140707T150456Z
	x-jdcloud-nonce: ed558a3b-9808-4edb-8597-187bda63a4f2
	authorization: JDCLOUD2-HMAC-SHA256 accessKey/20180226/cn-north-1/nc/jdcloud2_request, SignedHeaders=content-type;host;x-jdcloud-date;x-jdcloud-nonce, Signature=4432ad80f84a41d56f3d41b59918a0844b468d8c131fa7d7c993693f62cf43ef

请求体：

	空

 

## POST请求示例 ##    

下面以调用云主机创建接口为例，介绍如何产生一个POST类型OpenAPI调用。（直接构造OpenAPI调用较为繁琐，建议您直接使用京东云提供的SDK）

首先在云主机接口概览页，您可以看到云主机的请求地址，以及看到创建云主机的具体接口createInstances。

然后在createInstances页面，看到请求方式为POST，请求地址为/v1/regions/{regionId}/instances，同时还看到请求参数。regionId 通过地域编码查询得到。POST、PUT、PATCH请求的所有参数都是以json串的方式通过请求body传递。

最终生成的调用为：

	POST
	https://vm.jdcloud-api.com/v1/regions/cn-north-1/instances

请求头:

	x-jdcloud-algorithm: JDCLOUD2-HMAC-SHA256
	x-jdcloud-date: 20140707T150456Z
	x-jdcloud-nonce: ed558a3b-9808-4edb-8597-187bda63a4f2
	authorization: JDCLOUD2-HMAC-SHA256 accessKey/20180226/cn-north-1/nc/jdcloud2_request, SignedHeaders=content-type;host;x-jdcloud-date;x-jdcloud-nonce, Signature=4432ad80f84a41d56f3d41b59918a0844b468d8c131fa7d7c993693f62cf43ef

请求体：

	{
         "instanceSpec": {
                  "az": "cn-north-1a",
                  "instanceType": "g.s1.micro",
                  "imageId": "98d4a0f-88c1-451a-8971-f1f76903b6c",
                  "name": "sdk-test",
                  "elasticIp": {
                          "bandwidthMbps": 2,
                          "provider": "NO_BGP"
                  },
                  "primaryNetworkInterface": {
                          "networkInterface": {
                                   "subnetId": "subnet-0rtcw9jl0",
                                   "az": "cn-north-1a"
                          }
                  },
                  "systemDisk": {
                          "diskCategory": "local"
                  },
                  "dataDisks": [{
                          "diskCategory": "cloud",
                          "autoDelete": true,
                          "cloudDiskSpec": {
                                   "name": "sdk-test-disk1",
                                   "diskType": "premium-hdd",
                                   "diskSizeGB": 50
                          }
                  },
                  {
                          "diskCategory": "cloud",
                          "autoDelete": true,
                          "cloudDiskSpec": {
                                   "name": "sdk-test-disk2",
                                   "diskType": "ssd",
                                   "diskSizeGB": 40
                          }
                  }],
                  "description": "sdk测试"
         },
         "maxCount": 2,
         "regionId": "cn-north-1"
	}
