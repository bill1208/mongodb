# Mongo shell 连接 {#task_wdf_npz_jfb .task}

您可以在ECS上安装mongo shell，用mongo shell的方式连接云数据库MongoDB。

为保障鉴权成功，请使用mongo shell 3.0及以上的版本连接云数据库MongoDB。

1.   登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/detail/dds-bp141308a7947204/info)。 
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6671/154210182613267_zh-CN.png)** \> **管理**进入基本信息页面。 
3.  单击左侧导航栏的**数据库连接**。 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6675/154210182631535_zh-CN.png)
    -   红框标注的内容为连接地址。
    -   端口号为3717，连接地址和端口号之间用冒号隔开。
4.   在ECS上使用mongo命令进行连接，命令样例如下。 

    ```
    mongo --host dds-xxxx.mongodb.rds.aliyuncs.com:3717 -u root -p Ft123456 --authenticationDatabase admin
    ```


**mongo shell常见错误**

-   [连接问题](https://www.alibabacloud.com/help/zh/doc-detail/61100.htm)
-   [连接数问题](https://www.alibabacloud.com/help/zh/doc-detail/61114.htm)
-   [负载高问题](https://www.alibabacloud.com/help/zh/doc-detail/61149.htm)

