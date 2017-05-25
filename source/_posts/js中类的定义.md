---
title: js中类的定义
tags: es6 , javascript 
grammar_cjkRuby: true
---

## es5定义类的三种写法

 - 基于原型链的构造函数
  也是最常用最流行的写法，可以方便实现继承和扩展，有自己的私有方法
  
  - Object.create() 
  很方便的基于对象生成对象，简单，但是不能私有属性和方法，实例之间不共享数据
  
  -封装对象模拟类

``` javascript
  
  　var Cat = {
　　　　createNew: function(){
　　　　　　var cat = {};
　　　　　　cat.name = "大毛";
　　　　　　cat.makeSound = function(){ console("喵喵喵"); };
　　　　　　return cat;
　　　　}
　　};
  //调用
  var cat1 = Cat.createNew();
  
  //继承
  // 后者调用createNew()
  
  var Dog{
  createNew:function(){
  	var dog=Cat.createNew();
	return dog
	
  }
  }
```

### es6 类

es6之后就有自己的类了，
用法简单明了，方便继承。

es6 的类实现就是基于原型链的， bable转换后的代码就是es5的原型链写法；但是是真正的类哦！


参考

http://www.ruanyifeng.com/blog/2012/07/three_ways_to_define_a_javascript_class.html
   
   

