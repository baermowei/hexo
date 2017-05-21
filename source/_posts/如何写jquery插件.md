---
title: 如何写jquery插件 
tags: jquery,jquery插件,对象扩展
grammar_cjkRuby: true
---
 ### jquery的插件机制
 

 * jQuery.extend(object) 
 * jQuery.extend([deep], target, object1, [objectN])
 * jQuery.fn.extend(object)

**代码示例**

``` stylus
//闭包限定命名空间
(function ($) {
    $.fn.extend({
        "highLight": function (options) {
            //检测用户传进来的参数是否合法
            if (!isValid(options))
                return this;
            var opts = $.extend({}, defaluts, options); //使用jQuery.extend 覆盖插件默认参数
            return this.each(function () {  //这里的this 就是 jQuery对象。这里return 为了支持链式调用
                //遍历所有的要高亮的dom,当调用 highLight()插件的是一个集合的时候。
                var $this = $(this); //获取当前dom 的 jQuery对象，这里的this是当前循环的dom
                //根据参数来设置 dom的样式
                $this.css({
                    backgroundColor: opts.background,
                    color: opts.foreground
                });
                //格式化高亮文本
                var markup = $this.html();
                markup = $.fn.highLight.format(markup);
                $this.html(markup);
            });

        }
    });
    //默认参数
    var defaluts = {
        foreground: 'red',
        background: 'yellow'
    };
    //公共的格式化 方法. 默认是加粗，用户可以通过覆盖该方法达到不同的格式化效果。
    $.fn.highLight.format = function (str) {
        return "<strong>" + str + "</strong>";
    }
    //私有方法，检测参数是否合法
    function isValid(options) {
        return !options || (options && typeof options === "object") ? true : false;
    }
})(window.jQuery);
```

**调用**

``` javascript
        //调用
        //调用者覆盖 插件暴露的共公方法
        $.fn.highLight.format = function (txt) {
            return "<em>" + txt + "</em>"
        }
        $(function () {
            $("p").highLight({ foreground: 'orange', background: '#ccc' }); //调用自定义 高亮插	件
        });
```


**参考**
[参考地址][1]


  [1]: http://www.cnblogs.com/joey0210/p/3408349.html#