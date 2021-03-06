### 深入分析Java Web技术内幕读书笔记
 * 第一章：深入介绍web请求过程
   > 首先B/S架构的服务推动了互联网的发展，逐渐代替了以前的C/S架构的服务
   - 优点体现于
     * 1.浏览器的操作简单；
     * 2.基于http请求，已经开发有许多的服务器为基础，所以只需要注重逻辑代码的编写；
     * http请求是**无状态的短连接**通信方式，不能一直保持这个链接的处于活的状态，是为了保证请求的快速响应；
   - 输入URL地址->请求DNS域名转为Ip地址->定位到具体的服务器(负载均衡)->资源（可能来自于CDN）与数据（可能来自于数据库）的请求;
     * 如何发起一个http请求 其本质是一个socket连接，同时可以使用httpclient与Linux中的curl模拟请求的发起
   - 熟悉常见的http请求头和响应头
     * 请求头  Accept-charset,Accept-encoding,Accept-language,Host,user-Agent,connection
     * 响应头  Server content-type  content-language,content-encoding content-length,keep-alive
   - 常见的http状态码 
     * 200 成功 300 重定向  400 请求不存在 500 服务器内部错误
   - 浏览器的缓存机制
     * 浏览器中Ctrl+F5可以请求无缓存的数据，，这个是因为在这种操作的请求头中添加了2个参数，Pragm:no-cache,Control:no-cache
   - DNS域名解析过程
     * 1.查看缓存中是否已有解析过的缓存，有的话则使用之前以及解析过的；
     * 2.查找操作系统缓存中是否有这个域名，windows(C:\Windows\System32\drivers\etc\host)和Linux（etc/name.conf）配置文件中
     * 3.获取域名服务器,一把是有失效时间的，就近获取，公司的或者是学校 LDNS
     * 4.如果3没有命中，那么到RootServer域名解析器
     * 5.根域名服务器会返回给本地域名服务器地址
     * 6.本地域名服务器向gTLD服务器发送请求
     * 7.gTLD域名服务器查找并返回
     * 8.得到目标IP记录，以及TTL
     * 9.返回域名对应的IP与TTL
     * 10.解析结果返回给用户，并缓存TTL在本地
   - 清除缓存的域名
     * 1.域名解析的结果会缓存在1.localDNS 2.用户本地机器 二者的有效时间由TTL控制，其中本地的缓存是可以清除的
     * 2.windows下ipconfig/flushdns , linux下/etc/init.d/nscd restart  来清除缓存
   - CDN工作机制
     * 1.解释：内容分布网络，是一种流量分配网络，使用户在就近的CDN节点获取所需，提高网络的响应速度
     * 2.主要缓存网站中的静态资源数据为主，如CSS，HTML
   - 负载均衡
     * 1.解释：对任务分摊到多个操作单元上执行，提高服务器的响应速度
     * 2.分类：链路（通过DNS解析为不同的IP），集群（分为硬件和软件，硬件是有单独物理机来分发请求，软件是最常见的，成本低，缺点是增加网络的负担），操作系统（利用操作系统的软中断和硬中断来实现）

















































