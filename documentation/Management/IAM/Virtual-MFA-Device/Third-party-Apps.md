# 概览：
您除了可以使用京东云助手（微信小程序）绑定虚拟MFA验证，还可以根据手机系统来选择第三方应用程序：

应用程序|备注|空
---|:--:|:---:
IOS 系统|Google Authenticator|APP Store下载
安卓系统|谷歌动态口令|主流应用商店中搜索下载（如应用宝，百度搜索）<br />安卓版谷歌动态口令依赖外部二维码扫描组件，<br />所以您还需要在应用市场中搜索安装“条码扫描器”

# IOS系统如何安装和使用
#### 1. 打开APP Store 搜索 ‘Google Authenticator’ 或者通过扫描下方二维码来直接安装。

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/IOS%E4%BA%8C%E7%BB%B4%E7%A0%81.png)

#### 2. 打开Google Authenticator后，点击最下面的 ‘开始设置’ 按钮

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/IOS%E5%BC%80%E5%A7%8B%E8%AE%BE%E7%BD%AE.png)

#### 3. 选择 ‘扫描条形码’，然后会弹出条形扫描窗，扫描启用MFA第二步中的二维码生成6位动态验证码，您也可以选择手动输入用户名和密钥的方式来进行绑定。

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/IOS%E6%89%AB%E6%8F%8F%E6%9D%A1%E5%BD%A2%E7%A0%81.png)

#### 4. 动态验证码每隔30s刷新一次，输入连续的两组动态验证码，点击确认后即可完成绑定。

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/IOS%E5%8A%A8%E6%80%81%E9%AA%8C%E8%AF%81%E7%A0%81.png)

# 安卓系统如何安装和使用


#### 1. 打开应用宝或百度 搜索 ‘谷歌动态口令’ 和 ‘条码扫描器’，或者通过扫描下方二维码来直接安装。

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E5%AE%89%E5%8D%93%E4%BA%8C%E7%BB%B4%E7%A0%81.png)

#### 2. 打开谷歌动态口令后，点击页面中的 ‘开始’ 按钮

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E5%AE%89%E5%8D%93%E8%B0%B7%E6%AD%8C%E5%8A%A8%E6%80%81%E5%8F%A3%E4%BB%A4.png)

#### 3. 选择 ‘扫描条形码’，然后会弹出条形扫描窗，扫描启用MFA第二步中的二维码生成6位动态验证码，您也可以选择手动输入用户名和密钥的方式来进行绑定。 

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E5%AE%89%E5%8D%93%E6%89%AB%E6%8F%8F%E6%9D%A1%E5%BD%A2%E7%A0%81.png)

#### 4. 动态验证码每隔30s刷新一次，输入连续的两组动态验证码，点击确认后即可完成绑定。 

![](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Virtual%20MFA%20device/%E5%AE%89%E5%8D%93%E5%8A%A8%E6%80%81%E9%AA%8C%E8%AF%81%E7%A0%81.png)
