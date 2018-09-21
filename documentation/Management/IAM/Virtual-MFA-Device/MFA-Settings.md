# 启用虚拟MFA设备
## 为主账号绑定虚拟MFA设备
主账户为自己绑定虚拟MFA设备的流程如下：

选择 账户管理 > 虚拟MFA设备 > 启用， 短信验证后，弹出MFA启用页面。
![]( https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E4%B8%BA%E4%B8%BB%E8%B4%A6%E5%8F%B7%E7%BB%91%E5%AE%9A%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87.png)


## 主账号为子账号绑定虚拟MFA设备
主账号为IAM子账号绑定虚拟MFA设备的流程如下：

登录京东云控制台，选择 管理 > 访问控制 > 用户管理 > 用户详情 > 安全凭证，弹出MFA启用页面。
![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E4%B8%BB%E8%B4%A6%E5%8F%B7%E4%B8%BA%E5%AD%90%E8%B4%A6%E5%8F%B7%E7%BB%91%E5%AE%9A%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87.png)

子账号自行绑定虚拟MFA设备
子账号自行绑定虚拟MFA设备有两个入口，如下：

 - 子账号登录后进入概览页，点击 虚拟MFA设备， 弹出MFA启用页面
 - 子账号登录后进入账户管理，点击 虚拟MFA设备，弹出MFA启用页面
![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E5%AD%90%E8%B4%A6%E5%8F%B7%E8%87%AA%E8%A1%8C%E7%BB%91%E5%AE%9A%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87.png)

## 虚拟MFA设备启用流程：
Step 1：打开虚拟MFA应用程序，为了方便用户，我们提供了基于微信小程序版本的京东云助手。除此之外，我们还支持IOS版本的 Google Authenticator，安卓版本的谷歌动态口令，具体说明请参考第三方应用程序安装及使用指导。

我们推荐您使用京东云助手微信小程序，请打开微信 - “扫一扫”扫描图中二维码

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87%E5%90%AF%E7%94%A8%E6%B5%81%E7%A8%8B.png)

Step 2：添加账号，打开京东云助手微信小程序，扫描图中二维码，也可以点击手动输入，手动添加账号和密钥。 绑定成功后，京东云助手每隔30秒刷新一组动态验证码，输入连续的两组验证码后点击确定，完成虚拟MFA设备的绑定。
![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87%E5%90%AF%E7%94%A8%E6%B5%81%E7%A8%8B2.png)

Step 3: 完成绑定，两组动态验证码绑定成功，您在下次登录控制台时需要校验该账户已绑定的MFA设备的动态码。 同时我们建议您通过开启敏感操作验证，继续提升账号的安全性。 
![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87%E5%90%AF%E7%94%A8%E6%B5%81%E7%A8%8B3.png)


# 禁用虚拟MFA设备
当您不再使用MFA验证保护时，可以选择禁用。在通过安全操作验证后，直接在开启的入口处，点击禁用，即可生效。 需要注意的是，禁用MFA会导致绑定该账号的设备动态验证码不可用，若您重新开启，请绑定新的设备并告知共享账号的人员。 如果您需要更换MFA令牌，在解绑老的MFA后，绑定新的MFA即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E7%A6%81%E7%94%A8%E8%99%9A%E6%8B%9FMFA%E8%AE%BE%E5%A4%87.png)
