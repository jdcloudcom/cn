#  京东云对象存储类型介绍
OSS提供标准存储、归档存储、低冗余存储三种存储类型，全面覆盖从热到冷的各种数据存储场景。

**说明**：各存储类型的定价信息请参见[价格总览](https://docs.jdcloud.com/cn/object-storage-service/price-overview),具体的计费方式请参见[计费规则](https://docs.jdcloud.com/cn/object-storage-service/billing-rules)。

* [标准存储](StorageClass-Overview#user-content-1)
* [归档存储](StorageClass-Overview#user-content-2)
* [低冗余存储](StorageClass-Overview#user-content-3)

### 标准存储（STANDARD）

<div id="user-content-1"></div>

为用户提供了高可靠性、高可用性、高性能的对象存储服务，能够支持频繁的数据访问。
标准存储拥有低访问时延与高吞吐量，因而适用于有大量热点文件。标准存储类型是各种社交、分享类的图片、大型网站、音视频应用、大数据分析的合适选择。

关键特性：
* 99.999999999%的数据持久性
* 服务可用性99.9%
* 支持实时访问
* 支持HTTPS加密传输
* 支持图片处理
* 支持音视频处理
* 支持全部地域
* 存储费用标准
* 无最短存储时间和最小计量空间


### 归档存储（GLACIER）

<div id="user-content-1"></div>

OSS归档存储类型在存储类型中单价最低，适合需要长期保存（建议半年以上）的归档数据，在数据的存储周期内极少被访问；数据取回时，需要根据您
选择的取回模式，等待几分钟到几小时。归档存储类型适合需要长期保存的档案数据、操作日志、影视素材等。归档存储类型的Object有最短存储时间，存储时间短于
60天的Object提前删除会产生一定费用。归档类型存储Object有最小计量空间，Object大小低于48KB，会按照48KB计算存储空间，数据获取会产生数据取回费用。


关键特性：

* 99.999999999%的数据持久性
* 服务可用性99.90%
* 需提前申请还原操作，数据才可读取
* 支持HTTPS加密传输
* 支持全部地域
* 存储费用低廉
* 有最短存储时间和最小计量空间

### 低冗余存储（REDUCED_REDUNDANCY）

<div id="user-content-1"></div>

OSS低冗余存储类型需要用户能够承受数据丢失，不推荐使用。





