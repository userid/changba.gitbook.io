主要数据的存储结构
===
- MySQL主从结构
- zuitaoktv数据库下表的结构介绍
- Redis相关
 * user redis
 * user_extra
 * relation
 * redis_misc
 * redis_member,redis_family
 * 注意哪些数据的读写需要考虑内存的容量，以及QPS请求压力


- MemCached集群的使用
 * 主站， $mem = new useCache();
 * www站， $mem_site = new useSiteCache();
 * memcache queue的使用
 


- 增加redis字段，修改mysql表结构和索引时需要申请
