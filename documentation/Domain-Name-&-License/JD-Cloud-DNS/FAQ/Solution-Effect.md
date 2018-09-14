## **测试域名解析生效的办法**

根据[域名生效原理](http://www.jcloud.com/help/detail/2172/isCateLog/1)可以知道，解析记录生效分为两个步骤:在云解析生效和在Local DNS生效。只有在Local DNS生效之后，客户端才能得到正确的解析结果。如果解析记录在本地没有生效，但是在云解析服务器已经生效，请耐心等待Local DNS刷新自身缓存，理论缓存时长由解析记录中配置的TTL值决定。实际网络中某些Local DNS会修改缓存时长，具体生效时间由Local DNS行为决定。

下面以www.jddnstest.com为例，分别在Windows和Linux平台展示对应的测试方法和步骤。已通过云解析控制台添加jddnstest.com解析，NS地址已修改为云解析地址ns1.jdgslb.com/ns2.jdgslb.com，配置好www.jddnstest.com的A记录地址。

## **Windows平台测试方法和步骤：**

Windows平台可以采用系统命令ping和nslookup，在CMD窗口，执行命令进行测试。

一、测试解析记录是否在客户端/Local DNS生效

操作步骤：

1.  打开Windows命令行窗口，依次点击 开始->所有程序->附件->命令提示符

2.  在CMD窗口中，执行命令 ping www.jddnstest.com

![11.png](http://img1.jcloudcs.com/cms/62124ca3-98dd-4892-bb44-528eadb8ed1120180302174149.png)

可以看到www.jddnstest.com已经获取到正确的解析地址

3.  如果找不到域名的解析地址则会提示找不到

![22.png](http://img1.jcloudcs.com/cms/51ec4fe9-5c28-4bce-a877-c6f72c3cc3cf20180302174301.png)

4.还可以采用nslookup命令进行测试，执行nslookup www.jddnstest.com

![33.png](http://img1.jcloudcs.com/cms/d460660e-2268-4d46-ad0e-813dfff1dbd920180302175129.png)

可以看到在客户端能够获取到www.jddnstest.com正确的IP地址

二、测试解析记录是否在云解析服务器生效

测试域名的解析记录是否在云解析服务器生效，只能采用nslookup命令进行，在CMD窗口，执行nslookup www.jddnstest.com ns1.jdgslb.com，其中ns1.jdgslb.com为域名jddnstest.com所属的云解析地址。

![44.png](http://img1.jcloudcs.com/cms/c64afba1-fb02-4e49-812b-1ec17818ac8320180302175530.png)

可以看到在客户端成功获取到了www.jddnstest.com的地址，且结果是通过云解析的服务器返回的。

## **Linux平台测试方法和步骤：**

Linux平台可以采用ping和dig命令，通过命令行测试。

一、测试解析记录是否在Local DNS/客户端生效

1、在命令行窗口执行ping www.jddnstest.com

![55.png](http://img1.jcloudcs.com/cms/f6715889-a5fa-4599-b546-3dff760320e920180302192031.png)

可以看到www.jddnstest.com已经获取到正确的解析地址

2、 如果找不到域名的解析地址则会提示" unknown host"

![66.png](http://img1.jcloudcs.com/cms/980fab9a-d757-47a9-8231-ac09b5219c3b20180302192113.png)

3、还可以采用dig命令进行测试，执行dig www.jddnstest.com

![77.png](http://img1.jcloudcs.com/cms/4d87e44d-c790-4834-85a5-b442581395aa20180302192158.png)

可以看到在客户端能够获取到www.jddnstest.com正确的IP地址

二、测试解析记录是否在云解析服务器生效

测试域名的解析记录是否在云解析服务器生效，只能采用dig命令进行，在命令行窗口执行dig www.jddnstest.com @ns1.jdgslb.com，其中ns1.jdgslb.com为域名jddnstest.com所属的云解析地址。

![88.png](http://img1.jcloudcs.com/cms/d505cc09-9c2b-4dc6-8a2b-15a62859777e20180302192238.png)

可以看到在客户端成功获取到了www.jddnstest.com的地址，且结果是通过云解析的服务器返回的。