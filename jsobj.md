# JS对象基本用法
## 声明对象的两种语法
```
let obj={'name':'frank','age':18}
```
```
let obj=new Object({'name':'frank'})
```
## 如何删除对象的属性
```
delete obj.xxx或者delete obj['xxx']
```
* 用这个方法可以删除obj的xxx属性
```
'xxx' in obj === false
```
* 表示obj不含有xxx这个属性名，但是要和含有属性名，但是值为undefined区分
```
'xxx' in obj && obj.xxx===undefined
```
* obj.xxx === underfined不能断定'xxx'是否是obj的属性
## 如何查看对象的属性
* 查看自身所有属性
```
object.keys(obj)
```
* 查看自身属性和共有属性
```
console.dir(obj)
```
* 判断一个属性是自身的还是共有的
```
obj.hasOwnProperty('toString')
```
* 原型（每个对象都有原型）
1. 原型里存着对象的共有属性
2. obj的原型就是一个对象
3. pbj.__proto__存着这个对象的地址
4. 这个对象里有toString/constructor/valueOf等属性
* 对象的原型也是对象
1. 对象的原型也有原型
2. obj={}的原型是所有对象的原型
3. 这个原型包含的所有对象的共有属性，是对象的根
4. 这个原型也有原型，是null
* 查看属性的两种方法
1. 中括号语法(优先用)obj['key']
2. 点语法：obj.key
### obj.name等价于obj['name'],不等价于obj[name]//这里的name是字符串而不是变量
### let name='frank'
### obj[name]等价于obj['frank']
## 如何修改或增加对象的属性
### 修改或增加属性
* 直接赋值
```
let obj={name:'frank'}
obj.name='frank'
obj['name']='frank'
obj['na'+'me']='frank'
let key='name';obj[key]='frank'
```
* 批量赋值
```
Object.assign(obj,{age:18;gender:'man'})
```
### 修改或增加共有属性
* 无法通过自身修改或增加共有属性
1. let obj={},obj2={}//共有toString
2. obj.toString='xxx'只会改obj自身属性
3. obj.toString还是在原型上
* 修改或增加原型上的属性
1. obj.__proto__.toString='xxx'//不推荐使用__proto__
2. Object.prototype.toString='xxx'
3. 一般来说不要修改原型
### 修改隐藏属性
* 不推荐使用__proto__
```
let obj={name:'frank'}
let obj2=(name:'jack')
let common={kind:'human'}
obj.__proto__=common
obj2.__proto__=common
```
* 推荐使用Object.create
```
let obj=Object.create(common)
obj.name='frank'
let obj2=Object.create(common)
obj2.name='jack'
```
## 'name' in obj和obj.hasOwnProperty('name') 的区别
obj.hasOwnProperty('name')判断一个属性是自身的还是共有的
'name' in obj是判断一个对象有哪些属性
