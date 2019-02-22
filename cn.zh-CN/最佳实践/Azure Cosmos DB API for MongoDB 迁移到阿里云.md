# Azure Cosmos DB API for MongoDB 迁移到阿里云 {#concept_dwb_4rk_5fb .concept}

使用MongoDB数据库自带的备份还原工具，您可以将Azure Cosmos DB API for MongoDB迁移至阿里云。

## 注意事项 {#section_j3k_5sk_5fb .section}

-   该操作为全量迁移，为避免迁移前后数据不一致，迁移开始前请停止数据库写入。
-   如果您之前使用mongodump命令对数据库进行过备份操作，请将备份在dump文件夹下的文件移动至其他目录。确保默认的dump备份文件夹为空，否则将会覆盖该文件夹下之前备份的文件。
-   请在安装有MongoDB服务的服务器上执行mongodump和mongorestore命令，并非在mongo shell环境下执行。

## 数据库账号权限要求 {#section_oyv_j2l_5fb .section}

|实例类型|账号权限|
|:---|:---|
|Azure Cosmos DB|read|
|目的MongoDB实例|readWrite|

## 环境准备 {#section_y4p_ztk_5fb .section}

1.  创建云数据库MongoDB实例，详情请参考[创建实例](../../../../../cn.zh-CN/副本集快速入门/创建副本集实例.md#)。

    **说明：** 

    -   实例的存储空间要大于Azure Cosmos DB。
    -   实例的数据库版本选用3.4。
2.  设置阿里云MongoDB数据库的数据库密码，详情请参考[设置密码](../../../../../cn.zh-CN/用户指南/账号管理/重置密码.md#)。
3.  在某个服务器上安装MongoDB程序，详情请参考[安装MongoDB](https://docs.mongodb.com/manual/administration/install-community/)。

    **说明：** 

    -   请安装MongoDB3.0以上版本。
    -   该服务器仅作为数据备份与恢复的临时中转平台，迁移操作完成后不再需要。
    -   备份目录所在分区的可用磁盘空间要大于Azure Cosmos DB。
    本案例将MongoDB服务安装在Linux服务器上进行演示。


## 迁移步骤 {#section_gy4_pvk_5fb .section}

1.  登录Azure门户。
2.  在左侧导航栏单击**Azure Cosmos DB**。
3.  在Azure Cosmos DB页面，单击需要迁移的Cosmos DB 账户名称。
4.  在账户详情页，单击**Connection String**。
5.  单击**Read-only Keys**页签，查看连接该数据库所需的信息。

    ![](images/32319_zh-CN.png "Azure连接信息")

    **说明：** 迁移数据时使用只读权限的账号密码信息即可。

6.  在安装有MongoDB服务的Linux服务器上执行以下命令进行数据备份，将数据备份至该服务器上。

    ```
    mongodump --host <HOST>:10255 --authenticationDatabase admin -u <USERNAME> -p <PRIMARY PASSWORD> --ssl --sslAllowInvalidCertificates
    ```

    说明：将<HOST\>、<USERNAME\>、<PRIMARY PASSWORD\>更换为[Azure连接信息](#fig_qbq_fy5_vfb)图中对应选项的值。

    等待备份完成，Azure Cosmos DB的数据库将备份至当前目录下dump文件夹中。

7.  获取阿里云MongoDB数据库的Primary节点连接地址，详情请参考[实例连接说明](../../../../../cn.zh-CN/副本集快速入门/连接实例/副本集实例连接说明.md#)。
8.  在安装有MongoDB服务的Linux服务器上执行以下语句将数据库数据全部导入至阿里云MongoDB数据库。

    ```
     mongorestore --host <mongodb_host>:3717 --authenticationDatabase admin -u <username> -p <password> dump
    ```

    说明：

    -   <mongodb\_host\>：MongoDB实例的Primary节点连接地址。
    -   <username\>：登录MongoDB实例的数据库用户名。
    -   <password\>：登录MongoDB实例的数据库密码。

等待数据恢复完成，Azure Cosmos DB API for MongoDB数据库即迁移至阿里云MongoDB数据库中。

