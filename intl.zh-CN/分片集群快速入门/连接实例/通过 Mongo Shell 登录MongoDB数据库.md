# 通过 Mongo Shell 登录MongoDB数据库 {#task_wdf_npz_jfb .task}

您可以在ECS上安装mongo shell，用mongo shell的方式连接云数据库MongoDB。

为保障鉴权成功，请安装 Mongo Shell 3.0及以上的版本。安装步骤请参考官方文档 [Install MongoDB](https://docs.mongodb.com/v3.4/installation/)。

已经将允许访问该实例的IP地址或者IP段加入到实例白名单中，详情请参见[设置白名单](intl.zh-CN/分片集群快速入门/设置白名单.md#)。

1.   登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/detail/dds-bp141308a7947204/info)。 
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6689/154501488313802_zh-CN.png)** \> **管理**。 
3.   单击左侧导航栏的**数据库连接**，获取MongoDB的连接地址和端口号，如下图所示。 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6695/154501488313838_zh-CN.png)

    本示例有三个Mongos节点，需要登录哪个节点，使用对应的地址进行登录即可。

4.   在ECS上使用mongo命令进行连接，命令样例如下。 

    ```
    mongo --host <host>:3717 -u <username> -p <password> --authenticationDatabase admin
    ```

    说明：

    -   <host\>：MongoDB实例的连接地址。
    -   <username\>：登录数据库的用户名，默认为root。
    -   <password\>：登录数据库的密码。
    mongo shell常见错误

    -   [连接问题](https://www.alibabacloud.com/help/zh/doc-detail/61100.htm)
    -   [连接数问题](https://www.alibabacloud.com/help/zh/doc-detail/61114.htm)
    -   [负载高问题](https://www.alibabacloud.com/help/zh/doc-detail/61149.htm)

