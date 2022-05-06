# Cookie和Sessio
**Cookie：**
HTTP Cookie(也叫Web Cookie或者浏览器Cookie)是服务器发送到用户浏览器并且保存到本地的一小块数据，他会在浏览器下次向同一个服务器发起请求的时候被携带并发送到服务器上，通常，它用于告知服务端两个请求是否来自同一个浏览器，如保持用户的登录状态，Cookie使基于无状态的HTTP协议记录稳定的状态信息成为可能。
Cookie主要用于一下三个方面：
	• 会话状态管理（如用户登录状态，购物车，游戏分数或其他需要记录的信息)
	• 个性化设置（如自定义设置，主题）
	• 浏览器行为跟踪器（如分析用户行为）
	
**Session:**
Session代表着服务器和客户端一次会话的过程。Session对象存储特定用户会话所需要的属性及配置信息，这样，当用户在应用程序的Web页之间跳转时，存储在Session对象中的变量将不会丢失，而是在整个用户会话一直存在下去。当客户端会话关闭，或者Session超时失效时对话结束。

**（2）Cookie和Session保持登录**
用户第一次请求服务器的时候，服务器会根据用户提交的信息，创建一个相应的Session，请求返回是将此Session的唯一标识信息SessionID返回给浏览器，浏览器接受到服务器返回的SessionID信息后，会将此信息存入到Cookie中，同时Cookie记录SessionID属于哪个域名。
当用户第二次访问服务器的时候，请求会自动判断此域名下是否存在Cookie信息，如果存在自动将Cookie信息也发送到服务端，服务端会从Cookie中获取SessionID，在根据SessionID查找到对应的Session信息，如果没有找到说明用户没用登录过或者登录失效，如果找到Session说明用户已经登录可以执行后面操作
更具以上流程可以知道，SessionID是链接Cookie和Session的一道桥梁，大部分系统也是根据此原理来验证用户登录状态。
![Alt text](https://wx4.sinaimg.cn/mw2000/008sKdQply1h1xw95w1zjj30un0eltea.jpg)
