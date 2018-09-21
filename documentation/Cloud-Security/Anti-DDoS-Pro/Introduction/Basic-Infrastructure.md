# 基础架构

IP高防是针对互联网服务器在遭受大流量的DDoS攻击后导致服务不可用的情况下，推出的付费增值服务。

用户开通IP高防服务，配置将用户访问的IP地址引流到高防服务提供的IP地址上，经过IP高防服务对所有异常流量的实时检测和清洗，确保仅正常流量可回源到用户服务器，从而保证了源站的稳定可靠。

## 未接入IP高防
未接入IP高防时，所有正常、非正常的访问都会直接到达源站。一旦发生DDoS攻击，源站很容易就被打瘫。

![IP高防架构图](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/ipant%20002.png)

## 接入IP高防后
接入IP高防业务后，所有对源站的访问流量，均会经过IP高防的实时检测。IP高防拥有强大的防护机制，经过高防机房的流量清洗，过滤掉了四层和七层的攻击，只将清洗后的干净流量回注到源站。
![IP高防架构图](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/ipant%20001.png)

