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
# 2.Hash类型
redis得hash是一个String类型得field和value得映射表。<br>
它的添加，删除操作都是0(1)（平均）。<br>
<br>
设值
```
hset key field value
```
hash也有不覆盖设值
```
hsetnx key field value
```
批量设值与批量取值
```
hmset key field1 value1 field2 value2 ...
hmget key field1 field2
```
hash可以增加数字，但是没有自增1的命令
```
hincrby key field number
```
获取hash中的字段数量
```
hlen key
```
获取hash中的所有字段名或者字段值
```
hkeys key 获取该hash的所有字段名
hvals key 获取该hash的所有字段值
hgetall key 获取所有键值对
```
删除hash中的指定字段
```
hdel key field
```
# 3.List类型
redis的list类型其实就一个 每个子元素都是String类型的双向链表。<br>
我们可以通过push, pop操作从链表的头部或者尾部添加删除元素，这样list既可以作为栈，又可以作为队列。<br>
<br>
添加元素与获取元素
```
lpush key value value ... 依次从左侧添加元素
rpush key value value ... 依次从右侧添加元素
lindex key index 获取指定下标的元素
lrange key beginIndex endIndex 获取元素，下标从0开始， -1表示最后
llen key 获取元素数量
```
在指定元素的前面或者后面添加字符串
```
linsert key before/after value1 value2 在value1的前面/后面添加value2
如果符合value1的有多个元素，则默认指定最左边的那个
```
在指定的下标设值元素
```
lset key index value
```
删除
```
lrem key number value
删除number个值为value的元素，number是正数则从左侧开始删除，number是负数则从右侧开始删除，number是0则删除所有。
ltrim key index1 index2
保留下标从index1到index2的元素，其余的去除
```
弹出
```
lpop key 左侧弹出
ropo key 右侧弹出
rpoplpush key1 key2 从key1的右侧弹出元素，添加到key2的左侧
```
