# 通过DMS登录MongoDB数据库 {#task488 .task}

您可以通过阿里云的[数据管理服务DMS](https://help.aliyun.com/document_detail/47550.html)登录MongoDB数据库。使用DMS您可以更便捷地对MongoDB数据库进行管理。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)。 
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154501486313851_zh-CN.png)** \> **管理**进入基本信息页面。 
3.  在**Mongos列表**标签页，单击需要登录的节点的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154501486313851_zh-CN.png)****登录**，自动跳转至DMS 数据管理登录页面。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6694/154501486313839_zh-CN.png)

4.  在DMS登录页面，填写如下相应的信息登录MongoDB。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154501486313740_zh-CN.png)

    -   用户名：登录数据库的用户名，默认为root。
    -   密码：开通实例时指定的密码或者创建实例后重置的密码。
    -   数据库：登录时鉴权的数据库，默认为admin。
5.  单击**登录**。 

    如果您尚未将DMS服务器的IP地址加入MongoDB实例的白名单中，单击**登录**后则会弹出对话框提示。需要将对话框中显示的DMS服务器IP地址加入到MongoDB实例的白名单中才可以正常登录。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154501486333336_zh-CN.png)

    MongoDB实例添加白名单操作请参考[设置白名单](cn.zh-CN/分片集群快速入门/设置白名单.md#)。

    登陆成功后您就可以创建新的数据库以及其他MongoDB数据库相关的操作。更多DMS中的MongoDB操作请参考：[DMS for MongoDB](https://help.aliyun.com/document_detail/47683.html)。


