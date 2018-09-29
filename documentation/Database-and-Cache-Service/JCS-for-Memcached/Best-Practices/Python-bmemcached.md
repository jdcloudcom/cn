# Python客户端: bmemcached
## 客户端代码地址： 
https://github.com/jaysonsantos/python-binary-memcached?spm=a2c4g.11186623.2.5.cAIpTa
## 客户端版本介绍：
https://github.com/jaysonsantos/python-binary-memcached/releases?spm=a2c4g.11186623.2.4.cAIpTa 
## bmemcached安装：
<code>pip install python-binary-memcached</code>
## Python代码示例：
```
#!/usr/bin/env python
import bmemcached

if __name__ == '__main__':
client = bmemcached.Client(('ip:port',), 'username', 'password')#免密模式下不需要用户名和密码
client.set('test1', 'value1')
    print (client.get('test1'))
    client.add('test2', 'value2')
    print(client.get('test1'))
    client.replace('test1', '1')
    client.incr('test1', 1)
    client.decr('test1', 1)
    _, cas = client.gets('test1')
    client.cas('test1', 11, cas)
    dictMap = {'a': '1', 'b': '2', 'c': '3'}
    client.set_multi(dictMap)
    keys = ['a', 'b', 'c']
print (client.get_multi(keys))
```
