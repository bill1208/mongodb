# 通过 Mongo Shell 登录MongoDB数据库 {#concept_qgf_hv4_dgb .concept}

您可以在本地或ECS上安装Mongo Shell工具，通过 Mongo Shell 的方式连接MongoDB数据库。

## 注意事项 {#section_psj_jv4_dgb .section}

为保障鉴权成功，请安装 Mongo Shell 3.0及以上的版本。安装步骤请参考官方文档 [Install MongoDB](https://docs.mongodb.com/v3.4/installation/)。

## 操作步骤 {#section_i15_dw4_dgb .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com)。
2.  单击目标实例ID或者单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6723/154501370813851_zh-CN.png)** \> **管理**
3.  单击左侧导航栏的**数据库连接**。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6675/154501370831535_zh-CN.png)

    **说明：** 

    -   红框标注的内容为连接地址。
    -   端口号为3717，连接地址和端口号之间用冒号隔开。
    -   连接到Primary节点拥有读写权限，连接到Secondary节点仅拥有读权限。
4.  在ECS上使用mongo命令进行连接，命令样例如下。

    ```
    mongo --host <host>:3717 -u <username> -p <password> --authenticationDatabase admin
    ```

    说明：

    -   <host\>：MongoDB实例的连接地址。
    -   <username\>：登录数据库的用户名，默认为root。
    -   <password\>：登录数据库的密码。

## 常见错误 {#section_why_5w4_dgb .section}

-   [连接问题](https://www.alibabacloud.com/help/zh/doc-detail/61100.htm)
-   [连接数问题](https://www.alibabacloud.com/help/zh/doc-detail/61114.htm)
-   [负载高问题](https://www.alibabacloud.com/help/zh/doc-detail/61149.htm)

