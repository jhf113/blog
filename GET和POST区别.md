# GET和POST区别
POST和GET是HTTP请求的两种方式，都可实现将数据从浏览器向服务器发送带参数的请求。

HTTP请求底层协议都是TCP/IP，所以两者没有本质的区别。
**HTTP**
**HTTP是什么**
HTTP：超文本传输协议。所有的WWW文件都必须遵守这个标准。

HTTP向服务器发送请求是TCP连接。HTTP服务器收到请求后向客户端返回一个状态行 比如“HTTP/1.1 200 OK”和

**HTTP请求的组成**
HTTP由四部分组成：

请求行（request line）：用于说明请求类型、要访问的资源路径、HTTP版本号（GET /index.html HTTP/1.1）
请求头部（header）：用于说明服务器要使用的附加信息
一个空行
请求数据（body）：任意添加的数据
![Alt text](https://img2018.cnblogs.com/blog/1722442/201906/1722442-20190621184936778-1359458815.png)
```
GET /books/?sex=man&name=Professional HTTP/1.1
Host: www.wrox.com
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.7.6)
Gecko/20050225 Firefox/1.0.1
Connection: Keep-Alive
这里是空行

------------------------------------------------------------------------------

POST /index.html HTTP/1.1   请求方法 url 协议/版本号
Host: localhost  主机地址
User-Agent: Mozilla/5.0 (Windows NT 5.1; rv:10.0.2) Gecko/20100101 Firefox/10.0.2 发送请求的应用程序名称
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-cn,zh;q=0.5 通知服务端可以发送的语言
Accept-Encoding: gzip, deflate 通知服务端可以发送的数据压缩格式
Connection: keep-alive
Referer: <a target=_blank href="http://localhost/" style="color: rgb(51, 102, 153); text-decoration: none;">http://localhost/</a>
Content-Length：25
Content-Type：application/x-www-form-urlencoded
请求空行 标志着请求头结束，请求正文（请求体）的开始
username=aa&password=1234
```
对于get方式的请求，浏览器会把http header和data一并发送出去，服务器相应200（返回数据）。
而对于POST，浏览器想法送header，服务器相应100, continue ，浏览器在发送data，服务器相应200（返回数据）。
***区别***
* get参数通过url传递，post放在request body中
* get请求在url中传递的参数是长度有限的，而post没有
* get比post更不安全，因为参数是直接暴露在url中，所以不能用来传递敏感信息。
* get请求只能进行url编码，而post支持多种编码方式
* get请求参数会被完成整的保留在浏览器记录里，而post中的参数不会被保留
* get和post本质上就是TCP连接，并无差别，但是由于HTTP的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同
* get产生一个TCP数据包，post产生两个TCP数据包

**post为什么会发送两个请求？**
post请求可以分为请求头和请求体两个部分，如果服务器先收到请求头，则会对其进行校验，如果校验通过，则回复客户端“100-Continue”，客户端再把请求体发给服务器。如果请求被拒了，服务器就会回复400之类的错误，这个交互就终止了。
