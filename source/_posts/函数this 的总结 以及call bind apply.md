---
title: 函数this 的总结 以及call bind apply 
tags: 函数,this,javascript, es6
grammar_cjkRuby: true
---

*  ## js 中this用法

 1. 在一般函数方法中使用 this 指代全局对象
 2. 作为对象方法调用，this 指代上级对象
 3. 作为构造函数调用，this 指代new 出的对象
 4. apply/call 调用 ，apply方法作用是改变函数的调用对象

	apply方法（或者call方法）不仅绑定函数执行时所在的对象，还会立即执行函数，因此不得不把绑定语句写在一个函数体内。
5.	bind方法用于将函数体内的this绑定到某个对象，然后返回一个新函数。
	

* ## apply /call  bind的使用

[es5的this几种情况][1]

[es5 this](http://www.cnblogs.com/pabitel/p/5922511.html) / http://javascript.ruanyifeng.com/oop/this.html
[js中this](https://segmentfault.com/a/1190000003046071)


  [1]: http://javascript.ruanyifeng.com/oop/this.html