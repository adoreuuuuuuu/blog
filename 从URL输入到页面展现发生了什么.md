# 从URL输入到页面展现发生了什么
# 1. 在浏览器输入URL
- URL(全称：Uniform Resource Locator）：统一资源定位符，用于定位互联网上的资源，通俗的讲相当于我们在浏览器中输入的网页地址
- http、https、ftp、file协议
  - http协议（全称：Hyper Text Transfer Protocol）超文本传输协议,是用于从万维网（WWW:World Wide Web ）服务器传输超文本到本地浏览器的传送协议，http://jirengu.com/blog 就是http协议。
  - https协议相当于将http协议加密过的协议，因为http协议应用的是明码，在某些情况下需要对此进行加密，就产生了https协议， https://10.245.23.456:3000/users就是https协议。
  - file协议主要用于访问本地计算机中的文件，就如同在Windows资源治理器中打开文件一样。
  - ftp（全称：File Transfer Protocol）协议，文件传输协议，是用于在网络上进行文件传输的一套标准协议，使用客户服务器模式。
# 2. 域名解析
- 域名是什么 对于 http://jirengu.com:8080/blog,jirengu.com就是域名；
- IP地址是什么 每个处于互联网中的设备都有IP地址，形如192.168.10.1；

1）浏览器缓存： 当用户通过浏览器访问某域名时，浏览器首先会在自己的缓存中查找是否有该域名对应的IP地址（若曾经访问过该域名且没有清空缓存便存在）；
2）系统缓存：当浏览器缓存中无域名对应IP则会自动检查用户计算机系统Hosts文件DNS缓存是否有该域名对应IP；
3）路由器缓存：当浏览器及系统缓存中均无域名对应IP则进入路由器缓存中检查，以上三步均为客服端的DNS缓存；
4）ISP DNS缓存：当在用户客服端查找不到域名对应IP地址，则将进入ISP DNS缓存中进行查询。比如你用的是电信的网络，则会进入电信的DNS缓存服务器中进行查找；
5）如果都没有找到，则向根域名服务器查找域名对应 IP，根域名服务器把请求转发到下一级，直到找到 IP
#3. 服务器处理
- 服务器是一台安装系统的机器，常见的系统如Linux、windows server 2012等，系统里安装的处理请求的应用叫 Web server（web服务器）；
- 常见的 web服务器有 Apache、Nginx、IIS、Lighttpdweb；
- 服务器接收用户的Request 交给网站代码，或者接受请求反向代理到其他 web服务器；

![image.png](http://upload-images.jianshu.io/upload_images/4452453-d3d5f92aa0607db9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#4. 网站处理流程
- MVC 模型(model)-视图(view)-控制器(controller)
  - 视图（View）：用户界面
  - 控制器（Controller）：业务逻辑
  - 模型（Model）：数据保存

![image.png](http://upload-images.jianshu.io/upload_images/4452453-c27dccc748c07dc8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
1. 访问网站 /users，Rails（一种后台语言）匹配对应的路由找到/users；
2. 将/users交给自己的控制器； 
3. 从模型里面查找user.all(所有的用户）；
4. 模型到数据库里面去查找；
5. 查完之后将数据返还给控制器；
6. 控制器就得到了所有用户的数据，将这些数据交给视图，视图相当于一个模板，模板将这些数据组合成一个html;
7. 将组合好的html再返还给控制器；
8. 控制器将组合好的html发回给浏览器；
# 5. 浏览器处理
- HTML字符串被浏览器接受后被一句句读取解析
- 解析到link或者herf 标签后重新发送请求获取css
- 解析到 script标签后发送请求获取 js，并执行代码
- 解析到img 标签后发送请求获取图片资源
#6. 绘制网页
- 浏览器根据 HTML 和 CSS 计算得到渲染树，绘制到屏幕上
- js 会被执行
