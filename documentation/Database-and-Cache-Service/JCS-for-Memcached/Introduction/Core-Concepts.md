# 核心概念
术语|说明
---|:---
Memcached|Memcached 是一个高性能的分布式内存对象缓存系统。 京东云缓存 Memcached兼容 Memcached 二进制协议和文本协议两种方式。
实例 ID	|实例对应一个用户空间，是缓存Memcached实例的唯一标识。
连接地址	|用于连接缓存Memcached的 Host 地址，以域名方式展示，可在实例信息>基本信息>连接地址中查询到。
连接密码	|用于连接缓存Memcached的密码。可在购买时设置，或者在购买时设置免密。
SASL	|SASL 全称 SimpleAuthentication and Security Layer，是一种用来扩充 C/S 模式验证能力的机制。Memcached 从1.4.3版本开始，支持 SASL 认证。由于缓存Memcached的多租户共享特性，也采用 SASL 作为鉴权机制。SASL 本质上是使用密码保证的缓存数据安全，建议采用强密码和定期修改密码的策略。
