# ECS Linux 篇 {#task853 .task}

目前云数据库MongoDB是需要通过ECS的内网进行连接访问，如果您本地需要通过公网访问云数据库MongoDB，可以在ECS Linux云服务器中安装rinetd进行转发实现。

1.   在云服务器ECS Linux上安装rinetd。 

    ```language-shell
    wget http://www.boutell.com/rinetd/http/rinetd.tar.gz&&tar -xvf rinetd.tar.gz&&cd rinetd
    sed -i 's/65536/65535/g' rinetd.c (修改端口范围)
    mkdir /usr/man&&make&&make install
    ```

2.   打开配置文件。 

    ```language-shell
    vi /etc/rinetd.conf
    ```

3.   在配置文件中输入如下内容： 

    ```language-shell
    0.0.0.0 3717 MongoDB的链接地址 3717 logfile /var/log/rinetd.log
    ```

4.   执行如下命令启动rinetd。 

    ```language-shell
    rinetd
    ```

    **说明：** 通过`echo rinetd >>/etc/rc.local`可以设置为自启动，可以使用`pkill rinetd`结束该进程。

5.   验证测试。 

    在本地通过mongo shell连接ECS Linux服务器后进行登录验证，比如安装了 rinetd的服务器的IP是1.1.1.1：

    ```language-shell
    mongo --host 1.1.1.1:3717 -u root -p 密码 --authenticationDatabase admin
    ```

    通过上述步骤即可实现：您本地的PC或服务器通过公网连接ECS Linux 3717端口，对云数据库MongoDB进行访问。

    **说明：** 您可以通过该方案进行测试使用，因rinetd为开源软件，如在使用过程中存在疑问，您可以参看其官方文档或与rinetd官方进行联系确认。


