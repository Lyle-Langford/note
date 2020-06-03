# 1.String类型
String是最简单的类型，一个key对应一个value，String类型是二级制安全的。redis的String可以包含任何数据，比如jpg图片或者序列化的对象。<br>
<br>
设置key对应的值为String类型的value。
```
set key value
```
获取某个key的值
```
get key
```
不覆盖设值。如果key已存在会返回0，并且设置不成功。如果key不存在会返回1，并且设值。nx是not exist的意思。
```
setnx key value
```
指定key的有效期。例：setex color 10 red 设置color对应的value的值为red，并且有效期为10秒，10秒后删除该key。
```
setex key number value
```
局部字符替换。number表示从第几个字符开始替换，数字从0开始。
```
setrange key number value
可以按以下步骤尝试:
set email eson@126.com, 值为eson@126.com;
setrange email 5 gmail.com, 值为eson@gmail.com;
setrange email 5 xx, 值为eson@xxail.com;
```
由局部字符设值，就有局部取值。下标还是从0开始。
```
getrange key number1 number2
```

批量设值。返回ok表示全部设置车工，返回0表示没有任何值被设置。
```
mset key1 value1 key2 value2 ......
```
批量设值（不覆盖）
```
msetnx key1 value1 key2 value2 ......
```
有批量设值，就有批量取值。
```
mget key1 key2 ......
```
先取值再设值。先获取key原来的值，再给这个key设值新的值
```
getset key value
```
对值为纯数字的，可以自增
```
incr key 自增1
incrby key number 增加指定的数字
decr key 自减
decrby key number 减少指定的数字
```
追加字符串，返回新字符串值得长度。如果没有这个key，则等同于set
```
append key value
```
获取长度
```
strlen key
```

