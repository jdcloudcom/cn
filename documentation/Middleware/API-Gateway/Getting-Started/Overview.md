# API的开放和调用
使用前，您需要已注册京东云账号，并完成实名认证。如果还没有账号请先注册。
申请公测：在API网关产品页点击申请公测，之后经过运营人员审批加入公测名单，用户会收到已开通的通知（邮件或短信），之后可进入控制台开始使用，服务在菜单互联网中间件-API网关。【公测期适用】

您可以通过创建和部署API分组，实现服务的对外开放。您可依次完成以下步骤完成开放API服务：
- STEP1: 创建API分组
- STEP2: 创建分组下的API
- STEP3： 发布API分组到环境上
-	STEP4： 给分组绑定域名、配置流控策略、后端签名
-	STEP5： 给API调用者授权访问



## 前提条件
- 已注册京东云账号，并完成实名认证。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud&ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，或 [实名认证](https://uc.jdcloud.com/account/certify)。


## 操作步骤
### STEP1:创建API分组

1. 登录 [API网关 控制台](https://apigateway-console.jdcloud.com/apiGroupList)。

2. 在“API分组管理”页面，点击 **新建API分组** ，进入“创建”页面。

3. 填写分组信息后，点击确定，即新建分组。当首次新建时，系统会自动将其保存为版本号为0.0.1的版本。后续可在版本管理中进行多版本维护。




### STEP2:创建分组下的API
API 分组创建完成您就可以创建 API 了，创建 API 是定义 API 请求的过程。您需要在创建中依次定义以下内容：
- API 的基本信息：地域、API 名称、子路径、描述等。
- API 请求：查询参数、请求体类型、请求体格式、响应体类型、响应体格式等。
- API 高级配置：后端路径、后端参数、后端常量参数。




### STEP3：发布API分组到环境上

在 **API分组管理**页，通过 **发布**操作，将API分组发布到环境

发布过程中，可选择需要发布的环境（测试、预发、线上），选择要发布的版本，配置后端地址，然后点击发布，即可将分组发布到环境中。



### STEP4:给分组绑定域名、配置流控策略、后端签名
1.API网关基于 API分组，来绑定域名。API网关通过域名来定位到一个唯一的 API分组，再通过Path+HTTPMethod 确定唯一的 API。

2.进行流控策略配置和绑定

3.进行后端签名的配置和绑定




### STEP5：给API调用者授权访问

授权过程分为两部分：

（1）API调用者创建访问密钥，并将密钥提供给API提供者。

（2）API提供者使用API调用者提供的密钥，进行API分组的访问授权

