# C/C++连接

下面是一个c/c++连接Jmiss-Redis的示例：

- step1：下载安装c/c++连接redis的c客户端

```
 git clone https://github.com/redis/hiredis.git 
 cd hiredis 
 make 
 sudo make install 
 ldconfig
```

- step2：编写测试代码

```
 #include <stdio.h>
 #include <stdlib.h>
 #include <string.h>
 #include <hiredis.h>
 int main(int argc, char **argv) {
     unsigned int j;
     redisContext *c;
     redisReply *reply;
     if (argc < 3) {
         printf("Usage: example jredis-hb1-prod-957e3a3d-0d76-45d4-a896-706173208db2.jmiss.jcloud.com 6379 token\n");
         exit(0);
     }
     const char *hostname = argv[1];
     const int port = atoi(argv[2]);
     const char *token = argv[3];
     struct timeval timeout = { 1, 500000 }; // 1.5 seconds

     c = redisConnectWithTimeout(hostname, port, timeout);
     if (c == NULL || c->err) {
         if (c) {
            printf("Connection error: %s\n", c->errstr);
            redisFree(c);
         } else {
            printf("Connection error: can't allocate redis context\n");
         }
         exit(1);
     }

     /* AUTH */
     reply = redisCommand(c, "AUTH %s", token);
     printf("AUTH: %s\n", reply->str);
     freeReplyObject(reply);

     /* PING server */
     reply = redisCommand(c,"PING");
     printf("PING: %s\n", reply->str);
     freeReplyObject(reply);

     /* Set a key */
     reply = redisCommand(c,"SET %s %s", "foo", "hello world");
     printf("SET: %s\n", reply->str);
     freeReplyObject(reply);

     /* Set a key using binary safe API */
     reply = redisCommand(c,"SET %b %b", "bar", (size_t) 3, "hello", (size_t) 5);
     printf("SET (binary API): %s\n", reply->str);
     freeReplyObject(reply);

     /* Try a GET and two INCR */
     reply = redisCommand(c,"GET foo");
     printf("GET foo: %s\n", reply->str);
     freeReplyObject(reply);
     reply = redisCommand(c,"INCR counter");
     printf("INCR counter: %lld\n", reply->integer);
     freeReplyObject(reply);

     /* again ... */
     reply = redisCommand(c,"INCR counter");
     printf("INCR counter: %lld\n", reply->integer);
     freeReplyObject(reply);

     /* Create a list of numbers, from 0 to 9 */
     reply = redisCommand(c,"DEL mylist");
     freeReplyObject(reply);
     for (j = 0; j < 10; j++) {
         char buf[64];
         snprintf(buf,64,"%d",j);
         reply = redisCommand(c,"LPUSH mylist element-%s", buf);
         freeReplyObject(reply);
     }

     /* Let's check what we have inside the list */
     reply = redisCommand(c,"LRANGE mylist 0 -1");
     if (reply->type == REDIS_REPLY_ARRAY) {
         for (j = 0; j < reply->elements; j++) {
            printf("%u) %s\n", j, reply->element[j]->str);
         }
     }
     freeReplyObject(reply);
     /* Disconnects and frees the context */
     redisFree(c);
     return 0;
 }
 ```
 
step3：编译

<code>gcc -o example -g example.c -I /usr/local/include/hiredis –lhiredis</code>

step4：运行测试用例

```
./example jredis-hb1-prod-957e3a3d-0d76-45d4-a896-706173208db2.jmiss.jcloud.com 6379 B69B341E5C669082EFCF2E405C626379
AUTH: OK
PING: PONG
SET: OK
SET (binary API): OK
GET foo: hello world
INCR counter: 3
INCR counter: 4
0) element-9
1) element-8
2) element-7
3) element-6
4) element-5
5) element-4
6) element-3
7) element-2
8) element-1
9) element-0
```
