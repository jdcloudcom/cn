# 应用场景

以下说明消息队列 JCQ 用场景。

## 系统解耦
在不是强耦合多系统中，很多业务流程不强依赖于核心流程，可以放到消息队列中让消息消费者去按需消费，而不影响核心主流程。</br>
场景：电商场景</br>
上游业务交易系统完成后，将消息存储到消息队列中，下游业务系统物流、购物车、积分等等从消息队列中消费，相互隔离，并行处理，能保证分布式系统之间的最终一致。

![系统解耦场景](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/系统解耦-01.png)

## 削峰填谷
上下游系统处理能力存在差距的时候，利用消息队列作为数据的缓冲器，控制信息流量，在下游有能力处理的时候，再进行消费，避免系统处理的请求无效，无服务能力。</br>
场景：秒杀抢购</br>
用户在页面进行秒杀，前端页面即刻响应，订单或者确认稍后反馈给用户，客户便可关闭网页进行其他活动。

![削峰填谷场景](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/削峰填谷-02.png)

## 广播
生产者只关心消息是否送达了队列，不关心谁订阅了消息，系统的多个部分可以同时发送或消费消息。</br>
场景一：任务分配</br>
对于分布式处理框架，任务分配调度和任务处理的实现可以利用消息队列来完成。</br>
场景二：ConfigService更新配置</br>
ConfigService进行了配置更新，将已有更新这条信息发送到Topic中，其他服务器定时去获取Topic中的内容，发现配置更新便可以去ConfigService中更新配置信息。

![广播场景](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/广播-03.png)

## 可靠消息传递
对于上游系统发出的请求，接收者可能由于网络，断电，负载过高等各种原因无法接受，而消息队列同步写入、三副本备份可以存储请求，保证消息的可靠传递，保证信息的可靠性。</br>
场景：资金转移</br>
当大量交易产生时，真正交易系统可能还未进行账户数值的变动，但交易操作会被持久化保存，直到成功完成。

![可靠消息传递场景](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/可靠消息传递-04.png)
