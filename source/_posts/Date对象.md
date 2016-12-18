---
title: Date对象
date: 2016-12-18 10:00:02
tags: javascript, date对象
---
# Date对象的使用
----------
## date对象简述
### Date()与new Date()
`Date()`可以当作普通函数直接调用，无论有没有参数，返回的都是当前的时间字符串
`new Date()`是实例化一个日期对象，有无参数时：
1.不传参数时：返回当前世界的字符串
2.milliseconds，1970年1月1日00:00:00 UTC开始计算的毫秒数作为参数。（可以为负值表示1970以前）
3.datestring，时间值字符串形式多种，常用的有
	```
	new Date('2013-2-15')
	new Date('2013/2/15')
	new Date('02/15/2013')
	```

	事实上所用可以被`Date.parse()`解析的都可以传进去
 4.new Date(year, month [, day, hours, minutes, seconds, ms])
	> 如果采用这种格式，最少需要提供两个参数（年和月），其他参数都是可选的，默认等于0。因为如果只使用“年”这一个参数，Date对象会将其解释为毫秒数。

 -----------
 new Date()默认会自动调用`Date.parse()`与`Date.UTC()`方法
 * `Date.parse()`解析日期字符串
 * `Date.UTC()`解析上面4的方法


**new Date()参数合法性与智能折算**
字符串不合法时，返回NaN或Invalid Date。如`new Date('2016-12-32')`；
使用4的方法，会自动折算,如`new Date(2016,12,33)`

## 日期的运算
* 加法---字符串运算
* 减法--数值运算
* 全等 --都是false

## 静态方法
* Date.parse()
	>方法用来解析日期字符串，返回距离1970年1月1日 00:00:00的毫秒数。
	>失败返回NaN
* Date.UTC()
	>Date对象返回的都是当前时区的时间。Date.UTC方法可以返回UTC时间（世界标准时间）
* Date.now() es5方法
	>方法返回当前距离1970年1月1日 00:00:00 UTC的毫秒数


## 实例方法

>to类：从Date对象返回一个字符串，表示指定的时间。
>get类：获取Date对象的日期和时间。
>set类：设置Date对象的日期和时间。

