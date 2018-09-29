# java: spymemcached
## 客户端下载：
https://code.google.com/archive/p/spymemcached/?spm=a2c4g.11186623.2.5.IU7oGl
## java示例代码1
（免密访问，需要把spymemcached的jar包添加到工程目录下才能编译运行）：
```
package Spymemcached;

import java.net.InetSocketAddress;
import net.spy.memcached.MemcachedClient;
import net.spy.memcached.internal.OperationFuture;
 
public class Spymemcached {
   public static void main(String[] args) {
   
      try{
         MemcachedClient mcc = new MemcachedClient(new InetSocketAddress("ip", port));
         System.out.println("Connection to server sucessfully.");
         OperationFuture<Boolean> fo = mcc.set("key", 0, "value");
         System.out.println("set status:" + fo.get());
         System.out.println("key value - " + mcc.get("key"));
         mcc.shutdown();
         
      }catch(Exception ex){
         System.out.println( ex.getMessage() );
      }
   }
}
```
## java示例代码2
（密码访问，需要把spymemcached的jar包添加到工程目录下才能编译运行）：
```
package Spymemcached;

import java.net.InetSocketAddress;

import net.spy.memcached.AddrUtil;
import net.spy.memcached.ConnectionFactoryBuilder;
import net.spy.memcached.ConnectionFactoryBuilder.Protocol;
import net.spy.memcached.MemcachedClient;
import net.spy.memcached.auth.AuthDescriptor;
import net.spy.memcached.auth.PlainCallbackHandler;
import net.spy.memcached.internal.OperationFuture;
 
public class Spymemcached {
   public static void main(String[] args) {
   
      try{
    	  AuthDescriptor ad = new AuthDescriptor(new String[]{"PLAIN"}, new PlainCallbackHandler("test", "test"));
    	  MemcachedClient mcc = new MemcachedClient(
                             new ConnectionFactoryBuilder().setProtocol(Protocol.BINARY)
                  .setAuthDescriptor(ad)
                  .build(),
                  AddrUtil.getAddresses("ip" + ":" + port));
         System.out.println("Connection to server sucessful.");
         OperationFuture<Boolean> fo = mcc.set("key", 0, "value");
         System.out.println("set status:" + fo.get());
         System.out.println("key value - " + mcc.get("key"));
         mcc.shutdown();
         
      }catch(Exception ex){
         System.out.println( ex.getMessage() );
      }
   }
}
```
