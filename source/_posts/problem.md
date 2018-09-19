---
    title: 开发常见问题及解决方法
---

## HTML+CSS

### 强制换行

```html
    <style>
        .jemery{
            word-break:break-all;
            word-wrap:break-word;
        }
    </style>
```



### 字数超过长度时自动使用省略号

```html
    <style>
        .jemery{
            text-overflow:ellipsis;
            overflow:hidden;
            white-space:nowrap;
        }
    </style>
```

### 使用:before给一个方框画上三角形

> 正常显示

```html
<style>
    .example:before {
        content: '';
        width: 0;
        height: 0;
        border: 10px solid transparent; /*调整小三角形的大小*/
        border-right-color: #fff;/*改变小三角的颜色（最好就是和父级div的背景颜色相同）;right是用于调整小三角的方向*/
        position: absolute;
        left: 280px;/*调整小三角形的位置*/
        top: 45%;/*调整小三角形的位置*/			    
    }
</style>
<div class="example" style="width:300px; height:150px;background: #66ccFF;position: relative;">
</div>
```

![](../../../../css/images/error/problem_1.png '正常显示')

> hover上去才有效果

```html
<style>
    .example:hover:before {
        content: '';
        width: 0;
        height: 0;
        border: 10px solid transparent; /*调整小三角形的大小*/
        border-right-color: #fff;/*改变小三角的颜色（最好就是和父级div的背景颜色相同）;right是用于调整小三角的方向*/
        position: absolute;
        left: 280px;/*调整小三角形的位置*/
        top: 45%;/*调整小三角形的位置*/			    
    }
</style>
<div class="example" style="width:300px; height:150px;background: #66ccFF;position: relative;">
</div>
```

![](../../../../css/images/error/problem_1.png 'hover效果')

## JavaScript

### this和其他选择器一起用

```javascript
    var jemery = $(this).find('#PrdCode').attr('data-PrdCode');
    // #PrdCode 和 data-PrdCode 都是自己所想要的操作的东西
```


### 获取URL传递过来的信息

```javascript
    function getUrlParam(name){
        //获取URL中的参数
        var paramstr = window.location.search;
        var reg = new RegExp("(^|&)"+ name + "=([^&]*)(&|$)"); // 构造一个含有目标参数的正则表达式对象
        var r = paramstr.substr(1).match(reg); // 匹配目标参数
        if(r != null) return unescape(r[2]);  return null; //返回参数值
    }
```
> 例如当前网址为：https://www.baidu.com/s?wd=unescape&rsv_spt=1&rsv_iqid=0xbbb6086400022313&issp=1&f=8&rsv_bp=0&rsv_idx=2&ie=utf-8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=6&rsv_sug1=6&rsv_sug7=101
>> console.log(getUrlParam('wd')); ==> unescape
>> console.log(getUrlParam('rsv_spt')); ==> 1


### 过滤一段HTML代码中的标签，指定标签除外

```javascript
    var description = '<h1><a href="#content" id="logo">Jemerys Blog</a></h1>';	
    var reg = /<(?!a|\/a).*?>/g;
    console.log(description)
    console.log(description.replace(reg, ""));
```
> 案例中指定`<a></a>`不过滤，其他都过滤，运行结果如下图所示。

![](../../../../css/images/error/problem_2.png '')

> **如果是单标签如img标签，正则表达式为`var reg = /<(?!img).*?>/g;`**

### 关于将一个数组中的空数据替换成指定内容

```javascript
    var jemery = ["","","","","","5","","","","7","",""];
    for(var i in jemery){
        if(jemery[i] == ""){
            jemery[i] = 0;
        }
    }
    console.log(jemery);//[0, 0, 0, 0, 0, "5", 0, 0, 0, "7", 0, 0]
```

> 但是如果有多个空格会如何呢？
```javascript
    var jemery = ["    ","","","","","5","  ",""," ","7","",""];
    for(var i in jemery){
        if(jemery[i] == ""){
            jemery[i] = 0;
        }
    }
    console.log(jemery);//["    ", 0, 0, 0, 0, "5", "  ", 0, " ", "7", 0, 0]
```
> 可见并不能达到预期的效果，此时需有其他操作，使用trim函数
```javascript
    var jemery = ["    ","","","","","5","  ",""," ","7","",""];
    for(var i in jemery){
        if(jemery[i].trim() == ""){
            jemery[i] = 0;
        }
    }
    console.log(jemery);//[0, 0, 0, 0, 0, "5", 0, 0, 0, "7", 0, 0]
```