# 通过DMS登录MongoDB数据库 {#concept_xdd_13v_cgb .concept}

您可以通过阿里云的[数据管理服务DMS](https://help.aliyun.com/document_detail/47550.html)登录MongoDB数据库。使用DMS您可以更便捷地对MongoDB数据库进行管理。

## 注意事项 {#section_tqx_53v_cgb .section}

通过DMS登录MongoDB数据库时，须使用MongoDB实例的内网连接地址，暂时不支持外网连接地址。

## 操作步骤 {#section_wtq_x3v_cgb .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)。
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154501371913851_zh-CN.png)** \> **管理**。
3.  击右上角的**登录数据库**，选择要登录的数据库节点为**Primary**或**Secondary**，直接跳转到DMS 数据管理登录页面

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6674/154501371913329_zh-CN.png)

4.  在DMS登录页面，填写如下相应的信息登录MongoDB数据库。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154501371913740_zh-CN.png)

    -   用户名：登录数据库的用户名，默认为root。
    -   密码：开通实例时指定的密码或者创建实例后重置的密码。
    -   数据库：登录时鉴权的数据库，默认为admin。
5.  单击**登录**。

    如果您尚未将DMS服务器的IP地址加入MongoDB实例的白名单中，单击**登录**后则会弹出对话框提示。需要将对话框中显示的DMS服务器IP地址加入到MongoDB实例的白名单中才可以正常登录。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154501371933336_zh-CN.png)

    MongoDB实例添加白名单操作请参考[设置白名单](cn.zh-CN/副本集快速入门/设置白名单.md#)。

    登陆成功后您就可以创建新的数据库以及其他MongoDB数据库相关的操作。更多DMS中的MongoDB操作请参考：[DMS for MongoDB](https://help.aliyun.com/document_detail/47683.html)。


