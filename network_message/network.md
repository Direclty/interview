# 网络基础

## 1、网络基础：

   * 定义 
   
     计算机网络各层 + 其协议的集合
     
   * 作用
   
     定义该计算机网络的所能完成的功能
     
   * 结构介绍 
   
     * 三种网络模型：
     
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/944365-b3deda7c3f3b92c6.png"/>
        </div>
    
      * OSI    体系结构(七层)：   概念清楚 & 理念完整 ，但是复杂 & 不实用
       
      * TCP/IP  体系结构(三层 [TCP协议](https://www.jianshu.com/p/65605622234b))：是Internet的核心协议 & 被广泛应用于局域网和广域网 (HTTP协议传信息的基础)
       
        <div>
           <img src="https://upload-images.jianshu.io/upload_images/944365-73d7d56b1f54d945.png?imageMogr2/auto-orient/"/>
        </div> 
        
        > 
        > 注意 ：http 位于最高层(应用层)
        >
        
        <div>
           <img src="https://upload-images.jianshu.io/upload_images/944365-492f1cf3981cb078.png?imageMogr2/auto-orient/"/>
        </div>
       
      * 五层   体系结构(五层)：   融合上面两种，目的是为了学习
      
## 2、HTTP协议  
     
### 简介：

   * 基本简介
   
       <div>
          <img src="https://upload-images.jianshu.io/upload_images/944365-a6c6e24b7bb7bfc7.png?imageMogr2/auto-orient/" />
       </div>
   
### 工作方式   

   * 工作方式
   
       <div align="center">
          <img src="https://upload-images.jianshu.io/upload_images/944365-28e4020dd64411b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/280" />
       </div>
       
### HTTP(报文)详解  

#### 请求报文

   * 格式
   
       <div align="center">
            <img src="https://upload-images.jianshu.io/upload_images/944365-76f625b54c1039be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/580" />
       </div>

* 请求行
    * 结构
         <div>
            <img src ="https://upload-images.jianshu.io/upload_images/944365-ee23b153f6d654c6.png?imageMogr2/auto-orient/" />
         </div>
           
    * 组成介绍
          <div>
            <img src ="https://upload-images.jianshu.io/upload_images/944365-332ccda4eb8625bf.png?imageMogr2/auto-orient/" />
          </div>
         
         > get和post的区别
         
         <div>
            <img src ="https://upload-images.jianshu.io/upload_images/944365-acce2f2323fd28a6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
         </div>
* 请求头

    * 请求和响应报文通用Header
    
         <div>
            <img src ="https://upload-images.jianshu.io/upload_images/944365-254eb5a7db3d3fe5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
         </div>
     
    * 通用的Header
    
         <div>
             <img src ="https://upload-images.jianshu.io/upload_images/944365-22f107afd0839c1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
         </div>
     
* 请求体

    * 作用：存放需要发送给服务器的信息
        
        > 可选部分，如[get]() 请求就没有请求数据
        
    * 使用方式
         <div>
              <img src ="https://upload-images.jianshu.io/upload_images/944365-6a361cc6960eb113.png?imageMogr2/auto-orient/" />
         </div>
         
* 总结
     
  * 关于报文的总结如下
           <div>
             <img src="https://upload-images.jianshu.io/upload_images/944365-63e390481e92aebe.png?imageMogr2/auto-orient/">
             <img src="https://upload-images.jianshu.io/upload_images/944365-806653dd8c7df0e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/480"/>
           </div>
           
#### 响应报文

 <div>
    <img src=""/>
 </div>
 
* 结构 

    <div>
        <img src="https://upload-images.jianshu.io/upload_images/944365-e74ef9116a1b5df8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/580"/>
    </div>
    
* 结构详细介绍 

     * 组成
       
       <div>
           <img src="https://upload-images.jianshu.io/upload_images/944365-834e3a1b316f265c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700"/>
        </div>
      
     * 具体介绍
     
         <div>
             <img src="https://upload-images.jianshu.io/upload_images/944365-bd27e7365b0b2855.png?imageMogr2/auto-orient/"/>
         </div>
         
     * 响应头
     
         * 请求响应报文通用header
         
             <div> 
                <img src="https://upload-images.jianshu.io/upload_images/944365-254eb5a7db3d3fe5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
             </div>
             
         * 常见响应header
         
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/944365-a9f0a212c4ea72b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
            
         * 响应体
         
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/944365-9e829a9edda9ceb0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
            
         * 响应报文 总结    
            
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/944365-cc24a9b8effcbd42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
            
### 两种方式总结
   
   * 请求报文 & 响应报文
   
       <div>
            <img src="https://upload-images.jianshu.io/upload_images/944365-57aec599cfef3f0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
       </div>
   
### 额外知识

  * HTTP1.0/HTTP1.1和HTTP2.0的区别  
  
       * HTTP1.1比HTTP1.0的优点
       
           * [长连接](http://www.cnblogs.com/boystar/p/7466042.html)
           * [节约宽带](http://www.cnblogs.com/boystar/p/7466042.html)
           * [HOST域](http://www.cnblogs.com/boystar/p/7466042.html)
           * 引入持久连接，即同一个TCP的连接中可传送多个HTTP请求和 & 响应
           * 多个请求和响应可同时进行、可叠加
           * 引入更多的请求头和响应头
              
     >   如身份认证、状态管理 & Cache缓存等机制相关的、HTTP1.0无host字段
     
       * HTTP1.1和[HTTP2.0](http://www.cnblogs.com/TomSnail/p/6104697.html)的区别
       
           * [HTTP/2采用二进制格式而非文本格式](http://www.cnblogs.com/Will-guo/p/8445102.html)
           * [为什么这样设计](http://www.cnblogs.com/Will-guo/p/8445102.html)
           * [服务器推送](http://www.cnblogs.com/boystar/p/7466042.html)
           * [多路复用](http://www.cnblogs.com/boystar/p/7466042.html)
           * [数据压缩](http://www.cnblogs.com/boystar/p/7466042.html)
     
  * HTTP1.0/HTTP1.1和HTTP2.0和[SPDY](http://www.cnblogs.com/TomSnail/p/6104697.html)之间的区别
  
       * HTTP1.0/HTTP1.1的不足
       
           * [只允许客户端主动发起请求](http://www.cnblogs.com/TomSnail/p/6104697.html)
           * [HTTP头冗余](http://www.cnblogs.com/TomSnail/p/6104697.html)
           * [单路连接](http://www.cnblogs.com/TomSnail/p/6104697.html)
           * [明文传输](http://www.cnblogs.com/TomSnail/p/6104697.html)
           
       * HTTPS的不足
           
           * [除了安全不能解决HTTP的其他问题](http://www.cnblogs.com/TomSnail/p/6104697.html)
           * [有一定费用](http://www.cnblogs.com/TomSnail/p/6104697.html)
           * [性能问题](http://www.cnblogs.com/TomSnail/p/6104697.html)
  
       * SPDY应运而生(扩展知识)
           
           > SPDY是Google公司2012年发布的基于TCP/IP的应用层协议。SPDY协议通过压缩、多路复用和优先级来缩短网页的加载时间和安全性。
           
            SPDY是Speedy的音，是更快的意思。
            
            * 简单原理
            
               * 协议层次 
                
                    <div>   
                        <img src="https://images2015.cnblogs.com/blog/562880/201611/562880-20161126171020846-132545577.png"/>
                    </div>
                    
            > 如上图SPDY位于HTTP之下，TCP和SSL之上
            
            * [数据格式及各数据位的意义](http://www.cnblogs.com/TomSnail/p/6104697.html)
            
            * [核心特性](http://www.cnblogs.com/TomSnail/p/6104697.html)
            
                * 单链接多路复用
                
                * 全双工，支持服务器推送技术
                
                * 压缩了HTTP头
                
                * 请求分级，重要资源有限传送
                
                * 强制使用SSL传输协议
                
            * 存在问题
                
                * 多域名情况下同样要建立多个连接
                
                * SSL/TLS协议性能问题
                
                * 所有头部名都要小写
                
                * 客户端必须支持gzip压缩
                
                * Google不再支持SPDY
                
            * 使用情况
            
               > 国内使用SPDY的大厂是阿里，还开源了一款基于Nginx的服务器[Tengine]( http://tengine.taobao.org/download/tengine-2.1.2.tar.gz)。
     
## 3、HTTPS协议
* 第一点：HTTPS过程(分为8步，三密钥):怎么验证第二步里面服务器发回的公钥（保证安全，以防被修改）？
   * 1、对称加密   ：
   
   明文 + 加密算法 + 私钥 = 密文  &  密文 + 解密算法 + 私钥 = 明文
   
   * 2、非对称加密 ：
   
   公钥加密 明文 +  加密算法 + 公钥 => 密文  & 密文 + 解密算法 + 私钥 => 明文
   
   私钥加密 明文 + 加密算法 +  私钥 => 密文  & 密文 + 解密算法 + 公钥 => 明文
   
* 第二点：

   HTTPS协议 = HTTP协议 + SSL/TLS 协议（在SSL/TLS中加密，然后用HTTP进行传输）
   SSL全称 Secure Sockets Layer,安全套接成协议，为网络通信提供安全及数据完整性的一种协议
   TLC全称 Transport Layer Security，安全传输层协议是SSL的后续版本（是差别显著的，两者采用的加密方式不一样）
   
*  第三点：HTTPS过程(分为8步，三密钥)：

   三密钥：服务端 公钥、私钥 和 客户端随机密匙
   
     * 1、向服务端发送HTTPS请求，连接到443端口
     * 2、服务端一对密匙：公钥 和 私钥，公钥可以对任何人公开
     * 3、向客户端发送公钥
     * 4、客户端验证公钥，验证成功生成随机数叫client key,并用公钥进行非对称加密，第一次HTTP请求结束
     * 5、向服务器发送加密之后的数据（第二次请求）
     * 6、服务器收到加密的数据之后解密出client key ,用client key对数据加密传输数据
     * 7、发送加密数据到客户端
     * 8、客户端用client key进行解密
     
   怎么验证第二步里面服务器发回的公钥（保证安全，以防被修改）？
   
     > 数字证书：a借钱 -     b担保人     - c借到钱
                       证书认证中心（全称 Certificate Authority 简称 CA） ：全球100多个VeriSign、GlobalSign等等
                       认证过程：CA里面有自己的公钥和私钥，用自己的私钥对要发送的公钥进行非对称加密，得到密文之后在加上证书过期时间，颁发给，颁发者等信息组成数字证书
      得到数字证书之后用公钥解密（用内置的100多种CA证书看能够解密成功），并检查颁发给和过期时间等
      证书链
      
* Android中的HTTPS：

  HttpsUrlConnection 继承 httpUrlConnection
  国内访问12306.cn的时候会弹出数字证书,不是Android内置的数字证书，为了解决这个问题，要自己修改
  * 1、不对证书做任何审查（有重大安全漏洞）
  * 2、下载12306.cn的证书，并放在assets目录中（五步骤）
  * 3、会存在过期问题，
  * 4、最好的方式是信任12306证书的签发者
  
## 4、Socket

  * 目录
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/944365-59926986f3c800e0.png?imageMogr2/auto-orient/" />
        </div>

* Socket是什么？

    * 套接字，应用层与 TCP/IP 协议族通信中的中间软件抽象层，表现为一个封装了TCP/IP协议族的编程接口
    
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/944365-1a92e10c6c694d0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/545" />
        </div>
        
        * 1、Socket不是协议,是一个编程接口(API)，属于传输层(数据在网络中如何传输)
        
        * 2、通过Socket才能在Android平台上通过TCP/IP协议进行开发
        
        * 3、对用户来说，只需要用户调用Socket去组织数据，以符合指定的协议，即可通信
        
        * 成对出现，一对套接字： 
           
            > Socket ={(IP地址1:PORT端口号)，(IP地址2:PORT端口号)}
            
        *    一个 Socket 实例 唯一代表一个主机上的一个应用程序的通信链路
        
    *  建立Socket连接过程
        
        <div>
           <img src="https://upload-images.jianshu.io/upload_images/944365-eb79b5a461ac71b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600" />
        </div>
            
        * 原理
            
            * Socket的使用类型主要有两种：
            
                * 流套接字(StreamSocket) ：基于 TCP协议，采用 流的方式 提供可靠的字节流服务
                
                * 数据报套接字(DatagramSocket)：基于 UDP协议，采用 数据报文 提供数据打包发送的服务
                   
                   <div>
                      <img src="https://upload-images.jianshu.io/upload_images/944365-8df0ed7afe6b32d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/610"/>
                   </div>
                   
    * Socket 与 Http 对比 
    
        * Socket属于传输层，因为 TCP / IP协议属于传输层，解决的是数据如何在网络中传输的问题
        
        * HTTP协议 属于 应用层，解决的是如何包装数据
        
        * 由于二者不属于同一层面，所以本来是没有可比性的。但随着发展，默认的Http里封装了下面几层的使用，所以才会出现Socket & HTTP协议的对比：（主要是工作方式的不同）：             
        
            * Http：采用 请求—响应 方式
            
                * 即建立网络连接后，当 客户端 向 服务器 发送请求后，服务器端才能向客户端返回数据。
                
                * 可理解为：是客户端有需要才进行通信
                
            * Socket：采用 服务器主动发送数据 的方式
            
                * 即建立网络连接后，服务器可主动发送消息给客户端，而不需要由客户端向服务器发送请求
                
                * 可理解为：是服务器端有需要才进行通信
* 怎么用？

    <pre class="hljs cpp"><code class="cpp"> 
    
        <span class="hljs-comment">// 步骤1：创建客户端 &amp; 服务器的连接</span>
        
            <span class="hljs-comment">// 创建Socket对象 &amp; 指定服务端的IP及端口号 </span>
            Socket socket = <span class="hljs-keyword">new</span> Socket(<span class="hljs-string">"192.168.1.32"</span>, <span class="hljs-number">1989</span>);  
        
            <span class="hljs-comment">// 判断客户端和服务器是否连接成功  </span>
            socket.isConnected());
        
                             
        <span class="hljs-comment">// 步骤2：客户端 &amp; 服务器 通信</span>
        
        <span class="hljs-comment">// 通信包括：客户端 接收服务器的数据 &amp; 发送数据 到 服务器</span>
        
            &lt;-- 操作<span class="hljs-number">1</span>：接收服务器的数据 --&gt;
                
                    <span class="hljs-comment">// 步骤1：创建输入流对象InputStream</span>
                    InputStream is = socket.getInputStream() 
        
                    <span class="hljs-comment">// 步骤2：创建输入流读取器对象 并传入输入流对象</span>
                    <span class="hljs-comment">// 该对象作用：获取服务器返回的数据</span>
                    InputStreamReader isr = <span class="hljs-keyword">new</span> InputStreamReader(is);
                    BufferedReader br = <span class="hljs-keyword">new</span> BufferedReader(isr);
        
                    <span class="hljs-comment">// 步骤3：通过输入流读取器对象 接收服务器发送过来的数据</span>
                    br.readLine()；
        
        
            &lt;-- 操作<span class="hljs-number">2</span>：发送数据 到 服务器 --&gt;                  
        
                    <span class="hljs-comment">// 步骤1：从Socket 获得输出流对象OutputStream</span>
                    <span class="hljs-comment">// 该对象作用：发送数据</span>
                    OutputStream outputStream = socket.getOutputStream(); 
        
                    <span class="hljs-comment">// 步骤2：写入需要发送的数据到输出流对象中</span>
                    outputStream.write（（<span class="hljs-string">"Carson_Ho"</span>+<span class="hljs-string">"\n"</span>）.getBytes(<span class="hljs-string">"utf-8"</span>)）；
                    <span class="hljs-comment">// 特别注意：数据的结尾加上换行符才可让服务器端的readline()停止阻塞</span>
        
                    <span class="hljs-comment">// 步骤3：发送数据到服务端 </span>
                    outputStream.flush();  
        
        
        <span class="hljs-comment">// 步骤3：断开客户端 &amp; 服务器 连接</span>
        
                     os.close();
                    <span class="hljs-comment">// 断开 客户端发送到服务器 的连接，即关闭输出流对象OutputStream</span>
        
                    br.close();
                    <span class="hljs-comment">// 断开 服务器发送到客户端 的连接，即关闭输入流读取器对象BufferedReader</span>
        
                    socket.close();
                    <span class="hljs-comment">// 最终关闭整个Socket连接</span>
        </code>
    
    </pre>
    
* 为什么这么用？