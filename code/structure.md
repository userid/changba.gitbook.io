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
- `php`自带的函数一定要准确使用，不要理解错含义， 比如`empty()`,`array_merge()`,
`in_array()`,`usort()`等, 注意参数的顺序;
- `php`代码中禁止使用引用;
- `php` 谨慎区分`==`和`===`的含义， 注意`null`，`0`,`"0"`,`false`的含义;
- 和客户端约定返回变量时，尽量用`"0"`和`"1"`取代`false`和`true`;
- 代码风格要一致,修改现有代码不要改变原代码不一致的写法; 新写代码时注意:
 * `if`和`function`后的`{`不单独换行;
 * 用4个空格代替`Tab`;
 * `php`文件的尾部，不能有`?>`, 最好有一个单独的回车结尾;
 * 类的每个单词首字母大写;
 * 函数的首字母小写，其他单词的首字母小写;
 * 变量可以用和函数相同的方式，也能用全小写，`_`分隔的方式;
 


