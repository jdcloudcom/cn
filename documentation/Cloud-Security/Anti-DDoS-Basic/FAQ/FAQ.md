# 常见问题

**1、Q: 基础防护应用场景是什么？**

A: 京东云DDoS基础防护应用于攻击流量最高不超过2G的DDoS攻击防护场景。一旦攻击流量超过该机房的基础防护能力，黑洞将被触发，触发黑洞后会对被黑洞的公网IP限制一定时长。

**2、Q: 怎么启动基础防护？**

A: 基础防护无需启动，您只要购买了京东云的公网IP，默认会自动对每个公网IP开启DDos防御，提供2G的防御带宽。

**3、Q: 如何关闭基础防护？**

A: DDos基础防护为自动开启，无法进行关闭。DDos基础防护对您的公网IP进行DDos防御，并不会对正常的业务访问造成任何影响。

**4、Q: 对防御的公网IP有什么要求？**

A: 基础防护只能防御已经备案的域名，如域名未备案，将立刻停止防御，并发送告警通知。

**5、Q: 触发黑洞状态的公网IP，在黑洞中会停留多长时间？**

A: 触发黑洞状态的公网IP在黑洞中停留时间至少是60分钟，在此期间公网IP仍处于被监控的状态。一旦再次监测到超过该机房基础
  防护能力的流量攻击，黑洞时间会在最后一次监测到攻击的时间点上再延长60分钟。
  
**6、Q: 攻击流量超过2G，会如何处理？**

A: 在攻击超过2G的情况下会触发黑洞，屏蔽一段时间外部对该IP的访问。建议您购买京东云的[IP高防](https://www.jdcloud.com/products/ipanti)服务，获得更大的防御能力。

**7、Q: 基础防护支持哪些攻击类型**

A：包括并不限于SYN Flood、ACK Flood、TCP Flood、UDP Flood、DNS反射攻击、NTP反射攻击、SSDP反射攻击等常见攻击。

如果上述不能解决您的问题，请咨询产品售后：[售后咨询](https://ticket.jdcloud.com/myorder/form?cateId=2&questionId=13)

# 相关文档

- [什么是基础防护？](../Introduction/Product-Overview.md)
- [基础防护架构](../Introduction/Basic-Infrastructure.md)
- [快速入门](../Getting-Started/Anti-DDos-Basic-Started.md)
