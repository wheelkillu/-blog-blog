# 今天学习了jQuery的设计模式，下面是我的笔记
首先先说一下命名风格，在有如下代码
```
const div=$('div#test')
```
中，我们如何确定div是DOM对象还是jQuery对象呢？
我们有一个约定俗成的说法就是：代码中所有$开头的变量，都是jQuery对象，则可把如上代码改成
```
const $div=$('div#test')
```
这样我们就不用迷惑啦，那么下面来解决一下这么几个问题
1. jQuery 如何获取元素
```
$('#myId')//获取ID为myId的元素
$('#div').find('.red')//查找#div里的.red元素
$('#div').parent()//获取#div的父元素
$('#div').children()//获取#div的子元素
$('#div').siblings()//获取与#div同一级别的元素
$('#div').index()//获取#div该元素从0开始的排行
$('#div').next()//获取该元素的下一个元素
$('#div').prev()//获取该元素的上一个元素
$('.red').each(fn)//遍历元素并对每个元素执行fn这个函数
```
2. jQuery 的链式操作是怎样的
我们的jQuery可以对元素进行一系列操作，并且把所有的操作连接在一起，这就叫做链式操作比如
```
$('#test').find('.child').addClass('red') 
```
也可以分解开来写成：
```
$('#test')//找到#test元素
 .find('.child')//选择其中的.child元素
 .addClass('red')//对所有的.child元素加上red这个类 
```
3. jQuery 如何创建元素
```
$('<div><span>1</span></div>')
$('<p>hi</p>')
```
4. jQuery 如何移动/插入元素
在jQuery中我们有两组方法来移动元素，第一组是直接移动元素，另一组是移动其他的元素，使目标元素到达我们想要的位置</br>
* 假如我们现在选中了一个div元素，要把div元素移动到p的后面,两种方法分别这样操作</br>
第一种方法是使用insertAfter(),把div元素移动到p元素后面：
```
$('div').insertAfter($('p'))//返回div元素
```
另一种方法是使用.after(),把p元素放在div元素前面
```
$('p').after($(''div))//返回p元素
```
这两种方法都是在现存元素的外部，从后面插入元素，但是返回的元素不一样</br>
相反,如果我们想从前面插入元素，就要使用.insertBefore()和.before()</br>
以上两种方法都是从现存元素的外部插入元素，如果我们想从内部插入元素，就要用如下的办法：</br>
* 假如我们有如下代码
```
<div class="inner">Hello</div>
```
我们想在div元素内部插入一个p标签，第一种方法是使用.appendTo()
```
$('<p>Test</p>').appendTo('.inner')
```
另一种方法是使用.append
```
$('.inner').append('<p>Test</p>')
```
同理，从现存元素内部前面插入元素就要使用.prependTo()和.prepend()
5. jQuery 如何修改元素的属性
我们可以使用同一个函数来完成取值和赋值（getter/setter）
```
$('h1').html()//html()内没有参数，表示取出h1的值
$('h1').html('hi')//html()内有参数hi，表示对h1进行赋值
```
我们常用的取值和赋值方法如下
* 注意：$div大部分时候对应多个div元素，即修改的时候会修改其中所有元素的值，但是取值的时候只取出第一个元素的值
```
$div.text(?)//读写文本内容，但是当取值时，它会取出所有元素的text内容
$div.html(?)//读写HTML内容
$div.attr('title',?)//读写匹配的元素集合中的第一个元素的属性的值
$div.css({color:'red'})//修改css样式
$div.addClass('blue')//添加类名
$div.on('click',fn)//绑定事件处理函数
$div.off('click',fn)//移除事件处理函数
```

##### 参考文案：http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html
##### 参考文案：https://www.jquery123.com/
