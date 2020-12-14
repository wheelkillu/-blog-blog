# 排序小博客
#### 今天学习了几种排序方法，选择排序、快速排序、归并排序、计数排序，个人比较喜欢后两种，下面就用我的思路来说一下这两种排序方法
## 归并排序
假设我现在是一名体育委员，要将学好不同的学生按顺序排好，<br/>
现在有5名同学，学号分别是12，14，8，2，26，<br/>
我手里的办法只会将知道顺序的两个部分进行排序，
接下来我把他们分为两个部分，左半部分是12、14，右半部分是8，2，26，<br/>
拿出左半部分，再分成12和14两个部分，<br/>
我们当作12和14这两个学号的同学是两个已经排好序的个体，<br/>
用手里已有的办法，可以将这个两个同学排好序，<br/>
再拿出整体同学的右半部分，分成8和2、26左右两个部分<br/>
同理可以先将右半部份的2和26进行排序，<br/>
已知8和2，26这左右两个部分已经知道顺序了，<br/>
那么我们就可以用手里的办法，把这两小部分进行排序,<br/>
然后再往外推理，将五个同学进行排序，<br/>
具体的代码演示如下
```
let mergeSort=arr=>{
  let k=arr.length
  if(k===1){return arr}
  let left=arr.slice(0,Math.floor(k/2))
  let right=arr.slice(Math.floor(k/2))
  return merge(mergeSort(left),mergeSort(right))
}
let merge=(a,b)=>{
  if(a.length===0) return b
  if(b.length===0) return a
  return a[0]>b[0]?[b[0]].concat(merge(a,b.slice(1))):[a[0]].concat(merge(a.slice(1),b))
}
```
## 计数排序
现在我要将手中打乱的扑克牌进行排序，一般想到的方法是，一张一张看，新出的牌放在桌子上，和桌子上重复的牌就累在已有的牌上面，<br/>
整个操作下来之后，就可以在桌子上看见每种牌都有四张的一个情况，<br/>
然后再按照大小顺序，将牌收起来，这就叫做计数排序，<br/>
放到编程中的思路就是，<br/>
我将手上打乱顺序的数组12，14，8，2，2，26进行排序，<br/>
首先需要一个哈希表做记录，<br/>
每当发现一个新的数字N，就将它记作N：1，表示N出现了一次（比如例子中2出现两次，就记作N：2）<br/>
记录完之后我们知道了数组每个数出现与否或几次以及这个数组的最大值，然后开始从小到大循环遍历哈希表，<br/>
如果过程中发现哈希表中有这个数字，就打印出来，<br/>
这样就可以得到一串排好序的数组，<br/>
具体代码演示如下
```
let mergeSort=arr=>{
  let k=arr.length
  if(k===1){return arr}
  let left=arr.slice(0,Math.floor(k/2))
  let right=arr.slice(Math.floor(k/2))
  return merge(mergeSort(left),mergeSort(right))
}
let merge=(a,b)=>{
  if(a.length===0) return b
  if(b.length===0) return a
  return a[0]>b[0]?[b[0]].concat(merge(a,b.slice(1))):[a[0]].concat(merge(a.slice(1),b))
}
```

