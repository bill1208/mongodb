# DMS连接数据库 {#task488 .task}

 [DMS](http://dms-rds.aliyun.com/) 是一款访问管理云端数据的Web服务，支持Redis、 MySQL、SQL Server、PostgreSQL和MongoDB等数据源。DMS提供了数据管理、对象管理、数据流转和实例管理四部分功能，您可以通过控制台上的图形化工具（DMS）进行连接。

1.   登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/detail/dds-bp141308a7947204/info)。 
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6689/154028546913802_zh-CN.png)** \> **管理**进入基本信息页面。 
3.  下拉找到**Mongos列表**，单击需要登录的节点的******登录**，自动跳转至DMS 数据管理登录页面。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6694/154028546913839_zh-CN.png)

4.   在DMS登录页，填写如下相应的信息，即可成功登录MongoDB，如下图所示。 

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/44625/cn_zh/1520495279476/dms2.png)

    -   数据库用户名：root
    -   数据库名：admin
    -   密码：开通实例时指定的密码或者创建实例后重置的密码
    登陆成功后您就可以创建新的数据库以及做其他与MongoDB数据库相关的操作。更多DMS中的MongoDB操作请参考：[DMS for MongoDB](https://help.aliyun.com/document_detail/47683.html)。


