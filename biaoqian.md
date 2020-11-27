# html常用标签
## a 标签的用法
1. a标签的属性有：
* href(网址，路径，伪协议，id，mailto，tel)
* target(内置名称：_blank,_self,_top,_parent；程序员命名)
* download(不用了不靠谱)
* rel=noopener
## img 标签的用法
1. 属性
* alt(加载图片失败的时候设置一张图片显示)
* height
* width(单写一个，另一个会自动等比例缩放)
* src
2. 事件
* onload
* onerror(图片加载失败的时候可以挽救)
3. 响应式(让手机上也能适应)
* max-width:100% 
## table 
1. 这是一段table标签的代码示例
```
<table>
   <thead>
    <th></th>
   </thead>
   <tbody>
    <tr>
      <td></td>
    </tr>
   </tbody>
   <tfoot>
   </tfoot>
</table>
```
2. 相关样式
* table-layout(auto是让表格更加个性化，fixed是让表格尽量等距离)
* border-collapse(合并单元格间隙)
* border-spacing(设置单元格间隙大小)
## 其他感想
今天还学习了input标签和form标签，比如input要加name表示同一个组，还有autocomplete可以建议用户要填充表单的内容，知道了input标签内不会放另外的标签，button标签内可以有任何标签，老师还提了一点别的标签，说以后学JS的时候会细讲。
