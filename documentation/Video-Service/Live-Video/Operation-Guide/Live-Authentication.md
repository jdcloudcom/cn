# 直播鉴权

鉴权功能旨在保护用户站点的内容资源不被非法站点下载盗用，由客户站点提供给用户加密
URL（包含权限验证信息），用户使用加密后的 URL 向服务器发起请求，服务器对加密 URL
中的权限信息进行验证以判断请求的合法性，对合法请求给予正常响应，拒绝非法请求，从而有效保护客户站点资源。

## 1.鉴权设置

登录直播控制台，进入“域名管理”页面，选择要查看播放地址的一组域名，点击右侧的“管理”进入域名配置页，点击“鉴权配置”切换到鉴权配置页面

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/%E7%9B%B4%E6%92%AD%E5%BD%95%E5%88%B6-%E9%A1%B5%E9%9D%A2%E5%88%87%E6%8D%A2.png)

滑动推流鉴权右侧的滑钮打开鉴权功能，目前只支持推流鉴权

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/%E7%9B%B4%E6%92%AD%E9%89%B4%E6%9D%83-%E9%89%B4%E6%9D%83%E5%BC%80%E5%90%AF.png)

填写对应的参数信息，点击“确定”完成鉴权配置

![](https://github.com/jdcloudcom/cn/blob/cn-live-video/image/live-video/%E7%9B%B4%E6%92%AD%E9%89%B4%E6%9D%83-%E9%89%B4%E6%9D%83%E4%BF%A1%E6%81%AF%E6%A8%A1%E6%9D%BF%E9%A1%B5.png)

## 2.鉴权说明

**鉴权URL组成**

鉴权URL由直播推流地址 + 验证串组成，验证串是根据鉴权 key + 失效时间通过 md5
算法计算出，该地址适用于 PC 端、移动端、第三方推流。

鉴权 KEY：用户在鉴权配置中填写的KEY参数。

有效时间：指用户访问客户源服务器时间超过自定义的时间（**timestamp** 字段指定）后，该鉴权失效，例如，有效时间为
1800s，用户设置访问时间：2020-08-15 15:00:00，链接真正失效时间是：2020-08-15
15:30:00。

**用户访问加密 URL 构成**

http:// DomainName/Filename?auth_key=timestamp-rand-uid-md5hash

**鉴权字段描述**

| **字段**  | **描述**                                                                                                  |
|-----------|-----------------------------------------------------------------------------------------------------------|
| timestamp | 失效时间，整形正数，固定长度 10，1970 年 1 月 1 日以来的秒数。用来控制失效时间，10 位整数，有效时间 1800s |
| rand      | 随机数，一般设成 0                                                                                        |
| uid       | 暂未使用（设置成 0 即可)                                                                                  |
| md5hash   | 通过 md5 算法计算出的验证串，数字和小写英文字母混合 0-9a-z，固定长度 32                                   |

**验证方法**

服务器拿到请求后，首先会判断请求中的 timestamp
是否小于当前时间，如果小于，则认为过期失效并返回 HTTP 403 错误，如果 timestamp
大于当前时间，则构造出一个同样的字符串（参考以下 sstring 构造方式）。

然后使用MD5算法算出 HashValue，再和请求中带来的 md5hash
进行比对，比对结果一致，则认为鉴权通过，返回文件，否则鉴权失败，返回 HTTP 403
错误。

**示例说明**

1.  通过 req_auth 请求对象:

http:// cdn.example.com/sports/football

2.  密钥设为：

jdlivekeyexample123 (由用户自行设置)

3.  鉴权配置文件失效日期为：

2015年10月10日00:00:00，计算出来的秒数为 1444435200

4.  服务器会构造一个用于计算 Hashvalue 的签名字符串：

/publishDomain/sports/football-1444435200-0-0-jdlivekeyexample123

5.  服务器会根据该签名字符串计算 HashValue

HashValue=md5sum("/publishDomain
/sports/football-1444435200-0-0-jdlivekeyexample123")

=80cd3862d699b7118eed99103f2a3a4f

6.  请求时 url 为：

http:// cdn.example.com/sports/football?auth_key=1444435200-0-0-80cd3862d699b7118eed99103f2a3a4f

计算出来的 HashValue 与用户请求中带的 md5hash = 80cd3862d699b711

8eed99103f2a3a4f 值一致，于是鉴权通过。
