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


    