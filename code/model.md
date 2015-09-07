常见对象的构建
===
##### 构建`User`对象
```php
//该方法用来获得用户信息，该信息首先来自memcache，有10分钟延时，适合快速获取非及时的用户信息
UserService::getUserInfoSnapshot($userid);

//该方法用来获得用户信息，从redis中获取用户信息，不包含敏感信息
UserService::GetUserInfoFromRedis($userid);
#等同于
$api = ZuiTaoKTV::GetInstance();
$api->GetUserInfoFromRedis($userid);

//不包含GPS位置信息的函数
UserService::GetUserInfoWithLocationFromRedis($userid);
```

##### 构建`UserWork`对象

```php
$api = ZuiTaoKTV::GetInstance();
$api-> GetUserWork($workid,$curuserid='',$listen_count=1, $isSimpleRet = false, $getfromtrash = false);
/*
  其中$listen_count是一个废弃的参数， $isSimpleRet表示是否获取听过次数、礼物数、转发数、评论数的信息，
  $getfromtrash表示是否读取已经删除的作品 这个参数只在导出用户作品时用到。
*/
#因此常见用法就是：
$api-> GetUserWork(9999);
$api-> GetUserWork(9999, 15357,1, true);

```

##### 构建`Song`对象
```php

```

##### 构建`Duet`合唱对象
```php

```

##### 构建`Gift`礼物相关对象
```php

```

