1. ### HTML语义化的理解

   概念：语义化是指根据页面内容选择合适的标签，而不是单纯使用div+css，便于开发者阅读，同时让浏览器的爬虫和机器很好的解析。

   好处：有利于SEO，有助于爬虫抓取更多的有效信息，爬虫是依赖于标签来确定上下文和各个关键字的权重；语义化的HTML在没有CSS的情况下也能呈现较好的内容结构与代码结构；方便其他设备的解析；便于团队开发和维护

2. ### HTML5有哪些特性？哪些新标签？

   绘画：canvas

   媒介回放：video和audio

   存储：localStorage和sessionStorage（本地离线存储和临时存储）

   语义化元素：article, footer, header, nav, section

   新技术：websocket, webworker

3. ### HTML META标签

   可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。


   <meta charset=’utf-8′>    <!--声明文档使用的字符编码-->
   <meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>   <!--优先使用 IE 最新版本和 Chrome-->
   <meta name=”description” content=”不超过150个字符”/>       <!--页面描述-->
   <meta name=”keywords” content=””/>     <!-- 页面关键词-->
   <meta name=”author” content=”name, email@gmail.com”/>    <!--网页作者-->
   <meta name=”robots” content=”index,follow”/>      <!--搜索引擎抓取-->
   <meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no”> <!--为移动设备添加 viewport-->
   <meta http-equiv=”Cache-Control” content=”no-siteapp” />    <!--不让百度转码-->
   <meta http-equiv=”pragma” content=”no-cache”>
   <meta http-equiv=”cache-control” content=”no-cache”>
   <meta http-equiv=”expires” content=”0″>



4. ### `<img>`的`title`和`alt`有什么区别

   title:当鼠标滑动到元素上的时候显示

   alt`是`<img>的特有属性，是图片内容的等价描述，当图片无法加载时显示。可提图片高可访问性，除了纯装饰图片外都必须设置有意义的值，搜索引擎会重点分析。

5. ### `HTML5`的离线储存工作原理？

   离线存储概念：在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件

   原理：`HTML5`的离线存储是基于一个新建的`.appcache`文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像`cookie`一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示

6. ### 浏览器是怎么对`HTML5`的离线储存资源进行管理和加载的呢

   在线的情况下，浏览器发现`html`头部有`manifest`属性，它会请求`manifest`文件，如果是第一次访问`app`，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过`app`并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的`manifest`文件与旧的`manifest`文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。

   离线的情况下，浏览器就直接使用离线存储的资源。

7. ### iframe有那些缺点？

   - `iframe`会阻塞主页面的`Onload`事件
   - 搜索引擎的检索程序无法解读这种页面，不利于`SEO`
   - `iframe`和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载

8. ### Doctype作用? 

   `<!DOCTYPE>` 声明位于文档中的最前面，处于 `<html>` 标签之前。告知浏览器的解析器， 用什么文档类型 规范来解析这个文档

9. ### 严格模式与混杂模式如何区分？它们有何意义?

   - 严格模式的排版和 `JS` 运作模式是 以该浏览器支持的最高标准运行
   - 在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。 `DOCTYPE`不存在或格式不正确会导致文档以混杂模式呈现

10. ### 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？行内元素和块级元素有什么区别？

    - 行内元素有：`a b span img input select strong`
    - 块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4… p`
    - 空元素：`<br> <hr> <img> <input> <link> <meta>`
    - 行内元素不可以设置宽高，不独占一行，行内元素水平方向margin 和 padding有效，竖直方向无效；行内元素只包含数据和其他行内元素。
    - 块级元素可以设置宽高，独占一行，块级元素可以设置margin 和 padding；块级元素可包含行内元素和其他块级元素

11. ### HTML全局属性(global attribute)有哪些

    - `class`:为元素设置类标识
    - `data-*`: 为元素增加自定义属性
    - `draggable`: 设置元素是否可拖拽
    - `id`: 元素`id`，文档内唯一
    - `lang`: 元素内容的的语言
    - `style`: 行内`css`样式
    - `title`: 元素相关的建议信息

12. ### HTML5 为什么只需要写 <!DOCTYPE HTML>

    - `HTML5` 不基于 `SGML`，因此不需要对`DTD`进行引用，但是需要`doctype`来规范浏览器的行为
    - 而`HTML4.01`基于`SGML`,所以需要对`DTD`进行引用，才能告知浏览器文档所使用的文档类型

13. ### strong与em的异同？

    - `strong`:粗体强调标签，强调，表示内容的重要性
    - `em`:斜体强调标签，更强烈强调，表示内容的强调点

14. ### 简述一下src与href的区别

- `src`用于替换当前元素，href用于在当前文档和引用资源之间确立联系。
- `src`是`source`的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求`src`资源时会将其指向的资源下载并应用到文档内，例如`js`脚本，`img`图片和`frame`等元素

> <script src ="js.js"></script> 当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部

- `href`是`Hypertext Reference`的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加
- `<link href="common.css" rel="stylesheet"/>`那么浏览器会识别该文档为`css`文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用`link`方式来加载`css`，而不是使用`@import`方式

