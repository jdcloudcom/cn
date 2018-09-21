# 共享缓存

适用于多个域名共享一个主域名的缓存策略，可将这些域名添加在一个分组内并开启共享缓存功能，即组内域名将共享同一份缓存策略，从而降低回源。如域名a.com和b.com共享a.com的缓存策略，设置共享缓存后，用户请求b.com时返回a.com的缓存策略。

1、登录[CDN控制台](https://cdn-console.jdcloud.com/overview)，打开[域名管理](https://cdn-console.jdcloud.com/domainlist)，选择“[域名组列表](https://cdn-console.jdcloud.com/domainlist?activeName=group)”，点击“添加域名组”进行新建域名组。![image.png](https://img1.jcloudcs.com/cms/4091df29-08bc-4beb-80c6-019459f39a1120180403173118.png)

2、新建域名组，可选择需要共享缓存的域名列表，并设置要共享哪个域名的缓存策略，即为主域名。

![image.png](https://img1.jcloudcs.com/cms/bf8ba981-0bc3-4334-999b-87918607155c20180426161612.png)

- 泛域名作不建立域名组时也可共享缓存，即泛域名为*.a.com，在“[缓存配置](https://cdn-console.jdcloud.com/detail/cache?id=wshtest.jcloud.com)”中可单独打开共享缓存配置，即*.a.com下的所有子域名均请求*.a.com下的缓存策略，泛域名也可作为独立的域名与其他域名建立域名组共享缓存。

![image.png](https://img1.jcloudcs.com/cms/29343df3-6ad9-4753-8746-30c58aba175b20180403183817.png)
