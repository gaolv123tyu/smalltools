#### golang写简单的正向https代理服务器

使用tcp连接，自己解析http协议解决
1. 接受客户端tcp连接
2. 读取字节流为request,(同时还要保存已经读到的字节流，以便转发给服务器)
3. 在2步取得的报头中读取服务器IP（或域名）及端口信息，TCP拨号服务端建立tcp连接
4. 根据报头信息判断是否为https的connect询问，如是回复客户端,否则直接第5步
5. 开始上下流量转发  

代如如下：（该代码经测试已稳定运行数小时）  
经测试可代码http,https,下载文件，看视频  
已知存的问题是QQ中的图片无法显示
