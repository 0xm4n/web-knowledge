\1. 盒模型

标准盒模型的width和height是指content的宽和高；



\2. 块级元素和行内元素

块级元素：宽度占据父元素整个空间（独占一行），高度与内容相同。

行内元素：高宽与内容高宽一样，不会独占一行，一行排不下，才会换行

区别：

a)   块级元素可包含行内元素和其他块级元素。行内元素只包含数据和其他行内元素。

b)   块级元素可以设置 width, height属性；行内元素设置width, height无效;

c)   块级元素可以设置margin 和 padding；行内元素水平方向有效，竖直方向无效；

\3. Display属性

<display-outside> = block [|](https://developer.mozilla.org/zh-CN/docs/CSS/Value_definition_syntax#Single_bar) inline

<display-inside> = flex

<display-legacy> = inline-block

\4. 外边距重叠（margin合并问题 ）

概念：外边距重叠是指两个或多个盒子(可能相邻也可能嵌套)的相邻边界(其间没有任何非空内容、补白、边框)重合在一起而形成一个单一边界。

合并方式：

a)   全部都为正值，取最大者；

b)   不全是正值，则都取绝对值，然后用正值的最大值减去绝对值的最大值；

c)   没有正值，则都取绝对值，然后用0减去最大值。

https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing

\5. BFC 及其应用

概念：BFC 就是块级格式上下文，是页面盒模型布局中的一种 CSS 渲染模式，相当于一个独立的容器，里面的元素和外部的元素相互不影响。

触发方法：

a)   body 根元素

b)   浮动元素：float 除 none 以外的值

c)   绝对定位元素：position (absolute、fixed)

d)   display 为 inline-block、table-cells、flex

e)   overflow 除了 visible 以外的值 (hidden、auto、scroll)

应用：

a)   解决外边距重叠问题

b)   清除浮动

https://zhuanlan.zhihu.com/p/25321647

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/59

https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context

\6. 浮动float

https://segmentfault.com/a/1190000016153055

\7. CSS选择器优先级（权重）；

选择器类型：通配选择器、类型选择器、类选择器、ID选择器、标签选择器、伪类选择器、伪元素选择器…

CSS语言有规则来控制在发生碰撞时哪条规则将获胜

考虑以下三个方面：1、重要程度 2、优先级 3、资源顺序

一个选择器的优先级由四个部分相加 ，是个十百千 — 四位数的四个位数：

千位：style的属性

百位：ID选择器

十位：类选择器、标签选择器、伪类选择器

个位：类型选择器、伪元素选择器