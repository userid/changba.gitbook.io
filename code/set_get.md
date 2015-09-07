常见数据的存取
====
###用户相关的数据
 - 得到个人主页的相关信息(数字)

```php
/*
$curuserid==$userid 表示获取自己的信息;
$types是一个数组, 有以下的一个或多个参数：
gold 金币数
relation 相互关系
baggift  背包礼物数
forward_work  转发数
honor_work    上榜作品数
family        群组数 (仅有一个群组时返回数组)
room          包房数(仅有一个包房时返回数组)
fans          粉丝数
friends       好友数
work_listen   听过次数
user_work     作品数
my_duet       合唱数
*/
$api = ZuiTaoKTV::GetInstance();
$api->getUserPersonalNum( $curuserid , $userid, $types);
#例如:
$api->getUserPersonalNum(0,15357,array("room","user_work",));
/*
返回值(未查询的字段不计算):
UserPersonalNum Object
(
    [gold] => 0
    [forward_work] => 0
    [honor_work] => 0
    [family] => 0
    [room] => 1
    [fans] => 112
    [friends] => 0
    [my_duet] => 0
    [work_listen] => 0
    [user_work] => 5
    [relation] => 0
    [family_info] => 
    [room_info] => Array
        (
            [id] => 139600
            [name] => 了然的包房
        )

)

*/
```
- 用户手机号相关:
```php
#根据手机号获得用户名, 这个接口稍重，少用
UserService::getUserIdByPhone($phone);
#根据用户id，查找用户手机号
UserService::getPhoneByUserId($userid);
```

- 重置密码
```php
UserService::updatePassword($curuserid,$md5pwd);
```
- 判断唱吧号或者邮箱有没有被注册
```php
$api = ZuiTaoKTV::GetInstance();
$api->checkChangbaIDRegistered($accountid);
```
- 敏感词检测
 
`TODO`


### 文件上传


###作品相关的数据
- 听过次数
```
$api->RecordWorkListenedTimeToRedis($workid, $listenedtime, $listennum=1);
# 在changba.com上听歌增加听过次数的方法
$api-> RecordWorkListenedTimeOnWebSite($workid, $ip);
#得到听过次数
$api->GetUserWorkListenNum($workid);
```
- 最近听众
```php
$rService = new RecentListenerService();
$rService->getRecentListeners($workid);
```
- 评论
```php
#获取评论
$api->GetWorkComment2($workid,$start=0,$num=20,$asc='DESC',$needReplyCount=true, $workOwner='');
#最常见的用法
$api->GetWorkComment2($workid,$start,$num); //获取$start, $num个评论
```

###会员相关


###群组相关


