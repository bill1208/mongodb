# 通过DMS登录MongoDB数据库 {#concept_xdd_13v_cgb .concept}

您可以通过阿里云的[数据管理服务DMS](https://help.aliyun.com/document_detail/47550.html)登录MongoDB数据库。使用DMS您可以更便捷地对MongoDB数据库进行管理。

## 注意事项 {#section_tqx_53v_cgb .section}

通过DMS登录MongoDB实例的数据库时，须使用MongoDB实例的内网连接地址，暂时不支持公网连接地址。

## 操作步骤 {#section_wtq_x3v_cgb .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)。
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154519813513851_zh-CN.png)** \> **管理**。
3.  单击左侧导航栏的**数据库连接**，获取 Primary 节点的内网连接地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154519813534538_zh-CN.png)

4.  单击右上角的**登录数据库**，跳转到数据管理控制台页面。
5.  在数据管理控制台页面，填写如下信息登录MongoDB。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154519813513740_zh-CN.png)

    -   网络地址及端口：填入Primary 节点的内网连接地址。
    -   数据库用户名：默认为root。
    -   数据库：鉴权数据库，默认为admin。
    -   密码：数据库登录密码，如忘记密码可[重置密码](cn.zh-CN/单节点快速入门/设置密码.md#)。
6.  单击**登录**。

    如果您尚未将DMS服务器的IP地址加入MongoDB实例的白名单中，单击**登录**后则会弹出对话框提示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154519813533336_zh-CN.png)

    **说明：** 将对话框中显示的DMS服务器IP地址加入到MongoDB实例的白名单中即可正常登录，详情请参考[设置白名单](cn.zh-CN/单节点快速入门/设置白名单.md#)。


关于DMS中MongoDB数据库的相关操作介绍请参考：[DMS for MongoDB](https://help.aliyun.com/document_detail/47683.html)。

