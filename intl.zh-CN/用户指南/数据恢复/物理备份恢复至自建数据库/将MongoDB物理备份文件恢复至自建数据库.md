# 将MongoDB物理备份文件恢复至自建数据库 {#concept_lf5_qxp_5fb .concept}

您可以通过控制台下载MongoDB实例的的物理备份文件。本文介绍如何将MongoDB物理备份中的数据，恢复至本地自建的MongoDB数据库中。

## 前提条件 {#section_kdp_sxp_5fb .section}

-   该方法仅适用于云数据库MongoDB 副本集实例。
-   实例的存储引擎为 WiredTiger 或 RocksDB。

    **说明：** 如实例的存储引擎为 TerarkDB ，请使用[逻辑备份恢复至自建数据库](intl.zh-CN/用户指南/数据恢复/逻辑备份恢复至自建数据库.md#)。

-   实例的存储引擎为 RocksDB 时，您需要自行编译安装带有 RocksDB 存储引擎的 MongoDB 应用程序。
-   为保障MongoDB数据库的兼容性，自建MongoDB的版本要求如下。

    |MongoDB实例的数据库版本|要求本地自建MongoDB数据库版本|
    |:--------------|:-----------------|
    |3.2版本|3.2或3.4版本|
    |3.4版本|3.4版本|
    |4.0版本|4.0版本|


## 准备工作 {#section_lxg_5xp_5fb .section}

以下演示环境服务器的系统为Linux。（已安装对应版本的 MongoDB 服务，安装方法请参见MongoDB官方文档。）

下载及解压MongoDB物理备份文件。

1.  [下载MongoDB物理备份文件](intl.zh-CN/用户指南/数据恢复/物理备份恢复至自建数据库/副本集实例下载物理备份.md#)。
2.  将文件解压至本地服务器上MongoDB所在的data目录（**需确保是空的**）。

    假设将/path/to/mongo作为MongoDB物理恢复操作的所在目录。

    ```
    cd /path/to/mongo/data/
    rm -rf *
    ```

3.  将下载的MongoDB物理备份文件复制至/path/to/mongo/data/目录中并执行解压操作。

    ```
    tar xzvf hins_xxx.tar.gz 
    ```


## 以单节点模式恢复MongoDB物理备份的数据 {#section_pwz_yxp_5fb .section}

1.  在/path/to/mongo文件夹中新建配置文件mongod.conf。

    ```
    touch mongod.conf
    ```

2.  修改mongod.conf配置文件，使得符合启动的配置要求。

    根据存储引擎选择云数据库MongoDB物理备份启动的配置模板（单节点模式启动并开启认证），您可以复制至mongod.conf文件中。

    -   WiredTiger 存储引擎

        ```
        systemLog:
            destination: file
            path: /path/to/mongo/mongod.log
            logAppend: true
        security:
            authorization: enabled
        storage:
            dbPath: /path/to/mongo/data
            directoryPerDB: true
        net:
            http:
                enabled: false
            port: 27017
            unixDomainSocket:
                enabled: false
        processManagement:
            fork: true
            pidFilePath: /path/to/mongo/mongod.pid
        ```

        **说明：** 云数据库MongoDB默认使用的是WiredTiger存储引擎，并且开启了**directoryPerDB**选项，因此配置中指定了这个选项。

    -   RocksDB 存储引擎

        ```
        systemLog:
        	destination: file
        	path: /path/to/mongo/logs/mongod.log
        	logAppend: true
        security:
        	authorization: enabled​
        storage:
        	dbPath: /path/to/mongo/data
                engine: rocksdb
        net:
        	http:
        		enabled: false
        	port: 27017
        	unixDomainSocket:
        		enabled: false
        processManagement:
        	fork: true
        	pidFilePath: /path/to/mongo/logs/mongod.pid
        ```

3.  指定新建的配置文件 mongod.conf 来启动 MongoDB。

    ```
    /usr/bin/mongod -f /path/to/mongo/mongod.conf
    ```

4.  等待启动完成后，可通过服务器的 mongo shell 登录 MongoDB 数据库。

    ```
    mongo --host 127.0.0.1 -u <username> -p <password> --authenticationDatabase admin
    ```

    说明：

    -   <username\>：云数据库MongoDB上该实例的用户名，默认为 root 。
    -   <password\>：云数据库MongoDB上该实例设置的密码。

## 副本集模式启动MongoDB数据库 {#section_c4j_fcs_5fb .section}

云数据库MongoDB的物理备份默认带有原实例的副本集配置。启动时需以单节点模式启动，否则可能无法访问。

如需以副本集模式启动，需要先[以单节点模式恢复MongoDB数据](#section_pwz_yxp_5fb)，再按照以下步骤执行：

1.  通过服务器的mongo shell登录MongoDB数据库。
2.  移除原有副本集配置。

    ```
    use local
    db.system.replset.remove({})
    ```

3.  关闭mongodb进程服务。

    ```
    use admin
    db.shutdownServer()
    
    ```

4.  修改/path/to/mongo/目录下的配置文件mongod.conf，添加replication相关配置。详细命令用法请参考MongoDB官方文档[部署副本集](https://docs.mongodb.com/manual/tutorial/deploy-replica-set/index.html)。
5.  指定新建的配置文件 mongod.conf 来启动 MongoDB。

    ```
    /usr/bin/mongod -f /path/to/mongo/mongod.conf
    ```

6.  将成员加入副本集并初始化副本集。

    **说明：** 此步骤使用`rs.initiate()`命令进行操作，详细命令用法请参考MongoDB官方文档[rs.initiate\(\)命令介绍](https://docs.mongodb.com/manual/reference/method/rs.initiate/)。


