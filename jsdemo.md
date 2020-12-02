## JS的诞生
# JavaScript 的历史
它最初由[Netscape](https://baike.baidu.com/item/%E7%BD%91%E6%99%AF/70176?fromtitle=netscape&fromid=2778944)布兰登设计。[Ecma国际](https://baike.baidu.com/item/Ecma%E5%9B%BD%E9%99%85)以JavaScript为基础制定了[ECMAScript](https://baike.baidu.com/item/ECMAScript)标准。JavaScript也可以用于其他场合，如服务器端编程。
Netscape在最初将其脚本语言命名为LiveScript，后来Netscape在与Sun合作之后将其改名为JavaScript。JavaScript最初受Java启发而开始设计的，目的之一就是“看上去像Java”，因此语法上有类似之处，一些名称和命名规范也借自Java。但JavaScript的主要设计原则源自Self和Scheme。JavaScript与Java名称上的近似，是当时Netscape为了营销考虑与Sun微系统达成协议的结果。为了取得技术优势，微软推出了JScript来迎战JavaScript的脚本语言。为了互用性，Ecma国际（前身为欧洲计算机制造商协会）创建了ECMA-262标准（ECMAScript）。两者都属于ECMAScript的实现。尽管JavaScript作为给非程序人员的脚本语言，而非作为给程序人员的脚本语言来推广和宣传，但是JavaScript具有非常丰富的特性。
发展初期，JavaScript的标准并未确定，同期有Netscape的JavaScript，微软的JScript和CEnvi的ScriptEase三足鼎立。1997年，在ECMA（欧洲计算机制造商协会）的协调下，由Netscape、Sun、微软、Borland组成的工作组确定统一标准：ECMA-262。
# JavaScript 诞生记
1994年，网景公司（Netscape）发布了Navigator浏览器0.9版，虽然轰动一时，但是这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。所以他们急需一种网页脚本语言，使得浏览器可以与网页互动。此时，34岁的布兰登登场了。1995年4月，网景公司录用了他。布兰登的主要方向和兴趣是函数式编程，网景公司招聘他的目的，是研究将Scheme语言作为网页脚本语言的可能性。但是一个月之后，1995年5月，网景公司做出决策，未来的网页脚本语言必须"看上去与Java足够相似"，但是比Java简单，使得非专业的网页作者也能很快上手。布兰登被指定为这种"简化版Java语言"的设计师。但是，他对Java一点兴趣也没有。为了应付公司安排的任务，他只用10天时间就把Javascript设计出来了。
# JavaScript 的10个设计缺陷
1. 不适合开发大型程序
   Javascript没有名称空间，很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。
2. 非常小的标准库
   Javascript提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。
3. null和undefined
null属于对象（object）的一种，意思是该对象为空；undefined则是一种数据类型，表示未定义。

```typeof null; // object

　　typeof undefined; // undefined
```
两者非常容易混淆，但是含义完全不同。
```
　　var foo;

　　alert(foo == null); // true

　　alert(foo == undefined); // true

　　alert(foo === null); // false

　　alert(foo === undefined); // true
```
在编程实践中，null几乎没用，根本不应该设计它。
1. 全局变量难以控制
   Javascript的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。

```a = 1;

　　(function(){

　　　　b=2;

　　　　alert(a);

　　})(); // 1

　　alert(b); //2
```
5. 自动插入行尾分号
   Javascript的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。

比如，下面这个函数根本无法达到预期的结果，返回值不是一个对象，而是undefined。

```　　function(){

　　　　return
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
```
原因是解释器自动在return语句后面加上了分号。

```　　function(){

　　　　return;
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
```
6. 加号运算符
   +号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。

```　　alert(1+10); // 11

　　alert("1"+"10"); // 110
```
如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。

```　　alert(1+"10"); // 110

　　alert("10"+1); // 101
```
这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。
7. NaN
   NaN是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：

```　　NaN === NaN; //false

　　NaN !== NaN; //true

　　alert( 1 + NaN ); // NaN
```
与其设计NaN，不如解释器直接报错，反而有利于简化程序。
8. 数组和对象的区分
   由于Javascript的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。[Douglas Crockford](http://crockford.com/javascript/)的代码是这样的：

```　　if ( arr &&
　　　　typeof arr === 'object' &&
　　　　typeof arr.length === 'number' &&
　　　　!arr.propertyIsEnumerable('length')){

　　　　alert("arr is an array");

　　}
``` 
9. == 和 ===
    ==用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。

```　　"" == "0" // false

　　0 == "" // true

　　0 == "0" // true

　　false == "false" // false

　　false == "0" // true

　　false == undefined // false

　　false == null // false

　　null == undefined // true

　　" \t\r\n" == 0 // true
```
因此，推荐任何时候都使用"==="（精确判断）比较符。
10. 基本类型的包装对象
    Javascript有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。

```　　new Boolean(false);

　　new Number(1234);

　　new String("Hello World");
```
与基本数据类型对应的对象类型，作用很小，造成的混淆却很大。

```　　alert( typeof 1234); // number

　　alert( typeof new Number(1234)); // object
```
### 参考文献：
https://baike.baidu.com/item/javascript#4 
http://www.ruanyifeng.com/blog/2011/06/birth_of_javascript.html   
http://www.ruanyifeng.com/blog/2011/06/10_design_defects_in_javascript.html
