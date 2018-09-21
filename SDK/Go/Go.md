
# 京东云Golang SDK

[![GoDoc](https://godoc.org/github.com/jdcloud-api/jdcloud-sdk-go?status.svg)](https://godoc.org/github.com/jdcloud-api/jdcloud-sdk-go)

欢迎使用京东云开发者Golang工具套件（Go SDK）。使用京东云Go SDK，您无需复杂编程就可以访问京东云提供的各种服务。
为了方便您理解SDK中的一些概念和参数的含义，使用SDK前建议您先查看OpenAPI使用入门。

## 环境准备
1.	京东云Go SDK适用于Go 1.6及以上版本。
2.	在开始调用京东云open API之前，需提前在京东云用户中心账户管理下的[AccessKey管理页面](https://uc.jdcloud.com/accesskey/index)申请accesskey和secretKey密钥对（简称AK/SK）。AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。

## 下载和安装
1.	京东云Go SDK的下载地址：[Go SDK](https://github.com/jdcloud-api/jdcloud-sdk-go)。
2.	您也可以使用以下命令获取安装包，代码会被下载到GOPATH环境变量中第一个路径src目录中。

    `go get github.com/jdcloud-api/jdcloud-sdk-go/core github.com/satori/go.uuid`

## 调用SDK
### 业务侧SDK的调用主要分为4步：
1.	设置accessKey和secretKey
2.	创建业务Client
3.	设置请求参数
4.	执行请求得到响应

### 大致代码如下：
``` go
package main

import (
	"fmt"
  	. "github.com/jdcloud-api/jdcloud-sdk-go/services/vm/apis"
	. "github.com/jdcloud-api/jdcloud-sdk-go/services/vm/client"
	. "github.com/jdcloud-api/jdcloud-sdk-go/core"
)

func main() {
	accessKey := "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
	secretKey := "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
	credentials := NewCredentials(accessKey, secretKey)
	client := NewVmClient(credentials)

	req := NewDescribeInstancesRequest("cn-north-1")
	resp, err := client.DescribeInstances(req)
	if err != nil {
		return
	}
	fmt.Println(resp.Result.Instances)
	fmt.Println(resp.Result.TotalCount)
	fmt.Println(len(resp.Result.Instances))
}
```
如果需要设置额外的header，例如要调用开启了MFA操作保护的接口，需要传递x-jdcloud-security-token，则按照如下方式：
```
req := NewDeleteInstanceRequest("cn-north-1", "i-xxxxx")
req.AddHeader("x-jdcloud-security-token", "xxx")
resp, err := client.DeleteInstance(req)
```
请参考demo中的测试用例，访问京东云各业务线接口。
