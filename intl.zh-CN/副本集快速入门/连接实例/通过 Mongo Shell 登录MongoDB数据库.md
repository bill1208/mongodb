# 通过 Mongo Shell 登录MongoDB数据库 {#concept_qgf_hv4_dgb .concept}

您可以在本地服务器上或ECS上安装 Mongo Shell 工具，通过 Mongo Shell 的方式登录MongoDB数据库。

## 注意事项 {#section_psj_jv4_dgb .section}

-   为保障鉴权成功，请安装 Mongo Shell 3.0及以上的版本。安装步骤请参考官方文档 [Install MongoDB](https://docs.mongodb.com/v3.4/installation/)。
-   需要提前将访问该实例的IP地址或者IP段加入到实例白名单中，详情请参见[设置白名单](intl.zh-CN/副本集快速入门/设置白名单.md#)。
-   如需通过公网登录MongoDB数据库，需要申请公网连接地址，详情请参见[申请公网连接地址](intl.zh-CN/副本集快速入门/连接实例/申请公网连接地址.md#)。

## 操作步骤 {#section_i15_dw4_dgb .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com)。
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154512642113851_zh-CN.png)** \> **管理**
3.  单击左侧导航栏的**数据库连接**。
4.  在在安装有 Mongo Shell 的 服务器上进行连接。
    -   副本集中的单个节点连接方式。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6675/154512642131535_zh-CN.png)

        日常测试时，可直接连接 Primary 节点。需要注意的是一旦发生[主备切换](../intl.zh-CN/用户指南/主备切换/副本集实例设置主备切换.md#)，连接节点的角色将发生变化，从而会对读写操作造成影响。

        Mongo Shell 连接示例

        ```
        mongo --host <host>:3717 -u <username> -p <password> --authenticationDatabase admin
        ```

        **说明：** 

        -   <host\>：Primary 节点连接地址中的域名信息。
        -   <username\>：登录数据库的用户名，默认为root。
        -   <password\>：登录数据库的密码。
    -   高可用连接方式（推荐）：可实现高可用，确保连接的节点始终为 Primary 节点，不会因为主备切换而影响读写操作。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6675/154512642134449_zh-CN.png)

        Mongo Shell 连接示例

        ```
        mongo "<ConnectionStringURI>"
        ```

        **说明：** 

        -   双引号须为英文双引号。
        -   <ConnectionStringURI\>：实例的**ConnectionStringURI**地址，**ConnectionStringURI**地址中`****`为数据库密码。数据库密码设置请参考[设置密码](intl.zh-CN/副本集快速入门/设置密码.md#)。

## 相关问题 {#section_why_5w4_dgb .section}

-   [排查 Mongo Shell 登录问题](../intl.zh-CN/产品使用问题/排查 Mongo Shell 登录问题.md#)
-   [排查 MongoDB CPU使用率高的问题](../intl.zh-CN/最佳实践/排查 MongoDB CPU使用率高的问题.md#)
-   [如何查询及限制连接数](../intl.zh-CN/产品使用问题/如何查询及限制连接数.md#)

