---
title: http
date: 2017-02-20 18:52:24
tags: 
    - http 
commit: false 
categories: http 
---

### DNS

* 浏览器中的URL通过DNS解析成IP
* DNS 服务器是集群是分层级的，没有任何一个单一的 DNS 服务器是中包含所有服务器
* 如果一个服务器没着到，会沿着节点一层一层往上找
* 每一个请求都是独立的无状态的

### URL

* 由三部分组成
* HTTP 协议
* www

<!--more-->

### 媒体类型（MIME type）

* 因特网上有数千种不同的数据类型，HTTP 仔细地给每种要通过 Web 传输的对
象都打上了名为 MIME 类型
* content-type =
* text\/html
* text\/plain
* image\/jpg

### URI 为统一资源标识符

* 每个 Web 服务器资源都有一个名字URI

* url 统一资源定位符: [https:\/\/static.jdpay.com\/m-wallet\/v0.4.0\/img\/favicon.ico](https://static.jdpay.com/m-wallet/v0.4.0/img/favicon.ico)

* 协议 \(scheme\) https:\/\/ \|\| https:\/\/
* 网址 static.jdpay.com
* 资源路径 \/m-wallet\/v0.4.0\/img\/favicon.ico

* urn 统一资源名 与资源地无关

* 如： 不论因特网标准文档 RFC 2141 位于何处
* 都可以用 URN 来命名它： urn:ietf:rfc:2141

### 事物

* 一个http事物由一条客户端发起的请求命令和一个服务端返回响应结果构成
* 这种通信是通过HTTP报文的格式数据进行的

### 方法

* GET 从服务器向客户端发送命名资源

* POST 将客户端数据发送到一个服务器网关应用程序

* OPTIONS 查询针对请求URI指定的资源支持的方法。

* DELETE 从服务器中删除命名资源
* PUT 将来自客户端的数据存储到一个命名的服务器资源中去
* HEAD 仅发送命名资源响应中的 HTTP 首部
* CONNECT 方法要求在代理服务器通信时建立隧道，实现隧道协议进行TCP通信。
* TRACE 方法是让WEB服务器端将之前的请求通信环回给客户端的方法。

### 状态码

* 1XX 信息状态码 接受的请求正在处理

* 2XX 成功状态吗 请求正常处理完毕

* 3XX 重定向状态码 需要进行附加操作以完成请求

* 4XX 客户端错误状态码 服务器无法处理请求
* 5XX 服务器错误状态码 服务器处理请求出错

### 报文

* 起始行 HTTP\/1.1 200 OK

* 首部字段

* Server: nginx
* Connection: keep-alive
* ...

* 主体

* 发送的数据
* 返回的数据
### 链接

* TCP\/IP 传输协议
* 无差错的数据传输
* 按序传输
* 未分段的数据流
* 版本
* HTTP\/0.9 有缺陷不支持多媒体的 MIME 类型，各种 HTTP 首部
* HTTP\/1.0 广泛使用
* HTTP\/1.1 当前使用
* HTTP\/2.0\| HTTP-NG 优化性能

* ip 网络层 -&gt; TCP 传输层 -&gt; HTTP应用层
* 一次url请求

* 浏览器从url中解析出服务器的主机名称
* 浏览器将服务器的主机名称转换成服务器ip

* 通过 DNS

* 解析出端口

* 浏览器建立与 web 服务器的 TCP 链接

* 浏览器向服务器发送一条 http 请求报文

* 服务器返回给浏览器一条 HTTP 响应报文
* 关闭链接，浏览器显示文档

### WEB 的结构组件

```
- 代理
- 位于客户端和服务端中间
- 对请求和响应进行过滤等操作
- 缓存
- HTTP 仓库 使常用副本保存在离客户端更近的地方
- 网关
- 链接其他服务器的特殊 WEB 服务器
- HTTP <-(http)-> HTTP/FTP 网关 <-(FTP)-> FTP 服务器
- 隧道
- 对 HTTP 通信报文进行盲转发的特殊代理。
- Agent 代理
- 发起自动 HTTP 请求的半智能 Web 客户端。
```

### HTTP REQUEST

* 由3部分组成： 请求行 请求报头 请求正文

* 请求行 Method Request-URI HTTP-Version

* POST /loan/record HTTP/1.1
* Method : GET POST HEAD PUT DELETE TRACE OPTIONS
* HEAD 请求获取由Request-URI所标识的资源的响应消息报头
* RTACE 请求服务器回送收到的请求信息，主要用于测试或诊断
* OPTIONS 请求查询服务器的性能，或者查询与资源相关的选项和需求

* 请求报头

* 请求正文

### HTTP RESPONSE

* 由3部分组成：状态行 消息报头 响应正文

* 请求行 HTTP-Version Status-code 描述
* HTTP/1.1 200 ok
* Status-code

* 1XX 信息状态码 接受的请求正在处理
* 2XX 成功状态吗 请求正常处理完毕
* 3XX 重定向状态码 需要进行附加操作以完成请求
* 4XX 客户端错误状态码 服务器无法处理请求
* 5XX 服务器错误状态码 服务器处理请求出错

* 200 OK：请求正常处理。

* 204 No Content：请求正常处理，但没有资源可返回。
* 206 Partial Content： 客户端进行了范围请求，服务器成功执行这部分GET请求。
* 301 Moved Permanently： 永久性重定向，表明该资源已被分配了新的URI。
* 302 Found： 临时性重定向，表明该资源暂时被分配了新的URI。
* 303 See Other：表明请求的资源存在另一个URI，明确要求客户端采用GET方法重定向请求资源。
* 304 Not Modified : 未改变，使用缓存
* 400 Bad Request：请求报文中存在语法错误，需修改请求内容后再次发送。
* 401 Unauthorized\*：请求需包含通过HTTP认证（BASIC认证、DIGEST认证等）的认证信息，浏览器初次接收401响应会弹出认证窗口。若之前已进行过一次请求，则表示用户认证失败。
* 403 Forbidden：请求资源的访问被服务器拒绝。服务器端没有必要给出拒绝的详细理由，不过也可以在响应主体部分对原因进行描述。未获得文件系统的访问授权（比如在IIS上部署网站时默认不能通过浏览器访问文件）、访问权限出现问题（比如从未授权的发送源IP地址试图访问）都有可能返回403响应。
* 404 Not Found：服务器无法找到请求的资源（也可在服务器端拒绝访问且不想说明理由时使用）。
* 500 Internal Server Error：服务器端执行请求时发生内部错误。多为服务器端程序出现Bug。
* 503 Service Unavailable：服务器处于超负载或正在停机维护，暂时无法处理请求。

* 消息报头 请求头

{% asset_img img1.png request header %}

* 通用header

* Content-Type : 请求体/响应体的类型，如：text/plain、application/json
* Accept : 说明接收的类型，可以多个值，用,\(半角逗号\)分开
* Content-Length : 请求体/响应体的长度，单位字节
* Content-Encoding : 请求体/响应体的编码格式，如gzip, deflate
* Accept-Encoding : 告知对方我接受的Content-Encoding
* ETag : 当前资源的标识，和Last-modified, If-None-Match, if-Modified-since 配合，用于控制缓存
* Cache-Control : 取值一般维 no-cache 或者 max-age=xx, xx为整数，表示该资源缓存有效期（秒）
* Connection : keep-alive 服务端和客户端的TCP不会关闭!

* 请求Header

* Authorization: 用于设置身份认证信息
* User-Agent : 用户标识如 OS浏览器的类型和版本
* If-Modified-since : 值为上一次Last-Modified的被值，用于确认摸个资源是否被更改过，没有更改就从缓存中取。
* Cookie : 已有的cookie
* Referer : 页面地址上一次个路由， 来源
* Host : 请求主机的端口

* 响应的header
* Data: 服务器的日期
* Last-Modified : 资源最后呗修改的时间
* Transfer-Encoding : 取值为一般为chunked，出现在Content-Length不能确定的情况下，表示服务器不知道响应版体的数据大小，一般同时还会出现Content-Encoding响应头
* Set-cookie : 设置cookie
* Location : 重定向到另一个URL，如输入浏览器就输入baidu.com回车，会自动跳到 [https://www.baidu.com](https://www.baidu.com) ，就是通过这个响应头控制的
* Server : 后台服务器


