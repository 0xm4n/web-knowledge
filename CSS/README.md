1. ### 盒模型

   `IE`盒子模型（box-sizing: border-box;）、`W3C`盒子模型（box-sizing: content-box; ）；

   - 盒模型： 内容(content)、填充(`padding`)、边界(`margin`)、 边框(`border`)；
   - 区 别： `IE`的`content`部分把 `border` 和 `padding`计算了进去;

2. ### 外边距重叠

   概念：外边距重叠是指两个或多个盒子(可能相邻也可能嵌套)的相邻边界(其间没有任何非空内容、补白、边框)重合在一起而形成一个单一边界。

   合并规则：

   a)   全部都为正值，取最大者；

   b)   不全是正值，则都取绝对值，然后用正值的最大值减去绝对值的最大值；

   c)   没有正值，则都取绝对值，然后用0减去最大值。

3. ### BFC 及其应用

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

4. ### `display`有哪些值？说明他们的作用

   - `block` 转换成块状元素。
   - `inline` 转换成行内元素。
   - `none` 设置元素不可见。
   - `inline-block` 像一样显示，但其内容象块类型元素一样显示。
   - `list-item` 像块类型元素一样显示，并添加样式列表标记。
   - `table` 此元素会作为块级表格来显示
   - `inherit` 规定应该从父元素继承 `display` 属性的值
   - <display-outside> = block [|](https://developer.mozilla.org/zh-CN/docs/CSS/Value_definition_syntax#Single_bar) inline / <display-inside> = flex / <display-legacy> = inline-block

5. ### `display: none;`与`visibility: hidden;`的区别

   - `display:none`;会让元素完全从渲染树中消失，渲染的时候不占据任何空间；`visibility: hidden`;不会让元素从渲染树消失，渲染师元素继续占据空间，只是内容不可见
   - `display: none`;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示`；visibility: hidden;`是继承属性，子孙节点消失由于继承了`hidden`，通过设置`visibility: visible;`可以让子孙节点显式
   - 修改常规流中元素的`display`通常会造成文档重排。修改`visibility`属性只会造成本元素的重绘。
   - 读屏器不会读取`display: none`;元素内容；会读取`visibility: hidden;`元素内容

6. ### float属性

   概念：浮动的框可以向左或向右移动，直到他的外边缘碰到包含框或另一个浮动框的边框为止。由于浮动框不在文档的普通流中，所以文档的普通流的块框表现得就像浮动框不存在一样。浮动的块框会漂浮在文档普通流的块框上

7. ### 清除浮动的几种方式，各自的优缺点

   - 父级`div`定义`height`
   - 结尾处加空`div`标签`clear:both`
   - 父级`div`定义伪元素`::after`和`zoom`
   - 父级`div`定义`overflow:hidden`
   - 父级`div`也浮动，需要定义宽度
   - 结尾处加`br`标签`clear:both`
   - 比较好的是第3种方式，好多网站都这么用

8. ### 行内元素float:left后是否变为块级元素？

   行内元素设置成浮动之后变得更加像是`inline-block`（行内块级元素，设置成这个属性的元素会同时拥有行内和块级的特性，最明显的不同是它的默认宽度不是`100%`），这时候给行内元素设置`padding-top`和`padding-bottom`或者`width`、`height`都是有效果的

9. ### position属性

   - `absolute`：生成绝对定位的元素，相对于 `static` 定位以外的第一个父元素进行定位
   - `fixed`：生成绝对定位的元素，相对于浏览器窗口进行定位
   - `relative`：生成相对定位的元素，相对于其正常位置进行定位
   - `static` 默认值。没有定位，元素出现在正常的流中
   - `inherit` 规定从父元素继承 `position` 属性的值

10. ### overflow属性

    Overflow 属性规定当内容溢出元素框时发生的事情。

    取值：visible(默认)、hidden、scroll、auto

11. ### CSS选择器优先级；

    - 选择器类型：通配选择器、类型选择器、类选择器、ID选择器、标签选择器、伪类选择器、伪元素选择器…
    - 考虑以下三个方面：1、重要程度 2、优先级 3、资源顺序
    - 一个选择器的优先级由四个部分相加 ，是个十百千 — 四位数的四个位数：
      - 千位：内联style的属性
      - 百位：ID选择器
      - 十位：类选择器、标签选择器、伪类选择器
      - 个位：类型选择器、伪元素选择器

12. ### CSS 组合选择符

    - 后代选择器(以空格分隔)
    - 子元素选择器(以大于号分隔）
    - 相邻兄弟选择器（以加号分隔）
    - 普通兄弟选择器（以破折号分隔）

13. ### ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用

    - 单冒号(`:`)用于`CSS3`伪类，双冒号(`::`)用于`CSS3`伪元素
    - 用于区分伪类和伪元素

14. ### 伪类和伪元素的区别

    - 伪类表状态
    - 伪元素是真的有元素
    - 前者单冒号，后者双冒号

15. ### CSS引入方式 (link,@import,<style>,style)

16. ### `link`与`@import`的区别

17. ### CSS合并方法

18. ### 浏览器渲染时如何处理link的css文件

19. ### 知道css有个content属性吗？有什么作用？有什么应用？

20. ### CSS的单位有哪些，你常用的有哪些；

21. ### px, em, rem 区别是什么？

22. ### 手写flex水平垂直居中

23. ### 手写flex三列布局中间自适应

24. ### flex是由那些属性组成的简写

25. ### 流体布局

26. ### 圣杯布局

27. ### 双飞翼布局

28. ### 自适应布局

29. ### 水平垂直居中

30. ### 垂直居中

31. ### 如何垂直居中一个浮动元素？

32. ### 水平居中

33. ### 左边宽度固定，右边自适应

34. ### css中可以让文字在垂直和水平方向上重叠的两个属性是什么？

35. ### 用CSS画三角形

36. ### CSS 3的transform，translate和transition之间的区别与作用

37. ### CSS3新特性

38. ### 什么是FOUC?如何避免

39. ### 为什么要初始化CSS样式?

40. ### 列出你所知道可以改变页面布局的属性

41. ### CSS在性能优化方面的实践

42. ### stylus/sass/less区别

43. ### Sass、LESS是什么？大家为什么要使用他们？

44. ### postcss的作用

45. ### rgba()和opacity的透明效果有什么不同？

46. ### 重绘和回流（重排）是什么，如何避免？

47. ### 说一说css3的animation

48. ### css sprite是什么,有什么优缺点













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

