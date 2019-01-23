# 腾讯云MongoDB数据库迁移至阿里云 {#concept_srk_yky_ggb .concept}

使用MongoDB数据库自带的备份还原工具 mongodump 和 mongorestore，您可以将腾讯云MongoDB数据库迁移至阿里云MongoDB数据库。

## 背景信息 {#section_vst_zqz_ngb .section}

本文为您介绍当业务调整或需要使用阿里云MongoDB特性功能时，如何使用MongoDB自带的备份还原工具（ mongodump 和 mongorestore），通过全量数据迁移方法，将腾讯云MongoDB数据库迁移至阿里云MongoDB数据库。

## 前提条件 {#section_p1c_1rz_ngb .section}

-   本文适用于数据库版本为3.2或3.6版本的腾讯云MongoDB实例。
-   mongodump 和 mongorestore 工具安装的软件版本，与腾讯云MongoDB数据库的版本一致。

## 注意事项 {#section_j3k_5sk_5fb .section}

-   该操作为全量迁移，暂不支持增量迁移。迁移开始前需要停止腾讯云MongoDB数据库的相关业务，同时为避免迁移前后数据不一致，迁移开始前请停止数据库写入。
-   阿里云MongoDB实例支持3.2、3.4和4.0版本。
-   阿里云MongoDB数据库支持WiredTiger、RocksDB、TerarkDB三种存储引擎。
-   如果您之前使用 mongodump 命令对数据库进行过备份操作，请将备份在dump文件夹下的文件移动至其他目录。确保默认的dump备份文件夹为空，否则将会覆盖该文件夹下之前备份的文件。
-   请在安装有MongoDB服务的服务器上执行 mongodump 和 mongorestore 命令，并非在mongo shell环境下执行。

## 数据库账号权限要求 {#section_oyv_j2l_5fb .section}

|迁移对象|权限要求|
|:---|:---|
|腾讯云MongoDB实例|read|
|阿里云MongoDB实例|readWrite|

## 阿里云环境准备 {#section_y4p_ztk_5fb .section}

创建阿里云MongoDB实例，详情请参考[创建副本集实例](../../../../../cn.zh-CN/副本集快速入门/创建副本集实例.md#)或[创建分片集群实例](../../../../../cn.zh-CN/分片集群快速入门/创建分片集群实例.md#)。

**说明：** 

-   阿里云MongoDB实例的存储空间要大于腾讯云MongoDB数据库的存储空间。
-   如迁移至阿里云MongoDB分片集群实例，建议对数据进行分片，详情请参考[设置数据分片](../../../../../cn.zh-CN/最佳实践/设置数据分片以充分利用Shard性能.md#)。

## 操作步骤 {#section_nf4_mby_ggb .section}

由于腾讯云MongoDB实例只有内网连接地址，没有公网连接地址，需要创建一个具有公网地址的腾讯云服务器用作数据中转，完成数据库的迁移操作。迁移操作完成后如不再需要，可释放该服务器。

**说明：** 

-   为保障腾讯云服务器和腾讯云MongoDB实例可正常通信。创建腾讯云服务器时，腾讯云服务器的地域、可用区、私有网络和子网保持与腾讯云MongoDB实例一致。
-   创建腾讯云服务器时，选用的存储空间大于腾讯云MongoDB数据库的存储空间。

本次演示的案例中，创建腾讯云服务器时使用的是Linux系统。

1.  创建一个按量付费的腾讯云服务器。
2.  登录腾讯云服务器，安装MongoDB程序，程序版本与腾讯云MongoDB数据库的版本一致。详情请参考[安装MongoDB](https://docs.mongodb.com/manual/administration/install-community/)。
3.  在腾讯云控制台，查看腾讯云MongoDB实例的内网IP地址。

    ![查看MongoDB实例的内网IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154823765535670_zh-CN.png)

4.  在腾讯云服务器上执行以下命令进行数据备份，将数据备份至该服务器上。

    ```
    mongodump --host <HOST>:27017 --authenticationDatabase admin -u <USERNAME> -p <PRIMARY PASSWORD>
    ```

    **说明：** 

    -   <HOST\>：腾讯云MongoDB实例的内网IP地址。
    -   <USERNAME\>：腾讯云MongoDB数据库的登录用户名，默认为 mongouser。
    -   <PRIMARY PASSWORD\>：腾讯云MongoDB数据库登录密码。
    示例：

    ```
    mongodump --host 10.10.0.7:27017 --authenticationDatabase admin -u mongouser -p xxxxxxxx
    ```

    等待备份完成，腾讯云MongoDB数据库将备份至当前目录下dump文件夹中。

5.  在腾讯云控制台，查看腾讯云服务器的公网IP地址。

    ![查看云服务器的公网IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154823765535509_zh-CN.png)

6.  登录[阿里云MongoDB控制台](https://mongodb.console.aliyun.com)，将腾讯云服务器的公网IP地址加入到阿里云MongoDB实例的白名单中。详情请参考[设置白名单](cn.zh-CN/用户指南/数据安全性/设置白名单.md#)。
7.  获取阿里云MongoDB实例的公网连接地址。

    -   如要迁移至阿里云MongoDB副本集实例，请获取 Primary 节点公网连接地址，详情请参考[副本集实例连接说明](../../../../../cn.zh-CN/副本集快速入门/连接实例/副本集实例连接说明.md#)。
    -   如要迁移至阿里云MongoDB分片集群实例，请获取任一 Mongos 节点的公网连接地址，详情请参考[分片集群实例连接说明](../../../../../cn.zh-CN/分片集群快速入门/连接实例/分片集群实例连接说明.md#)。
    **说明：** 公网连接地址需要手动申请，详情请参考[申请公网连接地址](cn.zh-CN/用户指南/管理网络连接类型/申请公网连接地址.md#)。

8.  在腾讯云服务器上执行以下语句将数据库数据导入至阿里云MongoDB数据库。

    ```
    mongorestore --host <mongodb_host>:3717 --authenticationDatabase admin -u <username> -p <password> -d <database> <database_backupfile_directory>
    ```

    **说明：** 

    -   <mongodb\_host\>：阿里云MongoDB副本集实例的 Primary 节点或阿里云MongoDB分片集群实例的 Mongos 节点连接地址。
    -   <username\>：阿里云MongoDB实例的数据库用户名。
    -   <password\>：阿里云MongoDB实例的数据库密码。
    -   <database\>：需要恢复的数据库。备份文件中如有多个数据库，需要重复本步骤进行其它数据库的恢复。
    -   <database\_backupfile\_directory\>：数据库备份文件所在的目录。
    示例：

    恢复数据库备份文件中的 mongodbtest 数据库

    ```
    mongorestore --host dds-bpxxxxxxxxxx-pub.mongodb.rds.aliyuncs.com:3717 --authenticationDatabase admin -u root -p xxxxxxxx -d mongodbtest /dump/mongodbtest
    ```

    恢复数据库备份文件中的 test123 数据库

    ```
    mongorestore --host dds-bpxxxxxxxxxx-pub.mongodb.rds.aliyuncs.com:3717 --authenticationDatabase admin -u root -p xxxxxxxx -d test123 /dump/test123
    ```


等待数据恢复完成，即完成腾讯云MongoDB数据库即迁移至阿里云MongoDB数据库的操作。根据业务需求选择合适的时间，将业务切换至阿里云MongoDB实例中。

## 更多信息 {#section_lzy_b21_4gb .section}

-   [副本集实例连接说明](../../../../../cn.zh-CN/副本集快速入门/连接实例/副本集实例连接说明.md#)
-   [分片集群实例连接说明](../../../../../cn.zh-CN/分片集群快速入门/连接实例/分片集群实例连接说明.md#)

