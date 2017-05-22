---
title: input输入框总结
tags: html , input ,placeholder
grammar_cjkRuby: true
---


* 常用的类型也就除了html4中的 还可以使用到 tel 、 number 、range（方便做demo)

* 属性有 ： (autocomplate  autofocus)  (form类的)  (min max step)  (palceholder required pattern )
    size _maxlength_ readonly disable hidden


* ？*placeholder*问题

    _颜色：_ ::-webkit-input-placeholder{} :-moz-placeholde

    _js解决兼容_ ：方法很多，这里提供一种基于jq的使用虚拟span的方案，测试可用

    ```javascript
    var JPlaceHolder = {
        //检测
        _check : function(){
            return 'placeholder' in document.createElement('input');
        },
        //初始化
        init : function(){
            if(!this._check()){
                this.fix();
            }
        },
        //修复
        fix : function(){
            jQuery(':input[placeholder]').each(function(index, element) {
                var self = $(this), txt = self.attr('placeholder');
                self.wrap($('<div></div>').css({position:'relative', zoom:'1', border:'none', background:'none', padding:'none', margin:'none'}));
                var pos = self.position(), h = self.outerHeight(true), paddingleft = self.css('padding-left');
                var holder = $('<span></span>').text(txt).css({position:'absolute', left:pos.left, top:pos.top, height:h, lienHeight:h, paddingLeft:paddingleft, color:'#aaa'}).appendTo(self.parent());
                self.focusin(function(e) {
                    holder.hide();
                }).focusout(function(e) {
                    if(!self.val()){
                        holder.show();
                    }
                });
                holder.click(function(e) {
                    holder.hide();
                    self.focus();
                });
            });
        }
    };
    //执行
    jQuery(function(){
        JPlaceHolder.init();
    });
    ```

* 样式问题
    input 的字体值等不继承，所以要重新写

    _去掉默认样式_：**-webkit-appearance**:none;
             -moz-appearance: none;

    (不如直接用样式覆盖)

    _去掉背景色_： **-webkit-box-shadow**: 0 0 0px 1000px white inset;

    _palcehoder_:颜色值


* 验证问题

     基于 *html5属性*的 required tel 等

     _如何修改提示提示信息_？ 可以修改字体信息，但是不常用，不如使用插件

* 样式定制

    修改默认的 radio checkbox的显示 例如iphone的开关

    修改type='range'的默认显示
    ```css
         ::-webkit-slider-runnable-track {
                                -webkit-appearance: none;
                                height: 2px;
                                border: none;
                                margin: 1em 0;
                                background: #fff;
                                color: #fff
                            }


    ```





