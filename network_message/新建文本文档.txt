# 网络基础

## 1、HTTP协议

### 网络基础：
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
  * HTTP1.1和HTTP1.0的区别  
       * HTTP1.1比HTTP1.0的优点
       
           * 引入持久连接，即同一个TCP的连接中可传送多个HTTP请求和 & 响应
           * 多个请求和响应可同时进行、可叠加
           * 引入更多的请求头和响应头
              
     >   如身份认证、状态管理 & Cache缓存等机制相关的、HTTP1.0无host字段
     
## 2、HTTPS协议
* 第一点：HTTPS过程(分为8步，三密钥):怎么验证第二步里面服务器发回的公钥（保证安全，以防被修改）？
   * 1、对称加密   ：
   
   明文 + 加密算法 + 私钥 = 密文   密文 + 解密算法 + 私钥 = 明文
   
   * 2、非对称加密 ：
   
   公钥加密 明文 +  加密算法 + 公钥 => 密文  密文 + 解密算法 + 私钥 => 明文
   
   私钥加密 明文 + 加密算法 +  私钥 => 密文  密文 + 解密算法 + 公钥 => 明文
   
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
## 3、Socket