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
```TODO```

接口的权限控制，对修改用户数据和读取用户私有信息的接口，需要校验用户的token,
参见ktvbox.php的`checkKTVToken()`.


