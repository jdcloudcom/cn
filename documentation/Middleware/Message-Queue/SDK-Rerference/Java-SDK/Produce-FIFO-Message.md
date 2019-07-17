# 生产顺序消息
（说明：当topic类型选择全局顺序消息时候，应用此producer来发送消息）

消息队列 JCQ SDK支持发送两种顺序消息方式：同步发送单条消息、同步发送批量消息（最多32条）。顺序消息适用由于需要严格按照先进先出的原则进行消息发布和消费的场景，具体参数和参考示例如下。

提示：当选择生产顺序消息时，使用者只能启动一个Producer进程，更多的Producer请求会被服务端拒绝。[为了保证到达服务端的消息真正有序]

## 可配置参数
| 参数          | 参数描述                                   |
| ------------- | ------------------------------------------ |
| PROPERTY_TAGS | 可以设置消息的标签（tag），暂时支持一条tag |

## 代码示例
```Java
package com.jcloud.jcq.sdk.demo;

import com.jcloud.jcq.protocol.Message;
import com.jcloud.jcq.sdk.JCQClientFactory;
import com.jcloud.jcq.sdk.auth.UserCredential;
import com.jcloud.jcq.sdk.producer.GlobalOrderProducer;
import com.jcloud.jcq.sdk.producer.ProducerConfig;
import com.jcloud.jcq.sdk.producer.model.SendBatchResult;
import com.jcloud.jcq.sdk.producer.model.SendResult;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import java.util.ArrayList;
import java.util.List;

/**
 * 全局顺序消息生产者 demo.
 * @date 2018-05-17
 */
public class GlobalOrderProducerDemo {
    private static final Logger logger = LoggerFactory.getLogger(GlobalOrderProducerDemo.class);
    /**
     * 用户accessKey
     */
    private static final String ACCESS_KEY = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA0";
    /**
     * 用户secretKey
     */
    private static final String SECRET_KEY = "BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB0";
    /**
     * 元数据服务器地址（接入点地址）
     */
    private static final String META_SERVER_ADDRESS = "127.0.0.1:18888";
    /**
     * topic名称
     */
    private static final String TOPIC = "testTopic";

    public static void main(String[] args) throws Exception {
        // 创建全局顺序消息producer
        UserCredential userCredential = new UserCredential(ACCESS_KEY, SECRET_KEY);
        ProducerConfig producerConfig = ProducerConfig.builder()
                .metaServerAddress(META_SERVER_ADDRESS)
                .build();
        GlobalOrderProducer globalOrderProducer = JCQClientFactory.getInstance().createGlobalOrderProducer(userCredential, producerConfig);

        // 开启producer
        globalOrderProducer.start();

        // 创建message, 全局顺序消息不支持延迟投递属性设置
        Message message = new Message();
        message.setTopic(TOPIC);
        message.setBody(("this is message boy").getBytes());
        Message message1 = new Message();
        message1.setTopic(TOPIC);
        message1.setBody(("this is message1 boy").getBytes());

        // 设置message tag属性, 如有需要
        message.getProperties().put(MessageConstants.PROPERTY_TAGS, "TAG");
        
        // 同步发送单条消息
        SendResult sendResult = globalOrderProducer.sendMessage(message);
        logger.info("messageId:{}, resultCode:{}", sendResult.getMessageId(), sendResult.getResultCode());

        // 同步发送批量消息, 一批最多32条消息
        List<Message> messages = new ArrayList<>();
        messages.add(message);
        messages.add(message1);
        SendBatchResult sendBatchResult = globalOrderProducer.sendBatchMessage(messages);
        logger.info("messageIds:{}, resultCode:{}", sendBatchResult.getMessageIds(), sendBatchResult.getResultCode());
    }
}
```

