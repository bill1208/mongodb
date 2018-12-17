# 通过 Mongo Shell 登录MongoDB数据库 {#task_iw5_tg4_hfb .task}

云数据库MongoDB支持通过 Mongo Shell 的方式连接登录。

为保障鉴权成功，请安装 Mongo Shell 3.0及以上的版本。安装步骤请参考官方文档 [Install MongoDB](https://docs.mongodb.com/v3.4/installation/)。

已经将访问该实例的IP地址或者IP段加入到实例白名单中，详情请参见[设置白名单](intl.zh-CN/单节点快速入门/设置白名单.md#)。

1.   登录MongoDB[管理控制台](https://mongodb.console.aliyun.com/)。 
2.   单击目标实例ID进入基本信息页面。 
3.   单击左侧导航栏的**数据库连接**，可查看到实例的**内网连接 - 专有网络**和**公网连接**两种连接地址，根据您的情况选用，如下图所示。 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6664/154501409213741_zh-CN.png)

    连接地址和端口号之间用冒号隔开，默认端口号为3717，默认连接数据库为admin。

4.  在[ECS](https://www.alibabacloud.com/help/zh/doc-detail/25367.htm)上使用mongo命令进行连接，命令样例如下。 

    ```
    mongo --host <host>:3717 -u <username> -p <password> --authenticationDatabase admin
    ```

    说明：

    -   <host\>：MongoDB实例的连接地址。
    -   <username\>：登录数据库的用户名，默认为root。
    -   <password\>：登录数据库的密码。
    Mongo shell常见问题：

    -   [连接问题](https://www.alibabacloud.com/help/zh/doc-detail/61100.htm)
    -   [连接数问题](https://www.alibabacloud.com/help/zh/doc-detail/61114.htm)
    -   [负载高问题](https://www.alibabacloud.com/help/zh/doc-detail/61149.htm)

