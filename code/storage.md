主要数据的存储结构
===
- `MySQL`主从结构
- 几个主要的`mysql`主库和从库的分布
- `zuitaoktv`数据库下表的结构介绍
- `Redis`相关
 * `user redis`
 * `user_extra`
 * `relation`
 * `redis_misc`
 * `redis_member`,`redis_family``
 * 注意哪些数据的读写需要考虑内存的容量，以及`QPS`请求压力


- `MemCached`集群的使用
 * 主站， `$mem = new useCache();`
 * `www`站， `$mem_site = new useSiteCache();`
 * `memcache queue`的使用
 


- 增加`redis`字段，修改`mysql`表结构和索引时需要申请
