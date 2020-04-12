### 1 -  盒模型

标准盒模型的width和height是指content的宽和高；



### 2 - 块级元素和行内元素

a) 块级元素的宽度占据父元素整个空间（独占一行），高度与内容相同；行内元素的高宽与内容高宽一样，不会独占一行，一行排不下，才会换行。

b) 块级元素可包含行内元素和其他块级元素；行内元素只包含数据和其他行内元素。

c) 块级元素可以设置 width, height属性；行内元素设置width, height无效;

d) 块级元素可以设置margin 和 padding；行内元素水平方向有效，竖直方向无效；



### 3 -  外边距重叠（margin合并问题 ）

概念：外边距重叠是指两个或多个盒子(可能相邻也可能嵌套)的相邻边界(其间没有任何非空内容、补白、边框)重合在一起而形成一个单一边界。

合并方式：

a)   全部都为正值，取最大者；

b)   不全是正值，则都取绝对值，然后用正值的最大值减去绝对值的最大值；

c)   没有正值，则都取绝对值，然后用0减去最大值。



### 4 -  BFC 及其应用

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



### 5 - Display属性

<display-outside> = block [|](https://developer.mozilla.org/zh-CN/docs/CSS/Value_definition_syntax#Single_bar) inline

<display-inside> = flex

<display-legacy> = inline-block



### 6 - Overflow属性

Overflow 属性规定当内容溢出元素框时发生的事情。

取值：visible(默认)、hidden、scroll、auto



### 7 - Position属性

static(默认)、absolute、relative、fixed

fixed：相对于浏览器窗口定位

absolute：相对于 <html> 元素或其最近的定位祖先定位



### 8 - CSS选择器的优先级

选择器类型：通配选择器、类型选择器、类选择器、ID选择器、标签选择器、伪类选择器、伪元素选择器…

CSS语言有规则来控制在发生碰撞时哪条规则将获胜

考虑以下三个方面：1、重要程度 2、优先级 3、资源顺序

一个选择器的优先级由四个部分相加 ，是个十百千 — 四位数的四个位数：

千位：style的属性

百位：ID选择器

十位：类选择器、标签选择器、伪类选择器

个位：类型选择器、伪元素选择器



### 9 - CSS的引入方式

内联方式、嵌入方式(<style>)、链接方式(link)、导入方式(@import)



### 10 - CSS单位

绝对长度单位：px、pt、in、cm

相对长度单位：em、rem、vh、vl、ch

百分比



### 11 - 手写flex垂直居中

``` css
div {

 display: flex;

 align-items: center;

 justify-content: space-around;

}
```



### 12 - 手写flex三列布局中间自适应



### 13 - flex属性是有哪些属性组成的简写

·   flex-grow：定义弹性盒子项（flex item）的拉伸因子

·    flex-shrink： 用于溢出容器的 flex 项。这指定了从每个 flex 项中取出多少溢出量，以阻止它们溢出它们的容器。 

·   flex-basis：指定了 flex 元素在主轴方向上的初始大小



### 14 - 双飞翼布局，圣杯布局写法思路



### 15 - 垂直水平居中的方法



### 16 - 垂直居中的方法

方法一：

``` css
#content {

   position: absolute;

   top: 50%;

   height: 240px;

   margin-top: -120px; /* negative half of the height */

}
```



方法二：

``` css
#content {

   display: inline-block;

   vertical-align: middle;

}
```

方法三：

父元素display: flex;子元素：align-self: center;

方法四：

``` css
#content {

   position: relative;

   top: 50%;

   transform: translate(-50%);

}
```

方法五：line-height = height

### 17 -水平居中的方法

行内元素：text-align:center

已知宽度块级元素：设置width，margin-left:auto;margin-right:auto;

未知宽度：display：inline-block; text-align:center;

多个块：父级元素display:flex; justify-content:center;



18 - CSS画三角形

``` css
# triangle {
    width: 0;
    height: 0;
    border: 50px solid transparent;
    border-bottom: 50px solid green;
}
```

