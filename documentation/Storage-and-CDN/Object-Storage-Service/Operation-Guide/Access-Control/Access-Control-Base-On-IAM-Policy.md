# 基于IAM Policy的权限控制
访问控制（Identity and Access Management， IAM）是京东云提供的一项用户身份管理与资源访问控制服务。IAM Policy是基于用户的授权策略。通过设置
IAM Policy，您可以集中管理您的用户（比如员工、系统或应用程序），以及控制用户可以访问您名下哪些资源的权限。比如能够限制您的用户只拥有对某一个
Bucket 的读权限。子账号是从属于主账号的，并且这些账号下不能拥有实际的任何资源，所有资源都属于主账号。


**说明**

OSS支持IAM中子用户及角色访问。使用IAM Policy 对子用户进行权限控制的前提是您必须登录IAM访问控制控制台，新建子用户，并授予其对应访问策略[详见IAM](https://docs.jdcloud.com/cn/iam/core-concepts)。并且OSS本期不支持子账号登录控制台，您的子账号目前仅可通过使用API/SDK完成对OSS的各种操作。

如果您有跨账号授权的需求请查看。[基于Bucket policy的访问控制](./Access-Control-Base-On-Bucket-Policy.md)，完成跨账号授权。

## 如何构建 IAM Policy

- IAM Policy 基本元素
- IAM Policy 示例

**说明：** 目前Bucket Policy与 IAM Policy 元素语法略有不同，请根据您的使用情况做好区分，不要混淆二者。
### IAM Policy 基本元素

IAM Policy语言包含以下基本意义的元素：

版本（Version）：Version 定义了 IAM Policy 的版本，当前支持的 "version" 元素值为 3。

* 委托人（principal）：描述策略授权的实体,用户授权访问策略中不需要指定，被授予IAM Policy的子账号即是策略授权的实体。该元素对于存储空间访问策略（Bucket Policy）有效，对用户授权访问策略（IAM Policy）则不应添加。

* 语句（statement）：描述一条或多条权限的详细信息。该元素包括效力、操作、资源等多个其他元素的权限或权限集合。一条策略有且仅有一个语句元素。
    - 效力（Effect）：描述声明产生的结果是“允许”（allow）， **暂不支持显示拒绝（deny)，功能更新中，敬请期待** 。该元素是必填项。
    - 操作（Action）：描述被允许或拒绝的操作。操作可以是 API或者功能集（一组特定的 API）。该元素是必填项，
             详见下文【OSS在IAM Policy中用法 -指定Action】。
    - 资源（Resource）：描述指代的是 OSS 上面的某个具体的资源或者某些资源。该元素是必填项，有关如何指定资源的信息，详见下文
    【OSS在IAM Policy中用法-Resource】。
    
    Policy 需遵循 JSON 语法规范,详细说明请参阅[IAM Policy-策略语法](https://docs.jdcloud.com/cn/iam/elements)。
    
### OSS在IAM Policy中用法
1. 指定Action

IAM policy 中 Action 支持列表如下：

|操作关键字|操作项说明|对应API|操作级别 | 
|-|-|-|-|
|oss:PutObject|上传某个Object到该Bucket，支持普通上传和分块上传等|PUT Object, POST Object, PUT Object - COPY, Initiate Multipart Upload, Upload Part, Complete Multipart Upload|  Object 级别操作  |
|oss:GetObject|获取该Bucket内某个Object及其相关信息|GET Object, HEAD Object|	Object 级别操作  |
|oss:DeleteObject|删除该Bucket内Object|DELETE Object|Object 级别操作|
|oss:AbortMultipartUpload|终止分片上传|AbortMultipartUpload|Object 级别操作 |
|oss:ListBucket|列出该Bucket内的Objcet|GET Bucket (List Objects), HEAD Bucket|Bucket 级别操作 |
|oss:DeleteBucket|删除该Bucket|DELETE Bucket|Bucket 级别操作 |
|oss:ListBucketMultipartUploads|罗列出Bucket中所有执行中的Multipart Upload事件|ListMultipartUploads|Bucket 级别操作 |
|oss:* |OSS支持的所有操作，包括Service 级别操作，Bucket 级别操作，Object 级别操作|对应全部API 列表参见[API参考](https://docs.jdcloud.com/cn/object-storage-service/compatibility-api-overview)|所有级别操作 |

示例：

例如，使用 oss:GetObject 权限，用户可对 OSS 执行下载操作。

**说明**

- 上表中为本期支持用户自定义IAM策略指定的Action，后期会持续支持更多操作，敬请期待。

- OSS支持的Action 分为三大类：

    * Service 级别操作，对应的是 GetService 操作，用来列出所有属于该用户的某个地域的所有 Bucket 列表。 **本期不支持用户自定义IAM策略指定** 
    * Bucket 级别操作，对应oss:DeleteBucket、oss:ListBucketMultipartUploads、oss:ListBucke操作的对象是 Bucket。
    * Object 级别操作，分为 oss:GetObject、oss:PutObject、oss:DeleteObject和oss:AbortMultipartUpload，操作对象是 Object。
    
- 如想授权某一类的 Object 的操作，可以选择这几种的一种或几种。另外，所有的 Action 前面都必须加上前缀“oss:”，如上面例子所示。

2. 指定Resource

对于您的 OSS 资源，在IAM policy中指定方式如下为：
您不需要指定区域和命名空间，如下所示用"\*"代替，relative-id指定您的OSS资源，可以是存储空间也可是其中一些或某个对象，目前仅支持通配符（\*）。

 各个资源描述方式详见[访问控制-资源描述方式](https://docs.jdcloud.com/cn/iam/resource)
 
```
//示例：
jrn:oss:*:*:bucket_name
jrn:oss:*:*:bucket_name/key_name
```

示例：以存储空间名为 examplebucket 为例

|资源表示|说明|
|-|-|
|jrn:oss:*:*:examplebucket/developers/design_info.doc|表示examplebucket存储空间中developers/design_info.doc某个对象|
|jrn:oss:*:*:examplebucket/* |表示 examplebucket 存储存储空间中的所有对象|
|jrn:oss:*:*:examplebucket/dir/* |表示 examplebucket 存储存储空间中dir目录下的全部对象|
|jrn:oss:*:*:examplebucket/abc*|表示 examplebucket 存储存储空间以adc为前缀的对象|
|jrn:oss:*:*:examplebucket*|表示 以examplebucket为前缀的存储存储空间以及其中全部对象|

### IAM Policy 示例
1. 完全授权的IAM Policy

完全授权的 IAM Policy表示允许子账号可以对OSS进行任何操作。您可以登录[访问控制控制台-用户管理](https://iam-console.jdcloud.com/subUser/list)直接授权系统策略（JDCloudOSSAdmin）。
```
{
    "Statement": [
        {
            "Action": [
                "oss:*"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ],
    "Version": "3"
}
```

2. 不限制前缀的只读不写IAM Policy


此Policy表示子用户可对名为app-base-oss的Bucket下所有的Object能够列举与下载。

```
{
    "Statement": [
        {
            "Action": [
                "oss:GetObject",
                "oss:ListBucket"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/*",
                "jrn:oss:*:*:app-base-oss"
            ]
        }
    ],
    "Version": "3"
}
```

3. 限制前缀的只读不写IAM Policy

此Policy表示子用户可对名为app-base-oss的Bucket中有前缀 myuser1/的Object能够列举与下载。但无法下载其他前缀的Object。采用此种Policy，可以将不同的子账号控制的应用对应不同的前缀，就可以达到在同一个Bucket中空间隔离的效果。
```
{
    "Statement": [
        {
            "Action": [
                "oss:GetObject",
                "oss:ListBucket"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/myuser1/*",
                "jrn:oss:*:*:app-base-oss"
            ]
        }
    ],
    "Version": "3"
}
```

4. 不限制前缀的只写不读IAM Policy

此Policy表示应用可以对名为app-base-oss的Bucket中完成带有前缀myuser1/的Object进行上传。但无法上传其他前缀的Object。采用此种Policy，如果不同的应用对应不同的前缀，就可以达到在同一个Bucket中空间隔离的效果。
```
{
    "Statement": [
        {
            "Action": [
                "oss:PutObject"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/myuser1/*"
            ]
        }
    ],
    "Version": "3"
}
```
5. 限制前缀的只写不读IAM Policy

此Policy表示应用只可以对名为app-base-oss的Bucket进行上传。
```
{
    "Statement": [
        {
            "Action": [
                "oss:PutObject"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/*"
            ]
        }
    ],
    "Version": "3"
}
```

6. 不限制前缀的读写IAM Policy

此Policy表示应用只可以对名为app-base-oss的Bucket下所有的Object进行列举、下载、上传和删除。
```
{
    "Statement": [
        {
            "Action": [
                "oss:GetObject",
                "oss:PutObject",
                "oss:DeleteObject",
                "oss:ListBucket",
                "oss:AbortMultipartUpload"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/*",
                "jrn:oss:*:*:app-base-oss"
            ]
        }
    ],
    "Version": "3"
}
```
7. 限制前缀的读写IAM Policy

此Policy表示应用可以对名为app-base-oss的Bucket下带有前缀myuser1/的Object进行列举、下载、上传和删除，但无法对其他前缀的Object进行读写。采用此种Policy，如果不同的子用户对应不同的前缀，就可以达到在同一个Bucket中空间隔离的效果。
```
{
    "Statement": [
        {
            "Action": [
                "oss:GetObject",
                "oss:PutObject",
                "oss:DeleteObject",
                "oss:ListBucket",
                "oss:AbortMultipartUpload"
            ],
            "Effect": "Allow",
            "Resource": [
                "jrn:oss:*:*:app-base-oss/myuser1/*",
                "jrn:oss:*:*:app-base-oss"
            ]
        }
    ],
    "Version": "3"
}
```
