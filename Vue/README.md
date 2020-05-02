### 1 - 前端框架的作用

组件化: 高度的组件化可以是我们的工程易于维护、易于组合拓展。

天然分层: JQuery 时代的代码大部分情况下是面条代码,耦合严重,现代框架不管是 MVC、MVP还是MVVM 模式都能帮助我们进行分层，代码解耦更易于读写。

生态: 现在主流前端框架都自带生态,不管是数据流管理架构还是 UI 库都有成熟的解决方案。

UI 与状态同步问题

\1. Webpack打包流程

a)   初始化参数：合并配置文件和shell语句中的参数

b)   开始编译：使用参数初始化Compiler对象，加载所有配置的插件

c)   确认入口：根据配置中的entry找到所有入口文件

d)   编译模块：从入口文件出发，调用loader对模块进行翻译，找出模块的依赖，递归处理。

e)   输出资源：根据入口和模块之间的依赖关系，组装成包含多个模块的chunk，将chunk转换为文件输出。

\2. Webpack HMR原理

https://zhuanlan.zhihu.com/p/30669007

\3. Webpack提供哪些功能

\4. Webpack loader作用, 构建过程，输出什么

\5. Webpack loader和Webpack plugin的区别

\6. Webpack配置

\7. Webpack去打包一个js文件的时候，打包出来的js发现太大了，这样加载时间太长，导致白屏时间过长，有什么解决方式

安装compression-webpack-plugin插件。前端将文件打包成.gz文件，然后通过nginx的配置，让浏览器直接解析.gz文件，可以大大提升文件加载的速度。

\8. CSS-loader是做什么的？假如写了一段CSS，最终是如何在浏览器上渲染的？

\9.  

10.浏览器同源策略

浏览器会限制一个[origin](https://developer.mozilla.org/zh-CN/docs/Glossary/源)的文档或者它加载的脚本与另一个源的资源进行交互。这能帮助阻隔恶意文档，减少可能被攻击的媒介

同源的定义：协议、端口和主机相同，路径可以不同

11.解决跨域问题的方案和实现原理

a) 通过jsonp跨域

b) 跨域资源共享（CORS）

c) nginx代理跨域

d) nodejs中间件代理跨域

e) WebSocket协议跨域

12.CORS跨域不能传递 cookies怎么办

返回Access-Control-Allow-Credentials: true

response.setHeader("Access-Control-Allow-Origin", request.getHeader("Origin"));

13.CORS简单请求，复杂请求

请求首部字段 [Origin](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Origin) 表明该请求来源，响应中携带了响应首部字段 Access-Control-Allow-Origin，服务端返回的 Access-Control-Allow-Origin: * 表明，该资源可以被任意外域访问

14.JSONP的原理

HTML的<script>标签请求的资源不受浏览器同远策略限制，可以在script中请求跨域资源，通过回调函数获取响应内容。

15.JSON Web Token原理

https://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html

16.什么是Cookie，什么是Session

Cookie：一小段的文本信息。客户端请求服务器，若服务器需要记录用户状态，则在响应中向客户端浏览器颁发一个Cookie。浏览器会保存Cookie。当浏览器再次请求该网站时，浏览器把请求的网址连同该Cookie一同提交给服务器。服务器检查该Cookie，以此来辨认用户状态。服务器还可以根据需要修改Cookie的内容。

maxAge：Cookie失效的时间，单位秒。如果为正数，则该Cookie在maxAge秒之后失效。如果为负数，该Cookie为临时Cookie，关闭浏览器即失效，浏览器也不会以任何形式保存该Cookie。如果为0，表示删除该Cookie。默认为–1

https://www.cnblogs.com/shoshana-kong/p/10669900.html

 

17.Cookie和Session区别

a)   cookie保存在客户端，session保存在服务器端

b)   cookie目的可以跟踪会话，也可以保存用户信息。session用来跟踪会话

 

18.回流与重绘

回流：当render tree中的一部分或全部因为元素的规模尺寸、布局、隐藏等改变时，浏览器重新渲染部分DOM或全部DOM的过程。回流也被称为重排，其实从字面上来看，重排更容易让人形象易懂（即重新排版整个页面）。

重绘：当页面元素样式改变不影响元素在文档流中的位置时（如background-color，border-color，visibility），浏览器只会将新样式赋予元素并进行重新绘制操作。

https://segmentfault.com/a/1190000018452924

19.如何减少回流和重绘

a)   在CSS中避免

b)   在JavaScript操作中避免

https://segmentfault.com/a/1190000018452924

20.为什么操作DOM慢

因为 DOM 是属于渲染引擎中的东西，而 JS 又是 JS 引擎中的东西。当我们通过 JS 操作 DOM 的时候，其实这个操作涉及到了两个线程之间的通信，那么势必会带来一些性能上的损耗。操作 DOM 次数一多，也就等同于一直在进行线程之间的通信，并且操作 DOM 可能还会带来重绘回流的情况，所以也就导致了性能上的问题。

https://blog.fundebug.com/2019/01/03/understand-browser-rendering/

21.从输入URL到渲染页面的过程

a)   DNS解析过程

b)   TCP连接

c)   https请求过程

d)   浏览器渲染过程

22.DNS解析过程

a)   浏览器检查本地hosts文件是否有该网址的映射关系，若有调用该映射完成解析

b)   若本地无该网址映射，客户端向本地DNS服务器发起查询，若本地DNS服务器存在该地址映射，则返回解析结果给客户端

c)   若本地DNS服务器不存在该地址映射，则向顶级服务器发起迭代查询或递归查询，直到解析完成

https://juejin.im/post/5b0a32a36fb9a07ab979f0b4

23.浏览器渲染步骤

a) 浏览器接收到 html 文档

b) 解析 html 文档生成 DOM对象模型，是一个树形结构。

c) 发起请求，获取 html 中的外部资源，比如图片，CSS文件，js文件等。

d) 获取CSS文件后，生成 CSS对象模型，也是一个树形结构。

e) 有了 DOM对象模型树和 CSS对象模型树，浏览器会生成渲染树（render tree）。

f) 有了渲染树，浏览器会执行一个叫做布局的操作（layout），用于计算页面上各个元素的几何位置。

g) 最终，浏览器会把“布局”好的页面元素绘制（paint）成我们最终看到的网页。

24.浏览器渲染过程

a)   解析HTML构建DOM树

b)   解析 CSS构建 CSSOM 树。

c)   将 DOM 与 CSSOM 合并成一个渲染树。

d)   根据渲染树排版布局，计算每个节点的几何信息。

e)   将各个节点绘制到屏幕上。

在解析html的过程中，html的解析会被中断，这是因为javascript会阻塞dom的解析。当解析过程中遇到<script>标签的时候，便会停止解析过程，转而去处理脚本，如果脚本是内联的，浏览器会先去执行这段内联的脚本，如果是外链的，那么先会去加载脚本，然后执行。在处理完脚本之后，浏览器便继续解析HTML文档。

同时javascript的执行会受到标签前面样式文件的影响。如果在标签前面有样式文件，需要样式文件加载并解析完毕后才执行脚本。这是因为javascript可以查询对象的样式。

https://juejin.im/entry/59e1d31f51882578c3411c77

25.<script>中defer和async的区别

a)   无 defer 和 async：浏览器停止解析文档，加载并执行脚本，脚本执行完，再继续解析文档

b)   async：在解析文档的同时，加载脚本，脚本加载完毕后，停止解析文档，执行脚本，脚本执行完，再继续解析文档。（脚本不按顺序执行，谁先加载完谁先执行）

c)   defer：在解析文档的同时，加载脚本。待文档解析完后，执行脚本。（脚本按顺序执行）

26.DOMContentLoaded与load的区别

DOMContentLoaded：初始的 HTML 文档被完全加载和解析完成之后，DOMContentLoaded 事件被触发，而无需等待样式表、图像和子框架的完成加载

load: 当一个资源及其依赖资源已完成加载时，将触发load事件

https://www.cnblogs.com/caizhenbo/p/6679478.html ！！！

27.浏览器是单线程还是多线程

a)   Javascript引擎是单线程的

b)   浏览器是多线程的

https://blog.csdn.net/It_rod/article/details/79880745

28.浏览器渲染Render（浏览器内核）进程中有哪些线程

a)   GUI渲染线程

b)   JS引擎线程

c)   异步http请求线程

https://blog.csdn.net/It_rod/article/details/79880745

29.浏览器什么时候加载图片

https://segmentfault.com/a/1190000010032501

https://juejin.im/post/5d3700ff6fb9a07ea648b41f

30.浏览器Web Worker

31.XSS

32.CSRF

33.中间人攻击

34.那在一个页面中还有什么提升页面性能的方式呢

a)   路由组件懒加载

b)   常用库CDN引入

35.图片懒加载，怎么实现 

36.各种地图框架的性能优化

37.git：pull和fetch区别  tag branch 区别

38.git常用的命令 

39.当git merge发生冲突的时候怎么做 