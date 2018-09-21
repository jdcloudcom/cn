# 签名算法

## 签名算法

在京东云用户中心账户管理下的AccessKey管理页面申请AccessKey和SecretKey密钥对（简称AK/SK）。
AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。
AK/SK密钥对允许启用、禁用，启用后可用其调用OpenAPI，禁用后不能用其调用OpenAPI。

消息队列 JCQ HttpProxy服务会对每个访问的请求进行验证，每个提交的请求都需要在请求的header中包含签名（signature）。
消息队列 JCQ通过使用AK/SK进行对称加密的方法来验证请求的发送者身份，如果计算出来的signature和提供的一样则认为该请求是有效的；
否则，将拒绝处理这次请求，并返回 HTTP 403，Authentication failed错误。

### signature生成规则如下：

使用secretKey对signSource进行**hmac-sha1**加密得到的字符串

### signSource生成规则如下：

将公共请求头中的`accessKey`和`dateTime`和`所有参数`构造成一个map，根据key值的字典序进行排序后使用key1=value1&key2=value2&...&key100=value100的格式进行连接形成字符串。

其中发消息的messages字段需要进行预处理，然后再加入到signSource的计算中。预处理规则如下：

首先，对于每条消息（Message）将其`properties`中的键值对拿到外面，与Message的其它字段一起排序后使用key1=value1&key2=value2&...&key100=value100的格式进行拼接，
生成字符串message_signsource，然后对message_signsource计算md5值生成为message_str，
最后将所有Message按其在list中出现的顺序使用英文逗号拼接成最终的字符串message_value（格式为`message_str1,message_str2,message_str3`）【以逗号分割】作为最终messages字段值的value。

### 示例代码（Python3）

```python
#!/home/lizhijian/opt/python3.7/bin/python3

import base64
import collections
import hashlib
import hmac
import json
import random
import requests
from datetime import datetime

def md5(content):
    b = bytes(content, 'utf-8')
    h = hashlib.new('md5')
    h.update(b)
    return h.hexdigest()

def message2str(message):
    m = dict(message)  # deep copy
    m.update(m.get('properties', {}))
    m.pop('properties')
    od = collections.OrderedDict(sorted(m.items()))
    ms = '&'.join([k + '=' + str(v) for k, v in od.items()])
    return md5(ms)

def get_sign_source(headers, params):
    d = {
        'accessKey': headers['accessKey'],
        'dateTime': headers['dateTime'],
    }
    d.update(params)
    if type(d.get('messages')) == list:
        d['messages'] = ','.join([message2str(m) for m in d['messages']])
    od = collections.OrderedDict(sorted(d.items()))
    return '&'.join([k + '=' + str(v) for k, v in od.items()])

def get_signature(source, key):
    key = key.encode('utf-8')
    source = source.encode('utf-8')
    digester = hmac.new(key, source, hashlib.sha1)
    signature = base64.standard_b64encode(digester.digest())
    return signature.decode('utf-8').strip()

def send_message(access_key, secret_key, topic, type_, messages):
    url = 'http://192.168.6.1:9090/v1/messages'
    headers = {
        "Content-Type": "application/json",
        "accessKey": access_key,
        "dateTime": datetime.utcnow().isoformat(timespec='seconds') + "Z",
    }
    body = {
        "topic": topic,
        "type": type_,
        "messages": messages,
    }
    sign_source = get_sign_source(headers, body)
    signature = get_signature(sign_source, secret_key)
    headers["signature"] = signature
    resp = requests.post(url, headers=headers, data=json.dumps(body))
    return resp.text

def mysend():
    access_key = "your_access_key"
    secret_key = "your_secret_key"
    topic = "your_topic"
    type_ = "NORMAL"
    messages = []
    for i in range(10):
        messages.append({
            'body': 'message-%d' % i,
            'delaySeconds': random.randint(0, 10),
            'tag': 'tag-%d' % i,
            'properties': {str(random.randint(0, 100)): 'test'}
        })
    resp = send_message(access_key, secret_key, topic, type_, messages)
    print(resp)

if __name__ == '__main__':
    mysend()
```
