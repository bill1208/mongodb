# 通过DMS登录MongoDB数据库 {#concept_xdd_13v_cgb .concept}

您可以通过阿里云的[数据管理服务DMS](https://help.aliyun.com/document_detail/47550.html)登录MongoDB数据库。使用DMS您可以更便捷地对MongoDB数据库进行管理。

## 前提条件 {#section_nlw_mz4_tgb .section}

已将DMS服务器的IP地址加入至 MongoDB 实例的白名单中，详情请参考[设置白名单](cn.zh-CN/单节点快速入门/设置白名单.md#)。

|MongoDB实例的网络类型|DMS服务器的IP地址|
|:-------------|:----------|
|内网连接 - 专有网络| 100.104.175.0/24

 100.104.72.0/24

 100.104.5.0/24

 100.104.205.0/24

 |

## 注意事项 {#section_tqx_53v_cgb .section}

通过DMS登录MongoDB实例的数据库时，须使用MongoDB实例的内网连接地址，暂不支持公网连接地址。

## 操作步骤 {#section_wtq_x3v_cgb .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)。
2.  在页面左上角，选择实例所在的地域。
3.  在左侧导航栏，单击**副本集实例列表**。
4.  找到目标实例，单击实例ID。
5.  单击左侧导航栏的**数据库连接**，获取 Primary 节点的内网连接地址。

    ![MongoDB内网连接地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154996124634538_zh-CN.png)

6.  单击右上角的**登录数据库**，跳转至数据管理控制台页面。
7.  在数据管理控制台页面，填写如下信息登录MongoDB数据库。

    ![DMS登录MongoDB页面](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23695/154996124613740_zh-CN.png)

    -   网络地址及端口：填入 Primary 节点的内网连接地址。
    -   数据库用户名：默认为 root 。
    -   数据库：鉴权数据库，默认为 admin 。
    -   密码：数据库登录密码，如忘记密码可[重置密码](cn.zh-CN/单节点快速入门/设置密码.md#)。
8.  单击**登录**。

更多关于DMS中MongoDB数据库的相关操作介绍请参考：[DMS for MongoDB](https://help.aliyun.com/document_detail/47683.html)。

