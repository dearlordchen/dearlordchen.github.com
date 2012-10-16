---
author: jiguang
title: Javascript万能表单验证
excerpt:
layout: post
category:
  - JavaScript
tags: [ ]
post_format: [ ]
---
大家都知道验证表单采用正则表达式，在表单是固定的情况下，或者已知可以生成什么样的表单的情况下比较容易操作。但是有些情况下，或许表单是有一组定制的数据生成的，我们无法预知表单的类型，id等信息，那么是不是就只能后台验证了呢？这里[笔者][1]做了一个简单的验证程序，可以大致验证input和select必须有值，radio和checkbox至少要选中一项，代码中用到了几个YUI的函数，也可以自己用原生js或其他的库改写一下。

    var D = YAHOO.util.Dom;
    
    var checkAll = function(aClass){
        var list = D.getElementsByClassName(aClass),
            tempName = '',count,tempValue = false,value = true;
    
        for(var i = 0, j = list.length; i<j; i++){
            if((list[i].name != '')&&(list[i].type == 'radio'||list[i].type == 'checkbox')){
    
                if(list[i].name != tempName){
                    tempName = list[i].name;
                    tempValue = false;
                    count = document.getElementsByName(tempName).length-1;
                    tempValue = tempValue||(list[i].checked);
                }else{
                    tempValue = tempValue||(list[i].checked);
                }
    
                if(count != 0){
                    count--;
                }else{
                    value = value && tempValue;
                    tempValue = false;
                    tempName = '';
                }
    
            }else if(list[i].type == 'text'||list[i].type == 'password'||list[i].type == 'select-one'){
                value=value&&(list[i].value!='');
            }
    
        }
        return value;
    };

PS：这个需求有点儿蛋疼了，不过在实际工作中，什么奇怪的需求都会遇到，你懂的。

 [1]: http://jiguang.github.com "笔者"