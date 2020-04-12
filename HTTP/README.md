### 1.1 - HTTP协议的基本概念

  HTTP是客户端和服务端之间请求和应答的标准，通常使用TCP协议。通常，由HTTP客户端发起一个请求，创建一个到服务器指定端口的TCP连接。HTTP服务器则在那个端口监听客户端的请求。一旦收到请求，服务器会向客户端返回一个状态，比如"HTTP/1.1 200 OK"，以及返回的内容，如请求的文件、错误消息、或者其它信息。

### 1.2 - HTTP报文结构

#### 1.2.1 - 起始行 

请求方法 + 请求URL + HTTP协议及版本

#### 1.2.2 - 首部

Accpet：告诉服务端，客户端接受什么类型的响应
Cache-Control：对缓存进行控制
User-Agent：告诉服务器，客户端使用的操作系统、浏览器版本和名称
Accept-Encoding：告诉服务器能接受什么编码格式,包括字符编码,压缩形式
Host：指定要请求的资源所在的主机和端口

#### 1.2.3 - 主体

### 1.3 - HTTP请求方法

#### 1.3.1 - 常用请求方法

  - HTTP1.0 三种请求方法：GET, POST, HEAD
  - HTTP1.1 新增六种请求方法：PUT, DELETE, OPTIONS, PATCH, TRACE, CONNECT<br>
    GET: 	请求一个指定资源。<br>
    HEAD: 与GET方法相同，但服务器响应时不包含响应体，用于超链接的有效性，可用性。<br>
    POST: 将数据提交到指定的资源，通常导致在服务器上的状态变化。<br>
    PUT: 从客户端向服务器传送的数据取代指定的文档的内容<br>
    DELETE: 请求服务器删除指定的页面。<br>
    OPTIONS: 允许客户端查看服务器的性能。<br>

#### 1.3.2 - GET和POST的区别

  - 收藏：GET产生的URL地址可以被收藏，而POST不可以
  - 缓存：GET请求会被浏览器主动缓存，而POST不会，除非自动设置
  - 浏览器历史：GET请求参数会被完整的保留在浏览器历史里，而POST的参数不会被保留
  - 长度限制：GET请求在URL中传输参数有长度限制，而POST没有
  - 数据类型：对参数的数据类型，GET只接受ASCII字符，而POST没有限制
  - 安全性：POST比GET更安全，因为GET请求的参数直接暴露在URL上
  - 数据位置：GET参数通过URL传输，而POST参数放在request body中

#### 1.3.3 - 保存一个图片为什么用 POST 不用 GET？GET也可以发送 base64 

  GET传输参数有长度限制

### 1.4 - HTTP状态码

#### 1.4.1 - 常用状态码

| 分类 | 分类描述                                       |
| :--- | :--------------------------------------------- |
| 1**  | 信息，服务器收到请求，需要请求者继续执行操作   |
| 2**  | 成功，操作被成功接收并处理                     |
| 3**  | 重定向，需要进一步的操作以完成请求             |
| 4**  | 客户端错误，请求包含语法错误或无法完成请求     |
| 5**  | 服务器错误，服务器在处理请求的过程中发生了错误 |

| 状态码 | 状态码英文名称        | 中文描述                                                     |
| :----- | :-------------------- | :----------------------------------------------------------- |
| 100    | Continue              | 继续。客户端应继续其请求                                     |
|        |                       |                                                              |
| 200    | OK                    | 请求成功。一般用于GET与POST请求                              |
| 201    | Created               | 已创建。成功请求并创建了新的资源                             |
| 202    | Accepted              | 已接受。已经接受请求，但未处理完成                           |
| 204    | No Content            | 无内容。服务器成功处理，但未返回内容。在未更新网页的情况下，可确保浏览器继续显示当前文档 |
| 206    | Partial Content       | 部分内容。服务器成功处理了部分GET请求                        |
|        |                       |                                                              |
| 301    | Moved Permanently     | 永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替 |
| 302    | Found                 | 临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI |
| 304    | Not Modified          | 未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源 |
|        |                       |                                                              |
| 400    | Bad Request           | 客户端请求的语法错误，服务器无法理解                         |
| 401    | Unauthorized          | 请求要求用户的身份认证                                       |
| 403    | Forbidden             | 服务器理解请求客户端的请求，但是拒绝执行此请求               |
| 404    | Not Found             | 服务器无法根据客户端的请求找到资源（网页）。通过此代码，网站设计人员可设置"您所请求的资源无法找到"的个性页面 |
|        |                       |                                                              |
| 500    | Internal Server Error | 服务器内部错误，无法完成请求                                 |
| 502    | Bad Gateway           | 作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应 |
| 503    | Service Unavailable   | 由于超载或系统维护，服务器暂时的无法处理客户端的请求。延时的长度可包含在服务器的Retry-After头信息中 |
| 504    | Gateway Time-out      | 充当网关或代理的服务器，未及时从远端服务器获取请求           |

#### 1.4.2 - 状态码301和302的区别

301是永久重定向，搜索引擎在抓取新内容的同时也将旧的网址替换为重定向之后的网址。

302是临时重定向，搜索引擎会抓取新的内容而保留旧的网址。搜索引擎认为新的网址只是暂时的。(网址劫持问题)

#### 1.4.3 - 状态码200和304的区别

200表示请求成功，304表示未修改

当缓存命中，但新鲜度测试未通过时，缓存会与服务器进行再验证，若再验证通过则返回304. 其他情况无论是从缓存读取还是直接从服务器读取都返回200.



### 1.5 - HTTP常见请求首部字段



### 1.6 - HTTP缓存机制

#### 1.6.1 - HTTP缓存机制概念
<img src="https://github.com/zhenyit/web-knowledge/blob/master/1.HTTP/cache-control.jpg" width="600px" />


#### 1.6.2 - HTTP缓存字段有哪些

- Expires(HTTP 1.0): 指定绝对的过期日期
- Cache-Control(HTTP 1.1): max-age指定文档的最大使用期（以秒为单位）
- If-Modified-Since（配合服务器响应首部Last-Modified）: 如果从指定日期之后文档被修改过了，就执行请求的方法
- If-None-Match（配合服务器响应首部ETag）:实体标签是附加在文档上的任意标签。它们可能包含了文档的序列号或版本号，或者是文档内容的校验和其他指纹信息，如果实体标签被修改了，就执行新的请求。 

#### 1.6.3 - HTTP缓存的应用场景

- 减少数据传输
- 缓解网络瓶颈
- 降低对原始服务器的要求
- 降低距离时延

#### 1.6.5 - 浏览器如何判断的请求是否来自缓存？

- 使用Date首部。将响应中Date首部的值与当前时间进行比较，如果响应中的日期比较早，客户端通常就可有认为这是一条缓存的响应。
- 客户端也可以通过Age首部来检测缓存的响应，通过这个首部可以分辨出这条响应的使用期。
- 打开 Google Chrome，按 F12，出现调试界面，切换到 Network 页。看是否有from cache



### 1.7 - HTTP版本

### 1.7.1 - HTTP 0.9、1.0、1.1、2.0的区别
### 1.7.2 - HTTP1.1的优化技术
### 1.7.3 - HTTP2.0的优化技术、特性

### 1.7.4 - http/1.1长连接

  http/1.1支持长连接，和请求的流水线（Pipelining）处理，在一个 TCP 连接上可以传送多个 HTTP 请求和响应，减少了建立和关闭连接的消耗和延迟，在 HTTP1.1 中默认开启 Connection： keep-alive，一定程度上弥补了 HTTP1.0 每次请求都要创建连接的缺点。但是存在串行的文件传输和浏览器同域并行请求限制的缺点

### 1.7.5 - 如何理解HTTP2.0的多路复用

  http/2多路复用就是在同一个TCP连接中，同一时刻可以传输多个HTTP请求。HTTP2采用二进制格式传输，取代了HTTP1.x的文本格式，这里有两个概念，帧（frame）和流（stream）。帧代表着最小的数据单位，每个帧会标识出该帧属于哪个流，流也就是多个帧组成的数据流。
多路复用，就是在一个 TCP 连接中可以存在多条流。即可发送多个请求，对端可以通过帧中的标识知道属于哪个请求。从而避免 HTTP 旧版本中的队头阻塞问题，极大的提高传输性能。

### 1.7.6 - HTTP2.0头部压缩、压缩算法



### 1.8 - HTTPS

#### 1.8.1 - HTTPS的概念

  https经由http进行通信，在http应用层与TCP传输层之间建立SSL加密层。对传输数据进行加密，保证传输过程中的数据安全。此外能对网站服务器进行真实身份认证。

#### 1.8.2 - HTTPS传输过程

  客户端发起https请求，服务器返回证书，客户端验证证书合法性(浏览器的"证书管理器"，有"受信任的根证书颁发机构"列表。客户端会根据这张列表，查看解开数字证书的公钥是否在列表之内。)，如证书合法，则产生随机（对称）密钥，使用服务器的公钥对随机密钥进行加密，然后客户端(使用以上的非对称加密的方式)发送对称加密使用的密钥到服务器， 接着服务器和客户端通过对称加密算法采用协商密钥对信息以及信息摘要进行加密通信。

#### 1.8.3 - HTTPS的优点和缺点

  优点：
  - 防窃听：数据加密传输
  - 防篡改：信息加密后，如果执意篡改，客户端则无法解密。且无法通过数据完整性校验；
  - 防冒充：身份认证，降低被劫持的风险
  
  缺点：
  - 新协议增加延时
  - 加解密消耗较多的CPU资源

#### 1.8.4 - 浏览器如何判断证书可信未被篡改
  - 证书是不是可信机构颁布
  - 证书中的域名与实际域名是否一致
  - 证书是否已经过期
  - 证书返回的公钥能否正确解开返回证书中的数字签名

#### 1.8.5 - 非对称加密、对称加密 HTTPS采用什么加密算法