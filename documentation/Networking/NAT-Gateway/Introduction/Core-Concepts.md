# 核心概念

以下是NAT网关帮助文档中使用到的概念及其解释，请参考。

| 名词/概念 | 解释 |
| :- | :- |
| SNAT | SNAT(Source Network Address Translation) 源地址转换，通过NAT网关访问Internet时，将源IP转换成NAT网关的公网IP的过程被称为SNAT。 |
| DNAT | DNAT(Destination Network Address Translation)目的地址转换， NAT网关上建立了一个公网IP和端口与私网IP和端口的静态映射关系，从Internet访问NAT网关的这个静态IP和端口时，目的IP和端口被转换成内网IP和端口，从而访问到内网的服务，这个过程为DNAT。 |
| ALG | ALG(Application Level Gateway) 应用层网关，通常NAT只做三层IP和四层的端口的转换，NAT ALG是通过对应用层协议载荷(payload)中的IP和端口信息进行转换，进而支持协议之间跨NAT网关的正常通信。以FTP协议为例，FTP一般需要建立控制和数据两条链路，数据链路建立过程中FTP客户端会通知服务器端主动连接客户端，这个IP和端口是作为TCP协议载荷(payload)的一部分发送出去的，支持ALG功能的NAT网关会对报文内容中的IP和端口信息进行更新，将虚机的私网IP和端口变更为NAT网关分配的对应的公网IP和端口并建设映射关系，这样Internet上的FTP服务器端收到此报文后会按照报文中提供的IP和端口信息主动连接并建立数据链路。 目前京东智联云NAT网关支持ICMP ALG。 |
| NAT网关公网IP | NAT网关创建时会默认创建并绑定一个公网IP，此公网IP不可解绑，不可单独删除，和NAT网关实例同生命周期。NAT网关公网IP所对应的带宽费用按配置计费，与弹性公网IP费用一致。|
