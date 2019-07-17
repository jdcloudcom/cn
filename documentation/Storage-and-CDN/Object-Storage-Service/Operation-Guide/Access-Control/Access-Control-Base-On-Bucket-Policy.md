# 基于Bucket Policy的权限控制

## Bucket Policy 

Bucket Policy是基于资源的授权策略。访问策略使用基于 JSON 的访问策略语言。您可以通过访问策略语言授权指定委托人（principal）对指定的 OSS 资源执行指定的操作。

### Bucket Policy常见的应用场景如下：

-   向其他账号直接授权访问。

    您可以授予其他主账号访问您的OSS资源的权限。

-   向其他账号的子用户授权访问。

    您可以授予其他账号的子用户访问您的OSS资源的权限。
    
-   向角色授权访问。

    您可以授予角色访问您的OSS资源的权限。

-   向匿名用户授予带特定条件限制的访问权限。

     某些场景下，您需要向匿名用户授予带IP限制的访问策略。例如，您对外提供服务的网站中静态文件存储在OSS，为避免被其他人盗链，产生不必要的费用。您可以通过Bucket policy设置带Referer限制的策略，来指定允许访问的名单。或者您企业内部的机密文档，只希望在企业内部访问，您可以基于Bucket Policy设置带IP限制的访问策略。以上场景都是存在访问人员数量大，如果针对每个人配置IAM Policy，工作量非常大。此时，利用Bucket Policy您可以高效方便地进行授权。
     
### Bucket Policy（存储空间策略）基本元素

#### 存储空间策略语言包含以下基本意义的元素：

* 委托人（principal）：描述策略授权的实体。例如用户，可能是其他合作商（主账号）、子账号、角色、匿名用户等。该元素对于存储空间访问策略有效，对用户访问策略则不应添加。
* 语句（statement）：描述一条或多条权限的详细信息。该元素包括效力、操作、资源、条件等多个其他元素的权限或权限集合。一条策略有且仅有一个语句元素。
    - 效力（Effect）：描述声明产生的结果是“允许”还是“显式拒绝”，包括 allow 和 deny 两种情况。该元素是必填项。
    - 操作（Action）：描述被允许或拒绝的操作。操作可以是 API或者功能集（一组特定的 API）。该元素是必填项，详见下文【元素用法-Action】。
    - 资源（Resource）：描述指代的是 OSS 上面的某个具体的资源或者某些资源。资源是用六段式描述。该元素是必填项，有关如何指定资源的信息，详见下文【元素用法-Resource】。
    - 条件（Condition）：描述策略生效的约束条件。条件包括操作符、操作键和操作值组成。条件值可包括Referer、IP 地址信息。该元素是非必填项。
   
**说明：** 
目前Bucket Policy与 IAM Policy 元素语法略有不同，请做好区分，不要混淆二者。
Bucket Policy 大小限制为16k。
     
    
## 元素用法 

### principal

委托人 principal 元素用于指定被允许或拒绝访问资源的用户、账户、角色或其他实体。元素 principal 仅在存储空间中起作用；用户策略中不必指定，因为用户策略直接附加到特定用户。下面是 Bucket Policy 中指定 principal 的示例。
   
**说明**

- account-ID：为主账号的账户ID，获取方式：主账号登录京东云控制台后，点击账号管理，查看基本资料页即可获取。
- principal不支持通配符。

1.要授予京东云其他主账号权限

 在指定主账号: "AWS":"arn:aws:iam::account-ID:root", 也可以省略"root"。
 示例
 例如，账户 ID 为 123456789012 的情况下，您可以使用以方法来在 Principal 元素中指定账户：
    
```
    //单个账号
    "Principal":{"AWS":"arn:aws:iam::123456789012:root"}
    //多个账号
    "Principal": {
    "AWS": [
    "arn:aws:iam::123456789012:root",
    "arn:aws:iam::123456789010"]
    }  
```
    
2.要授予京东云IAM 子用户权限

  指定IAM 子用户:"AWS": "arn:aws:iam::account-ID:user/user-name"，user-name 为您想要授权的子用户用户名。
    
```
    //单个IAM 子用户
    "Principal": { "AWS": "arn:aws:iam::123456789012:user/user-name" }  
    //多个IAM 子用户
    "Principal": {
    "AWS": [
        "arn:aws:iam::123456789012:user/user-name-1",
        "arn:aws:iam::111111111111:user/UserName2"]
    }
``` 

3.要授予京东云IAM 角色权限

指定IAM角色："AWS":"arn:aws:iam::accountID:role/roleName"，roleName为授权的角色名称。
```
    //单个IAM 角色
    "Principal": { "AWS": "arn:aws:iam::123456789012:role/role-test" }  
    //多个IAM 角色
    "Principal": {
    "AWS": [
        "arn:aws:iam::123456789012:role/role-test1",
        "arn:aws:iam::123456789012:role/role-test2"]
    }
```
 
4.要授予每个人权限，也称为匿名访问
 
  例如，如果您将存储空间配置为网站，您需要该存储空间中的所有对象都可公开访问，请按照如下方式： 
  示例：
  
```
  "Principal":{"AWS":"*"}
```
### Effect
Effect 代表本条的Statement的授权的结果，分为 允许（Allow） 和 显示禁止（Deny）。多条 Statement 同时匹配成功时，显示禁止（Deny）的优先级更高。
如果没有显式授予（允许）对资源的访问权限，则隐式拒绝访问。您也可显式禁止（deny）对资源的访问，这样可确保用户无法访问该资源，即使有其他策略授予了访问权限的情况下也是如此。
示例
```
"Effect" : "Allow"
//或者
"Effect" : "Deny"

```
### Action

Bucket policy 中 Action 支持列表如下：

|操作关键字|操作项说明|对应API|操作级别 | 
|-|-|-|-|
|s3:PutObject|上传某个Object到该Bucket，支持普通上传和分块上传等|PUT Object, POST Object, PUT Object - COPY, Initiate Multipart Upload, Upload Part, Complete Multipart Upload，Abort Multipart Upload|  Object 级别操作  |
|s3:GetObject|获取该Bucket内某个Object及其相关信息|GET Object, HEAD Object|	Object 级别操作  |
|s3:DeleteObject|删除该Bucket内某个Object|DELETE Object|Object 级别操作|
|s3:ListBucket|列出该Bucket内的Objcet|GET Bucket (List Objects), HEAD Bucket, List Multipart Upload|Bucket 级别操作 |
|s3:DeleteBucket|删除该Bucket|DELETE Bucket|Bucket 级别操作 |

示例：
例如，使用 s3:DeleteObject 权限，用户可对 OSS 执行删除存储空间操作。

### Resource

对于您的 OSS 资源，在Bucket policy 中与IAM policy中指定方式略有不同，Bucket policy 中指定OSS Resource表示方式为：
您不需要指定区域和命名空间，relative-id指定您的OSS资源，可以是存储空间也可是其中一些或者某个对象，支持通配符（？与/*）。
```
arn:aws:s3:::relative-id
//示例：
arn:aws:s3:::bucket_name 
arn:aws:s3:::bucket_name/key_name
```

示例：以存储空间名为 examplebucket 为例

|资源表示|说明|
|-|-|
|arn:aws:s3:::examplebucket/developers/design_info.doc|表示examplebucket存储空间中的/developers/design_info.doc 对象|
|arn:aws:s3:::examplebucket/* |表示 examplebucket 存储存储空间中的所有对象|
|arn:aws:s3:::examplebucket/dir/* |表示 examplebucket 存储存储空间中dir目录下的全部对象|
|arn:aws:s3:::examplebucket/abc*|表示 examplebucket 存储存储空间以adb为前缀的全部对象|
|arn:aws:s3:::example?bucket/* |表示存储空间 (例如 example1bucket、example2bucket、example3bucket 等) 中的所有对象|
### Condition
Bucket policy 中可使您在授予权限时指定条件，即规则生效的条件，该条件是可选的。
如果在一个Condition中指定了多个条件操作符，那么多个条件操作符是AND的关系。如果某个条件的值指定的是一个数组，那么数组内元素是OR的关系。
目前仅支持限制用户访问来源（Referer和IP地址）。下面列出了目前支持的操作符列表及说明。

1.String操作符

| Condition 操作符|说明|
|-|-|
|StringEquals|表示examplebucket存储空间中的/developers/design_info.doc 对象|
|NotStringEquals |忽略大小写的字符串不相等比较|
|StringLike | 忽略大小写的字符串比较。该值可以包含多字符通配符 * 或者单字符通配符? |
|StringNotLike|忽略大小写的不匹配字符串比较。该值可以包含多字符通配符 * 或者单字符通配符? |

2.IP Address Condition操作符

| Condition 操作符|说明|
|-|-|
|IpAddress|指定的IP地址或范围|
|NotIpAddress |除指定 IP 地址或范围外的所有 IP 地址|

3.通用操作符

| Condition 操作符|说明|
|-|-|
|Null|如果为空或者没有值|

示例：

1.限制IP访问

```
 "Condition": {
         "IpAddress": {"aws:SourceIp": "54.240.143.0/24"},
         "NotIpAddress": {"aws:SourceIp": "54.240.143.188/32"} 
      } 

```
2.对指定的HTTP Referrer进行控制

```
  "Condition":{
        "StringLike":{"aws:Referer":["http://www.example.com/*","http://example2.com"]}
      }

```

### Bucket policy 完整示例

1.主账号允许匿名用户（所有用户），在访问referer来源为www.abcxxx.com时执行对yourbucket 存储空间中所有对象的下载和上传操作，而无需鉴权。
更多授权相关设置参见[跨账号授权](../../Best-Practices/Access-Control-And-Permission-Management/Cross-Account-Access-Overview.md)。

```

{
	"Statement": [{
		"Sid": "allowReferer",
		"Effect": "Allow",
		"Principal": {
			"AWS": "*"
		},
		"Action": [
			"s3:PutObject",
			"s3:GetObject"
		],
		"Resource": [
			"arn:aws:s3:::yourbucket/*"
		],
		"Condition": {
			"StringLike": {
				"aws:Referer": [
					"www.abcxxx.com"
				]
			}
		}
	}],
	"Id": "20190125114348155",
	"Version": "2012-10-17"
}


```
2.授权跨账号对指定存储空间testbucket中文件image.png的读写权限
```
 {
	"Version": "2012-10-17",
	"Id": "BucketId",
	"Statement": [{
		"Sid": "OtherAccountAllow",
		"Effect": "Allow",
		"Principal": {
			"AWS": [
				"arn:aws:iam::123456789012:root"
			]
		},
		"Action": ["s3:GetObject", "s3:PutObject"],
		"Resource": "arn:aws:s3:::testbucket/image.png"
	}]
}
```






