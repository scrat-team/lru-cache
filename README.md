cache
=========

cache 模块基于 [node-lru-cache](https://github.com/isaacs/node-lru-cache) 修改而来，加入了 localStorage 支持。

cache 返回一个构造函数。

### LRUCache(options)

缓存构造函数。

#### 配置说明

* __namespace__：缓存命名空间，用做缓存 key 的一部分
* __max__：缓存内容数量，默认为 Infinity
* __maxAge__：缓存全局过期时间，单位秒，默认不过期
* __dispose__：缓存被删除时的回调函数，接收缓存的 key, value 作为参数
* __localStorage__：是否启用 localStorage 对缓存进行持久化，默认开启

``` javascript
var LRU = require('cache'),
    options = {
        namespace: 'waterfall',
        maxAge: 3 * 60
    },
    cache = new LRU(options);
```

__注意__ 开启了 localStorage 持久化后，JSON 序列化的过程可能会改变缓存的对象，不要缓存无法被 JSON 序列化的对象。

### cache.set(key, value, [expire])

__注意__ 这里设置了 expire 会覆盖全局的 maxAge 设置。

### cache.has(key)

### cache.get(key)

### cache.del(key)

### cache.reset()
