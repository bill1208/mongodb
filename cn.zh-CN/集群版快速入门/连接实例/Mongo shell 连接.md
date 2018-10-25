# Mongo shell 连接 {#task_wdf_npz_jfb .task}

您可以在ECS上安装mongo shell，用mongo shell的方式连接云数据库MongoDB。

为保障鉴权成功，请使用mongo shell 3.0及以上的版本连接云数据库MongoDB。

已经将允许访问该实例的IP地址或者IP段加入到实例白名单中，参见[设置白名单](https://www.alibabacloud.com/help/zh/doc-detail/88449.htm)。

1.   登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/detail/dds-bp141308a7947204/info)。 
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6689/154043593913802_zh-CN.png)** \> **管理**。 
3.   单击左侧导航栏的**数据库连接**，获取MongoDB的连接地址和端口号，如下图所示。 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6695/154043593913838_zh-CN.png)

    本示例有三个Mongos节点，需要登录哪个节点，使用对应的地址进行登录即可。

4.   在ECS上使用mongo命令进行连接，命令样例如下。 

    ```
    mongo --host dds-xxxx.mongodb.rds.aliyuncs.com:3717 -u root -p 123456 --authenticationDatabase admin
    ```

    mongo shell常见错误

    -   [连接问题](https://www.alibabacloud.com/help/zh/doc-detail/61100.htm)
    -   [连接数问题](https://www.alibabacloud.com/help/zh/doc-detail/61114.htm)
    -   [负载高问题](https://www.alibabacloud.com/help/zh/doc-detail/61149.htm)

