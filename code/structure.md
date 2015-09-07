主要接口和代码分布
===
##### api接口的描述，大致都在ktvbox.php中的ac='xxxx'的分支中

##### 代码结构与规范
 

###### ktvserver的代码
应该归类好文件结构

```
ktvbox.php
ktvbox_XXXXX.php
ZuiTaoKTV.php
DataStruct.class.php
common/common.inc.php
common/config.inc.php

libs/
background_worker/
tools/
common/
live/
service/
accounts/
maintenance/
```
###### www的代码
`TODO`

#####接口的权限控制
对修改用户数据和读取用户私有信息的接口，需要校验用户的token,
参见ktvbox.php的`checkKTVToken()`.

##### 代码规范
- php不能使用`require_once`和`include_once`, 对文件引用时不能使用相对路径，尽量使用绝对路径:
```
include __DIR__ . '/common/common.inc.php';
```
- SQL语句中的变量需要用单引号包括，是数字的参数用`intval()`转化，字符串在使用时
用`check_input()`转义特殊字符。
- 不重复多次构造redis和memcache对象，尽量使用单例或者复用对象。要减少网络请求和
重复的`mysql`和`redis`调用。
- `mysql`查询尽量有`limit`限制获取总数，不要获取超过1000的行数，不要有不经过索引
的查询，和like "%XXX%"一样的慢查询。
- `redis`有大量多行执行时，使用`multi()`和`exec()`组合的模式;
- `redis`对象在使用前一定要调用`init()`, 使用`multi()`后一定不能忘了`exec()`;

