# HTTP协议

标签： HTTP 协议

---

- [HTTP协议](#HTTP协议)
  - [协议特点](#协议特点)
  - [版本](#版本)
    - [HTTP 1.1 特点](#HTTP-11-特点)
    - [HTTP 2.0 特点 （规划中）](#HTTP-20-特点-规划中)
  - [报文结构](#报文结构)
  - [请求方法](#请求方法)
  - [状态码](#状态码)
    - [2xx系列](#2xx系列)
    - [3xx系列](#3xx系列)
    - [4xx系列](#4xx系列)
    - [5xx系列](#5xx系列)
  - [首部](#首部)
    - [分类](#分类)
      - [按在报文中出现的位置分类](#按在报文中出现的位置分类)
      - [按生存期分类](#按生存期分类)
      - [按功能分类](#按功能分类)
    - [数据协商](#数据协商)
      - [请求中相关首部](#请求中相关首部)
      - [实体中相关首部](#实体中相关首部)
    - [缓存](#缓存)
      - [强制缓存](#强制缓存)
      - [协商缓存](#协商缓存)
      - [三种刷新](#三种刷新)
    - [多部分对象集合](#多部分对象集合)
    - [范围请求](#范围请求)
    - [其他功能首部](#其他功能首部)
  - [XSS](#XSS)
    - [XSS分类](#XSS分类)
      - [存储型](#存储型)
      - [反射型](#反射型)
      - [DOM型](#DOM型)
    - [解决](#解决)
  - [CSRF](#CSRF)
    - [原理](#原理)
    - [解决方法](#解决方法)
      - [验证码](#验证码)
      - [Referer Check](#Referer-Check)
      - [Anti CSRF Token](#Anti-CSRF-Token)
  - [跨域](#跨域)
    - [同源策略](#同源策略)
      - [同源条件](#同源条件)
      - [限制范围](#限制范围)
      - [不受限制的例外](#不受限制的例外)
      - [解决方法](#解决方法-1)
        - [CORS解决方案](#CORS解决方案)
        - [JSONP](#JSONP)
        - [反向代理服务器](#反向代理服务器)
  - [HTTPS](#HTTPS)
    - [HTTP缺点](#HTTP缺点)
    - [HTTPS的解决方案](#HTTPS的解决方案)
      - [加密](#加密)
        - [加密分类](#加密分类)
        - [证书](#证书)
        - [通信流程](#通信流程)
      - [摘要](#摘要)
      - [HTTPS缺点](#HTTPS缺点)
  - [通信数据转发程序](#通信数据转发程序)
    - [代理](#代理)
    - [网关](#网关)
    - [隧道](#隧道)
  - [性能优化方面的应用](#性能优化方面的应用)

---

## 协议特点

- 请求响应模式
- 无状态
- cookie管理状态

## 版本

- HTTP 1.1————当前使用的版本
- HTTP 2.0————规划中的版本

### HTTP 1.1 特点

- 持久连接。建立起TCP连接后，只要没有一方要求主动断开连接，则一直保持连接状态。减少了重复连接、断开的开销。
- 管线化。持久连接使管线化称为可能，不用等待响应可直接发送下一个请求。

### HTTP 2.0 特点 （规划中）

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP2.0%E7%89%B9%E7%82%B9.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP2.0%E7%89%B9%E7%82%B9.png?raw=true)

## 报文结构

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP%E6%8A%A5%E6%96%87%E7%BB%93%E6%9E%84.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP%E6%8A%A5%E6%96%87%E7%BB%93%E6%9E%84.png?raw=true)

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP%E6%8A%A5%E6%96%87%E5%AE%9E%E4%BE%8B.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTP%E6%8A%A5%E6%96%87%E5%AE%9E%E4%BE%8B.png?raw=true)

## 请求方法

- GET————访问某资源，参数通过queryStrig传递，可以缓存
- POST————提交表单，restful中用于新增
- PUT————restful中用于修改
- DELETE————restful中用于删除
- OPTIONS————用于查询服务端支持的方法，在非一般请求中会用到。
- HEAD————同GET，只不过不会返回响应体，用于确认资源有效性与资源的更新时间
- TRACE————追踪路径，服务端返回客户端发送的请求原文，对比可以知道请求是否被篡改。有一个Max-Forwards字段用于确定经过哪个服务器时返回。
- connect————用于建立SSL或TLS层通信

## 状态码

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E7%8A%B6%E6%80%81%E7%A0%81%E5%A4%A7%E7%B1%BB.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E7%8A%B6%E6%80%81%E7%A0%81%E5%A4%A7%E7%B1%BB.png?raw=true)

### 2xx系列

- 200 OK————一切正常
- 204 No Content————不返回响应体，若返回204响应，浏览器不刷新。Asp.net EmptyResult返回的200
- 206 Partial Content————返回Content-Range指定范围的实体内容。用于响应客户端发起的范围请求，可用于断点续传。

### 3xx系列

- 301 Moved Permanently————永久重定向，搜索引擎会收录新地址，也会更新书签
- 302 Found————临时性重定向
- 303 See Other————同302，但Post会改为Get，301、302标准禁止改，但实际上都改为了Get
- 304 Not Modified————服务器资源未改变，客户端可直接使用缓存。此条**与重定向无关**
- 307 Temporary Redirect————同302，但不会将POST改为GET，所以body里传的数据也不会丢失

### 4xx系列

- 400 Bad Request————请求报文存在语法错误
- 401 Unauthorized————页面需要认证（BASIC认证、DIGEST认证），首部含WWW-Authenticate用于弹出对话框质询用户信息。
- 403 Forbidden————访问被拒绝，未获得文件系统的访问授权或客户端IP地址未授权
- 404 Not Found————找不到资源

### 5xx系列

- 500 Internal Server Error————服务器执行请求时出了Bug
- 503 Service Unavailable————服务器超负载或停机维护，无法处理请求，最好在首部加Retry After返回客户端。

## 首部

### 分类

#### 按在报文中出现的位置分类

- 通用首部字段
- 请求首部字段
- 响应首部字段
- 实体首部字段

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E9%80%9A%E7%94%A8%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E9%80%9A%E7%94%A8%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true)

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E8%AF%B7%E6%B1%82%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E8%AF%B7%E6%B1%82%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true)

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%93%8D%E5%BA%94%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%93%8D%E5%BA%94%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true)

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%AE%9E%E4%BD%93%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%AE%9E%E4%BD%93%E9%A6%96%E9%83%A8%E5%AD%97%E6%AE%B5.png?raw=true)

#### 按生存期分类

- 端到端首部（End-to-end Header）————此类别的首部会一直生存到最终接收目标
- 逐跳首部（Hop-by-hop Header）————此类别首部只对单次转发有效，通过代理服务器就不再转发了。

逐跳首部：

- Connection
- Keep-Alive
- Proxy-Authenticate
- Proxy-Authorization
- Trailer
- TE
- Transfer-Encoding
- Upgrade

出去以上8种外，全都是端到端首部

#### 按功能分类

- 数据协商
- 缓存
- ......

### 数据协商

数据协商机制是指客户端和服务器端就响应的资源内容进行交涉，然后提供给客户端最为适合的资源。

#### 请求中相关首部

- Accept————告知服务器用户代理能够处理的媒体类型（MIME类型）及优先级
- Accept-Charset————告知服务器用户代理支持的字符集和优先级
- Accept-Encoding————告知服务器用户代理支持的压缩编码编码及优先级，可以取值`gzip、compress、deflate、identity(不执行压缩)`
- Accept-Language————告知服务器用户代理能够处理的自然语言集

```http

Accept: text/html,application/xhtml+xml,application/xml;q=0.8 //未指定权重的默认为1
Accept-Charset: iso-8859-5, unicode-1-1;q=0.8
Accept-Encoding: gzip, deflate
Accept-Language: zh-cn,zh;q=0.7,en-us,en;q=0.3

```

#### 实体中相关首部

实体：实体主体（请求体/响应体） + 实体首部

- Content-Type————实体主体内数据的媒体类型
- Content-Encoding————实体部分的压缩编码
- Content-Language————实体主体使用的自然语言

```http

Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Content-Language: zh-CN

```

### 缓存

强制缓存优先级大于协商缓存。
强制缓存若判断缓存没过期则不会与服务端通信，直接返回200，size显示from disk cache。
协商缓存每次都要向服务器确认资源是否被更改，若更改则返回新的，没更改返回304,告诉客户端直接使用缓存。
强制缓存基于时间缓存，协商缓存基于文件是否改变缓存。
此缓存指浏览器端缓存或代理服务器缓存。

- Cache-Control:no-cache————不使用强制缓存（包括代理服务的缓存），为兼容http 1.1以下版本，一般加上`Pragma:no-cache`
- Cache-Control:no-store————完全不使用缓存
- Cache-Control:private————仅发起请求的浏览器可缓存
- Cache-Control:public————浏览器和代理服务器都可缓存

cache-control可组合多个属性，以逗号分隔。

#### 强制缓存

- Expires————http 1.0版本，指定一个过期**时刻**，但存在客户端和服务器端时间不同步的问题
- Cache-Control:max-age————http 1.1版本，指定有效**时长**，单位秒
- Cache-Control:max-stale————未指定参数时，即使指定了max-age过期了，依然可使用强制缓存，指定参数时，在max-stale内可用强制缓存
- Cache-Control:must-revalidate————必须到服务端验证有效性（Etag、Last-Modified）后才使用缓存,优先级高于max-stale

#### 协商缓存

- Last-Modified 和 If-Modified-Since————服务器每次返回响应带上Last-Modified，客户端下次请求同一资源，将其作为If-Modified-Sinces发送到服务端，服务端检测资源最后修改时间是否与之相同，相同则返回304，告诉浏览器直接使用缓存，否则返回新资源并带上最新的Last-Modified。存在资源未改变，但修改时间改变的缺点。
- Etag 和 If-None-Match————HTTP 1.1，优先级高于Last-Modified && If-Modified-Since,每次文件改变都会生成新的Etag,服务端响应会带上Etag，客户端下次请求同一资源用If-None-Match带上该值，与服务端对比，相同则返回304，不相同返回最新资源和最新Etag

#### 三种刷新

- 浏览器地址回车————若存在强制缓存且没过期，则直接使用
- F5————不适用强制缓存，使用协商缓存去服务端验证有效性
- ctrl+F5————删除本地的缓存后去服务端取最新的

### 多部分对象集合

场景：上传表单时，既有文本，也有一些文件附件。
![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%A4%9A%E9%83%A8%E5%88%86%E5%AF%B9%E8%B1%A1%E9%9B%86%E5%90%88.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%A4%9A%E9%83%A8%E5%88%86%E5%AF%B9%E8%B1%A1%E9%9B%86%E5%90%88.png?raw=true)

相关首部Content-Type

- multipart/form-data————请求时web表单上传
- multipart/byteranges————响应时返回多个范围的内容。

### 范围请求

- Range————获取部分资源的范围请求。用于断点续传
- Accept-Ranges————服务端是否可处理范围请求，是时指定其值为bytes，否时指定其值为none

- Content-Range————服务器返回资源的范围，用于响应范围请求。

### 其他功能首部

- Host————应用的域名，若应用部署在虚拟主机上，则必填。因为多个虚拟主机公用一个IP地址，不指出Host就无法区分发给哪个虚拟主机。
- Cookie————客户端携带Cookie信息
- Set-Cookie————服务器端设置Cookie信息,加HttpOnly属性可以使JavaScript脚本无法获得cookie
- Content-Diposition————服务器端指示客户端以何种形式展示返回的内容，值为attachment时表示以附件形式下载。
- Referer————从哪个页面链接过来，可以用来防盗链。在web服务器配置文件中判断referer头信息，若来自外站则重定向到一个提示图片
- User-Agent————浏览器用户代理名称，用于识别浏览器
- X-Requested-With:当值为XMLHttpRequest时，服务器端知道客户端是通过ajax请求过来的。

## XSS

全称：跨站脚本攻击（Cross Site Script）

定义：指攻击者通过**脚本注入**，在用户浏览网页时，控制用户浏览器的一种攻击。

注："跨站"是历史上这种攻击的演示案例是跨域的，但现今是否跨域都可以出现。

### XSS分类

- 持久型XSS
  - 存储型XSS
- 非持久型XSS
  - 反射式型XSS
  - DOM型XSS

持久型XSS一般攻击脚本持久化到了数据库，只要浏览就会触发。
非持久型XSS一般需要诱导受害者点击链接才会触发。

|类型|存储区|插入点|
|---|---|---|
|存储型 XSS|后端数据库|HTML|
|反射型 XSS|URL|HTML|
|DOM 型 XSS|后端数据库/前端存储/URL|前端 JavaScript|

存储区：攻击代码存放的位置。
插入点：攻击脚本插入的位置。

#### 存储型

存储型XSS会把攻击脚本存储在服务器端。常见于UGC（User Generated Content 用户原创内容）网站，如论坛发帖、商品评论、用户私信等。

#### 反射型

攻击脚本通过url或referer传递到服务器，然后返回到前端展示。与存储型的区别是需要诱导受害者点击url，且不会存储到数据库。

#### DOM型

跟反射性差不多，不过不用经过服务器，经过JavaScript直接回显到界面

### 解决

CSP————禁止外域的脚本执行，在元数据中加上 `Content-Security-Policy`或服务端响应头部加上 `Content-Security-Policy`
输入值检查————白名单只允许特定的标签出现。
输出值转义————一般vue、react自动提供了转义，除了v-html等直接显示HTML的命令。
HttpOnly————响应头部加上HttpOnly，使不能通过js操作cookie。

## CSRF

定义：跨站请求伪造（Cross-site request forgery），攻击者盗用你的身份，以你的名义进行某些非法操作。

### 原理

攻击过程：

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/CSRF.jpg?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/CSRF.jpg?raw=true)

基础支撑：同源策略限制不了表单提交的post请求，和img、script、iframe、link标签的get请求

实现条件：

1. 会话有效
2. 欺骗用户访问URL

### 解决方法

- 验证码
- Referer Check
- Token认证

#### 验证码

CSRF攻击的过程往往是在用户不知情的情况下构造网络请求。而验证码必须用户交互才能完成最终请求。因此可以有效遏制CSRF攻击。但其缺点是，每次请求都让用户填验证码，用户体验不好。

#### Referer Check

通过检测请求的Referer头部，确定请求是否来自允许的域，若来自非法域，则说明是一次CSRF攻击。缺点是处于隐私保护，请求中可能不含Referer头，另外当HTTPS跳转到HTTP时，也不含Referer。

#### Anti CSRF Token

CSRF需要攻击者构造出请求中的所有参数，当在参数加一个随机数时，攻击者就没法猜出来这个参数，也就没法伪造请求。

token需要同时放在表单和Session中。在提交请求时，服务器只需验证表单中的Token和用户Session中的Token是否一致，一致则是合法请求，不一致则是CSRF攻击。

## 跨域

### 同源策略

作用：限制从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的重要安全机制。

#### 同源条件

- 协议相同
- 域名相同
- 端口相同

#### 限制范围

- cookie、LocalStorage、IndexDB等浏览器存储
- DOM结构（IFrame里）
- AJAX请求

注意：对于跨域请求，浏览器发送请求到服务端发送响应都是通的，最后堵塞在了浏览器接收响应。同源策略**只限制了不同源的读，未限制不同源的写**

#### 不受限制的例外

- img、script、iframe、link等标签src发送get请求，还可以携带请求域的cookie
- 表单提交（不通过ajax提交），还可以携带请求域的cookie

因为以上原因，所以会存在CSRF。

#### 解决方法

- CORS
- JSONP
- 反向代理服务器（Nginx等）
- 后端程序接口代理

##### CORS解决方案

简单请求：
1.请求方法只能为GET、POST、HEAD。
2.请求头只能包含Accecpt、Accecpt-Language、Content-Language、Content-Language、Content-Type
3.若头部包含Content-Type，则只能为text/plain、multipart/form-data、application/x-www-form-urlencoded

非简单请求：不符合简单请求的就是非简单请求。

预检请求：在发送非简单请求前，会发送一个确认是否允许该请求的OPTIONS请求。
存在必要：大部分浏览器的同源限制时是在请求正常从服务器返回后，浏览器不解析，但服务端数据已更改。为避免这些不可预见的结果产生，所以需要一个预检请求提前确认所请求是否被允许。
非简单请求会在每次发送请求前会发送预检请求，设置Access-Control-Max-Age可避免每次都发送。

在响应头部加上以下这些就可以避免同源策略的限制

```http

Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Access-Control-Allow-Credentials: true

```

##### JSONP

原理：通过\<script>\<img>等标签的src发起的请求(GET)不会受到同源策略限制。
优点：可以兼容很老的浏览器。（一般现代浏览器都支持CORS）
缺点：只能发起GET请求。

##### 反向代理服务器

优点：
1.不用程序员编写代码，只用部署时配置一下。
2.调用的是第三方的接口时，无法在服务端配置CORS跨域

## HTTPS

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS.png?raw=true)

### HTTP缺点

- 明文传输，容易被监听
- 可能被篡改
- 容易假冒服务器

### HTTPS的解决方案

- 加密————解决监听问题
- 摘要————解决篡改问题
- 证书————解决身份假冒问题

#### 加密

##### 加密分类

- 对称加密————通信双方用同一把共享密钥加密解密，缺点是容易传输中被人截获
- 非对称加密————有公钥私钥两把钥匙，公钥公开给别人，私钥自己留着。当用公钥加密、私钥解密时用于加密；私钥加密，公钥解密时用于验证。
- 摘要（严格来说不属于加密）————常见的MD5用于获取数据的128位散列值，而根据散列值却很难推出原始数据。

HTTPS中加密采用非对称加密传输共享密钥给对方，之后用该共享密钥采用对称加密传输具体数据。因为非对称加密更耗时和资源。

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%B7%B7%E5%90%88%E5%8A%A0%E5%AF%86%E6%9C%BA%E5%88%B6.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%B7%B7%E5%90%88%E5%8A%A0%E5%AF%86%E6%9C%BA%E5%88%B6.png?raw=true)

##### 证书

上述流程中，如果服务器端发送的公钥在传送至客户端过程中**被篡改**，怎么保证**公钥的可信度**。
于是公钥证书出现了。证书是第三方权威的**数字证书认证机构**(CA Certificate Authority)颁发给服务器的，其携带两个信息，一个数字签名，一个服务器的公钥。数字签名是经证书认证机构私钥加密后的一段密文，而其公钥早已内置到浏览器（根证书中），若用这个内置公钥能够验证签名为真，则可以确信证书的可信度，从而确认服务器公钥的可信度.

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E5%85%AC%E9%92%A5%E8%AF%81%E4%B9%A6%E4%BD%9C%E7%94%A8%E6%B5%81%E7%A8%8B.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E5%85%AC%E9%92%A5%E8%AF%81%E4%B9%A6%E4%BD%9C%E7%94%A8%E6%B5%81%E7%A8%8B.png?raw=true)

##### 通信流程

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%B5%81%E7%A8%8B%E5%9B%BE.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%B5%81%E7%A8%8B%E5%9B%BE.png?raw=true)

证书同时解决了身份假冒问题,若需要验证客户端身份,客户端也需要安装证书,但向认证机构申请客户端证书需要收费,所以一般只有银行网站需要安装.

#### 摘要

应用层发送数据时会附加一种叫做MAC(Message Authentication Code)的报文摘要,用以检测报文的完整性,避免被篡改.

#### HTTPS缺点

- 速度慢
- 证书要花钱

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%AF%94HTTP%E6%85%A22%E5%88%B0100%E5%80%8D.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/HTTPS%E6%AF%94HTTP%E6%85%A22%E5%88%B0100%E5%80%8D.png?raw=true)

## 通信数据转发程序

### 代理

作用：

- 利用缓存技术，减少服务器负载
- 针对特定网站的访问控制
- 获取访问日志

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8.png?raw=true)

### 网关

一般用于协议转换。

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E7%BD%91%E5%85%B3.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E7%BD%91%E5%85%B3.png?raw=true)

### 隧道

使用加密技术使客户端与服务端安全通信。

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E9%9A%A7%E9%81%93.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E9%9A%A7%E9%81%93.png?raw=true)

## 性能优化方面的应用

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%89%8D%E7%AB%AF%E4%BC%98%E5%8C%96-%E9%9B%85%E8%99%8E%E5%86%9B%E8%A7%84.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%89%8D%E7%AB%AF%E4%BC%98%E5%8C%96-%E9%9B%85%E8%99%8E%E5%86%9B%E8%A7%84.png?raw=true)

[https://aotu.io/notes/2016/03/16/optimization/](https://aotu.io/notes/2016/03/16/optimization/)

- 减少HTTP请求，比如通过雪碧图减少图片资源请求次数。
- 缓存
- 压缩。最好压缩文本，音视频等格式压缩率低，还浪费cpu等资源。
- js放页面底部
- 图片懒加载
