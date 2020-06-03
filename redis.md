# 基本数据类型
## 1.String类型
String是最简单的类型，一个key对应一个value，String类型是二级制安全的。redis的String可以包含任何数据，比如jpg图片或者序列化的对象。<br>
```
set key value
```
设置key对应的值为String类型的value。
```
get key
```
获取某个key的值
```
setnx key value
```
不覆盖设值。如果key已存在会返回0，并且设置不成功。如果key不存在会返回1，并且设值。nx是not exist的意思。
```
setex key number value
```
例：setex color 10 red 设置color对应的value的值为red，并且有效期为10秒，10秒后删除该key。


