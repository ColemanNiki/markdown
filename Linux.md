### CentOS 6.5 Git安装
--------------------
1. **机器环境**  
    默认机器是腾讯云的CentOS 6.5。除默认外，无任何已安装服务。
2. **操作**  
    yum install curl curl-devel zlib-devel openssl-devel perl cpio expat-devel gettext-devel gcc perl-ExtUtils-MakeMaker package  
    > 配置安装需要的服务  

    wget http://distfiles.macports.org/git/git-2.1.1.tar.gz
    > 下载我们需要的安装包

    tar xzvf git-2.1.1.tar.gz
    > 解压git的安装包

    cd git-2.1.1
    > 进入目录中

    autoconf ./configure  
    make  
    make install
    > 编译内容，如果提示错误，获取root权限。

    git --version 
    > 如果输出版本号，说明安装成功


3. **mysql数据库配置**
    > http://www.centoscn.com/mysql/2014/1211/4290.html


-------------------

### Ubuntu root账户设置
-------------------
1. root账号一开始是没有密码的，首先使用`sudo passwd root` 为root账号添加密码
    > root 添加密码

2. 为了方便，可以切换到root账号，此时可以使用root，但是无法通过ssh登陆root `su root`
    > 切换到root账号

3. 修改sshd_config 文档的内容， `vi /etc/ssh/sshd_config` 找到下文的内容并且修改
    ```
        # Authentication:
        LoginGraceTime 120
        #PermitRootLogin without-password
        PermitRootLogin yes
        StrictModes yes
    ```
    > 修改配置文档

4. 使用新的配置，可以重启系统，也可以使用 `/etc/init.d/ssh restart`来重启服务
    >重启ssh服务


-------------------
    
