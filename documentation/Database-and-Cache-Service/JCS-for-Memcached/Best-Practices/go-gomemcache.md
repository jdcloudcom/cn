# go客户端: gomemcache(该客户端不支持密码连接)
## 客户端介绍：
https://godoc.org/github.com/bradfitz/gomemcache/memcache 
## 将客户端包下载到GOPATH：
<code>go get github.com/bradfitz/gomemcache/memcache</code>
## go代码示例：
```
package gomemcached

import (
	"fmt"
	"github.com/bradfitz/gomemcache/memcache"
)

func main() {
	mc := memcache.New("ip:port")//可通过添加多个实例的ip:port来实现集群版客户端
	mc.Set(&memcache.Item{Key: "key", Value: []byte("value")})

	it, err := mc.Get("key")
	if err != nil {
		panic(err)
	}

	fmt.Printf("Value: %s", it.Value)
}
```
