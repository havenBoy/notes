### HTTPS
> 简单的HTTP协议还是存在信息窃听或者身份伪装等安全问题，HTTPS解决问题

* 7.1 HTTP的缺点
  - 通信使用明文，不安全，报文本身不加密
    - 解决的方案：
        * 通信的加密  HTTP通过和SSL或者TLS的组合使用，创建通信的安全通信管道
        * 对报文内容的加密  加密的是报文的主体
  - 不验证通信方的身份，可能有伪装的
    - 对于发送请求客户端的身份的怀疑
    - 对于接受报文的客户端身份的怀疑
    - 对于某些具有访问权限的资源
    - 可能出现DOS攻击
  - 无法验证报文的完整性，可能报文被篡改
    * 报文在传输过程中，无法保证发送之前与接收之后的完整性；
* 7.2   HTTP + 加密 + 认证  + 完整性保护 = HTTPS
  * 


