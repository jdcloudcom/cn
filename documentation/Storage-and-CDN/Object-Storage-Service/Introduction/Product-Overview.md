# OSS概述

## OSS简介

京东云对象存储（Object Storage Service，简称OSS）是利用京东在分布式存储领域多年的深厚技术积累，为用户提供安全、稳定、海量、便捷的对象存储服务。京东云对象存储提供包括文件上传、存储、下载、分发、在线处理在内的全系列产品，从几字节到数TB的数据，都能够为您提供完整的存储方案。

京东云对象存储服务底层架构和京东内部使用的图片存储、订单存储系统是完全相同的。目前系统在京东内部已经承载了商城，金融、移动、物流、拍拍、京东云、数据部等近200个部门的关键数据，为京东业务高速增长提供了坚实的保障；

同时，京东云对象存储还为您提供简单方便的Restful接口与方便易用的SDK，帮助您在任何应用、任何时间、任何地点都能管理和访问京东云对象存储上的数据。

## OSS存储级别
标准型存储（Standard Storage）：标准存储为用户提供了高可靠性、高可用性和高性能的对象存储服务。标准存储拥有低访问时延和较高的吞吐量，因而适用于吞吐量大，热点文件、需要频繁访问的业务场景，如：移动应用、 大型网站、 图片分享、热点音视频等。

低冗余型存储（Reduced Redundency Storage）：低冗余型存储为用户提供了较低存储成本和较低访问时延的对象存储服务。与标准型存储相比，低冗余型存储大幅降低存储的价格，适用于读取频率较低、数据需在对象存储上做较长时间冷备的业务场景，最低存储时间为30天。

## 快速导航

[计费规则](../Pricing/Billing-Rules.md) 

[存储基本操作](../Operation-Guide/Sign-Up-Service-2.md)

[图片处理](../Operation-Guide/Image-Service-Guide/Introduction-1.md)

[视频处理](../Operation-Guide/Video-Service-Guide/Video-Service-Guide-Overview.md)

[兼容S3 API](../API-Reference-S3-Compatible/Introduction-2.md)

[JAVA SDK](../API-Reference-S3-Compatible/Compatibility-Tools/SDK-Java.md)

[PHP SDK](../API-Reference-S3-Compatible/Compatibility-Tools/SDK-PHP.md)

[PYTHON SDK](../API-Reference-S3-Compatible/Compatibility-Tools/SDK-Python.md)

[迁移工具OSS Tranfer](../Best-Practices/Data-Migration-Tool.md)

[S3FS挂载工具](../Best-Practices/S3fs.md)
