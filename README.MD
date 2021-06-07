
Webserver
===============
Linux下C++实现的WEB服务器。

* 使用 **线程池 + 非阻塞socket + epoll(ET和LT均实现) + 事件处理Reactor** 的并发模型
* 使用**状态机**解析HTTP请求报文，支持解析**GET和POST**请求
* 访问服务器数据库实现web端用户**注册、登录**功能，可以请求服务器**图片和视频文件**
* 实现**同步/异步日志系统**，记录服务器运行状态
* 经Webbench压力测试可以实现**上万的并发连接**数据交换

测试网站（阿里云服务器）
----

[阿克曼的Webserver](http://182.92.180.168:9000/)
测试账号：test
密码：1111


压力测试
---
阿里云服务器（1核2G）
![](https://tuchuang-1300238575.cos.ap-beijing.myqcloud.com/myblog/%E9%98%BF%E9%87%8C%E4%BA%91%E5%8E%8B%E6%B5%8B.png)

测试机器（虚拟机）配置 4核8G
![](https://tuchuang-1300238575.cos.ap-beijing.myqcloud.com/myblog/%E5%8E%8B%E6%B5%8B.png)

运行
-----
* 服务器测试环境
	* Ubuntu版本18.04(本地虚拟机)
	* MySQL版本5.7.33
* 浏览器测试环境
	* Windows、Linux均可
	* Chrome

* 创建数据库保存用户信息

    ```C++
    // 建立yourdb库
    create database yourdb;

    // 创建user表
    USE yourdb;
    CREATE TABLE user(
        username char(50) NULL,
        passwd char(50) NULL
    )ENGINE=InnoDB;

    // 添加数据
    INSERT INTO user(username, passwd) VALUES('name', 'passwd');
    ```

* 修改main.cpp中的数据库初始化信息

    ```C++
    //数据库登录名,密码,库名
    string user = "root";
    string passwd = "passwd";
    string databasename = "yourdb";
    ```

* 编译运行即可

