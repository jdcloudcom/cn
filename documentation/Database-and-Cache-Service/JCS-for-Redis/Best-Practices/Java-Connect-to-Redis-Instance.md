# Java连接
- step1：下载redis的java客户端参考地址：<a href="https://github.com/xetorthio/jedis">https://github.com/xetorthio/jedis</a> </p>

- step2：编写测试用例

```
package com.jd.jmiss;
import redis.clients.jedis.Jedis;
public class JedisTester {

public static void main(String[] args) {
    Jedis jedis = null;
    try {
        String host = "${your redis domain}";//控制台显示访问地址
        int port = 6379;
        String token = "${redis-id}:{your password}";//控制台显示的token
        jedis = new Jedis(host, port);
        //鉴权信息
        jedis.auth(token);
        String key = "redis";
        String value = "jmiss-redis";
        //set一个key
        String retCode = jedis.set(key, value);
        System.out.println("Set Key: " + key + " Value: " + value + "  return code is: " + retCode);
        //get 设置进去的key
        String getvalue = jedis.get(key);
        System.out.println("Get Key: " + key + " ReturnValue: " + getvalue);
    } catch (Exception e) {
        e.printStackTrace();
    }
    finally {
        if(null != jedis){
            jedis.quit();
            jedis.close();
        }
    }
}
}
```

## java maven + spring + jedis

- step1: 引入maven依赖

```
<dependencies>
<dependency>
   <groupId>redis.clients</groupId>
   <artifactId>jedis</artifactId>
   <version>2.5.2</version>
</dependency>

<dependency>
    <groupId>org.springframework.data</groupId>
    <artifactId>spring-data-redis</artifactId>
    <version>1.7.2.RELEASE</version>
</dependency>
</dependencies>

```


- step2：配置Spring元素


```
<beans>
<bean id="jedisPoolConfig" class="redis.clients.jedis.JedisPoolConfig">
    <!-- <property name="maxActive" value="${redis.pool.maxTotal}" />-->
     <property name="maxIdle" value="${redis.pool.maxIdle}" />
     <property name="timeBetweenEvictionRunsMillis" value="${redis.pool.timeBetweenEvictionRunsMillis}" />
     <property name="minEvictableIdleTimeMillis" value="${redis.pool.minEvictableIdleTimeMillis}" />
     <property name="testOnBorrow" value="${redis.pool.testOnBorrow}" />
     <property name="testWhileIdle" value="${redis.pool.testWhileIdle}" />
     <property name="maxWaitMillis" value="5000"/>
     <property name="minIdle" value="10" />
     <property name="numTestsPerEvictionRun" value="10" />
     <property name="testOnReturn" value="true" />
     <property name="softMinEvictableIdleTimeMillis" value="60000" />
</bean>
<bean id="jedisConnectionFactory" class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory" destroy-method="destroy">
     <property name="poolConfig" ref="jedisPoolConfig"></property>
     <property name="hostName" value="${redis.pool.host}"></property>
     <property name="port" value="${redis.pool.port}"></property>
     <property name="password" value="${redis.pool.pass}"></property>
     <property name="timeout" value="${redis.pool.timeout}"></property>
     <property name="usePool" value="true"></property>
</bean>
<bean id="redisTemplate" class="org.springframework.data.redis.core.RedisTemplate">
     <property name="connectionFactory" ref="jedisConnectionFactory"></property>
     <property name="keySerializer">
            <bean class="org.springframework.data.redis.serializer.StringRedisSerializer"/>
     </property>
</bean>
</beans>
```


- step3: 通过Properties文件配置redisPool相关参数


```
#IP地址
redis.pool.host=jcache-online20***59f-aeba-46*0-9fec-2de*****cd4c.jdicts.jcloud.com
#端口号
redis.pool.port=6379
redis.pool.pass=89376FC86*******403911BF5C538
#最大idle
redis.pool.maxIdle=300
#最大分配对象
redis.pool.maxTotal=600
#多长时间检查空闲连接
redis.pool.timeBetweenEvictionRunsMillis=5000
#空闲连接多长时间收回
redis.pool.minEvictableIdleTimeMillis=8000
#上面两个值的和加起来应该小于15秒，否则服务器会断掉连接
#borrow object
redis.pool.testOnBorrow=true
redis.pool.timeout=3000
redis.pool.testWhileIdle=true
```


- step4:定义 redis value对象 这里需实现序列化


```
class JMiss implements Serializable {
private String time;

public String getTime() {
    return time;
}

public void setTime(String value) {
    this.time = value;
}
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;

    JMiss jMiss = (JMiss) o;

    return !(time != null ? !time.equals(jMiss.time) : jMiss.time != null);
}
@Override
public int hashCode() {
    return time != null ? time.hashCode() : 0;
}
@Override
public String toString() {
    return "JMiss{" +
            "time='" + time + '\'' +
            '}';
}
}
```


- step5:定义JMiss控制器类


```
public class JMissProcessor {

private RedisTemplate<String, JMiss> redisTemplate;

public void setRedisTemplate(RedisTemplate<String, JMiss> redisTemplate){
    this.redisTemplate = redisTemplate;
}

public void setJMiss(String key, final JMiss jMiss){
    ValueOperations<String, JMiss> valueOps = redisTemplate.opsForValue();
    valueOps.set(key, jMiss);
}

public JMiss getJMiss(String key){
    ValueOperations<String, JMiss> valueOps = redisTemplate.opsForValue();
    return valueOps.get(key);
}
}
```


- step6:调用示例代码


```
public class JedisTester {

public static void main(String [] args){
    ApplicationContext context = new ClassPathXmlApplicationContext("spring-config.xml");
    final RedisTemplate<String, JMiss> redisTemplate = (RedisTemplate<String, JMiss>) context.getBean("redisTemplate");
    JMissProcessor processor = new JMissProcessor();
    processor.setRedisTemplate(redisTemplate);
    JMiss jmissIn = new JMiss();
    String key = "jmiss_redis_time";
    for(int i = 0 ; i < 10000; ++ i){
        System.out.println("i is " + i);
        SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss.SS");
        jmissIn.setTime(df.format(new Date()));
        processor.setJMiss(key,jmissIn);
        JMiss jmissOut = processor.getJMiss(key);
        System.out.println("jmissOut is " + jmissOut);
        if(jmissOut == null || !jmissIn.equals(jmissOut)){
            System.out.println("error happen");
        }else{
            System.out.println("read write succss");
        }
        try {
            Thread.sleep(1000 * i);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
}
```
