### GHOST框架安装
----

1. 编译安装`pcre`,`openssl`,`zlib`

2. 编译安装`nginx`

3. Ghost安装    
    1. 官方下载Ghost文档，解压
    2. 在Ghost解压目录下运行`npm install --production`
    3. 初次启动 `npm start --production`
        > 这里最好修改成淘宝镜像下载
    4. 设置nginx请求转发，具体需要转发的端口号看`config.js`中的设置
    5. 输入ip进入目录即可 `ip/ghost`为管理页面