# CSS知识总结
## 浏览器渲染原理
1. 浏览器渲染步骤
* 根据html构建html树(DOM)
* 根据css构建css树(CSSOM)
* 将两棵树合并成一颗渲染树(render tree)
* Layout布局(文档流、盒模型、计算大小和位置)
* paint绘制(把边框颜色、文字颜色、阴影等画出来)
* compose合成(根据层叠关系展示画面)
2. 三种更新方式
**第一种，全走** 
* ``div.remove``会触发当前消失，其他元素relayout
**第二种，跳过layout**
* 改变背景颜色，直接repaint+composite
**第三种，跳过layout和paint**
* 改变transform，只需composite
* 注意必须全屏查看效果
[所有属性的链接](https://csstriggers.com/)
## CSS 动画的两种做法（transition 和 animation）
1. transition过渡
* 作用（补充中间帧）
* 语法 transition:属性名 时长 过渡方式 延迟（可以用all表示所有属性）
**display:none=>block没法过渡，一般改成visibility:hidden=>visible
2. animation
* @keyframes语法
``@keyframes identifier{
    0%{
        top:0;left:0;
    }
    50%{
        top:50px;
    }
    100%{
        top:100px;left:100%;
    }
}``
* animation:时长 过渡方式(linear) 延迟 次数(infinite) 方向(alternate) 填充模式(forwards) 是否暂停(paused) 动画名
3. [把小心心放在这里吧](http://js.jirengu.com/muwoy/1/edit?html,css,output)
