# 使用DTS工具迁移数据 {#concept_rcw_511_kfb .concept}

云数据库MongoDB版目前提供两种迁移方案：使用数据传输服务 DTS（以下简称 DTS）导入数据和使用MongoDB自带命令行工具导入数据。本文主要介绍如何使用DTS将本地自建MongoDB数据库数据导入云数据库MongoDB。DTS支持全量数据迁移及增量数据迁移，可以实现在本地应用不停服的情况下，平滑地完成MongoDB数据库的迁移工作。

## DTS迁移数据限制 {#section_a3z_x11_kfb .section}

-   实例类型为单节点实例或副本集实例。
-   全量数据迁移。

    数据传输DTS将源数据库迁移对象的存量数据全部迁移到目标实例。

-   增量数据迁移。

    增量数据迁移的过程中，本地MongoDB的增量更新数据同步到云数据库MongoDB，最终本地MongoDB同云数据库MongoDB进入动态数据同步的过程。使用增量数据迁移，可以实现在本地MongoDB正常提供服务的情况下，平滑地完成本地自建MongoDB数据库到云数据库MongoDB的迁移。


## 迁移功能 {#section_icw_bb1_kfb .section}

-   MongoDB版本支持MongoDB 3.0、3.2、3.4版本。
-   MongoDB全量数据迁移支持。
    -   支持database迁移
    -   支持collection迁移
    -   支持index迁移
-   MongoDB增量数据迁移支持。
    -   支持document新增、删除、更新操作的同步
    -   支持collection新建、删除操作的同步
    -   支持database新建、删除操作的同步
    -   支持index新建、删除操作的同步

## 迁移权限要求 {#section_kvw_kb1_kfb .section}

当使用DTS进行MongoDB-\>云数据库MongoDB迁移时，不同的迁移类型对源跟目标MongoDB实例的迁移帐号权限要求如下：

|迁移类型|全量数据迁移|增量数据迁移|
|:---|:-----|------|
|本地MongoDB|read| -   待迁移库的read
-   admin的read权限
-   local的read权限

 |
|目的MongoDB实例|readWrite|readWrite|

## 迁移前准备 {#section_pl4_5b1_kfb .section}

如果您的本地MongoDB或MongoDB云数据库的迁移账号尚未创建，可以参考如下流程创建迁移账号：

```
    db.createUser({user:"username",pwd:"password",roles:[{role:"rolename1",db:"database_name1"},{role:"rolename2",db:"database_name2"}]})
```

迁移账号所需权限详见上面的迁移权限要求。

参数说明：

-   username：要创建的账号。
-   password：上面账号对应的密码。
-   rolename1/rolename2：待授权给username的角色名，例如上面的read，readWrite。
-   database\_name1/database\_name2：将database\_name1/database\_name2上的角色role1/role2授权给username。
-   关于MongoDB的角色授权也可以参考[MongoDB Create User说明](https://docs.mongodb.com/manual/reference/method/db.createUser/)。

## 迁移步骤 {#section_njl_2c1_kfb .section}

使用DTS进行数据迁移，操作步骤如下所示：

1.  打开阿里云[DTS控制台](http://dts.aliyun.com)，单击**数据迁移** \> **创建迁移任务**，进入任务配置页面，填写任务名称、源库信息以及目标库信息，如下图所示。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/60037/cn_zh/1506667681073/ykxx.png)![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/60037/cn_zh/1506667705070/mbk.png)

    |源库及目标库信息说明表|
    |:----------|
    |任务名称|     -   DTS为每个任务自动生成一个任务名称，任务名称没有唯一性要求。
    -   您可以根据需要修改任务名称，建议为任务配置具有业务意义的名称，便于后续的任务识别。
 |
    |源实例信息|     -   实例类型：选择有公网IP的自建数据库。
    -   数据库类型：选择MongoDB。
    -   主机名或IP地址：配置MongoDB访问地址，这个地址必须为公网访问方式。
    -   端口：本地MongoDB实例的监听端口。
    -   数据库名称：本地MongoDB数据的数据库名。
    -   数据库账号：本地MongoDB数据的连接账号。
    -   数据库密码：本地MongoDB数据连接账号对应的密码。
 |
    |目标实例信息|     -   实例类型：选择MongoDB实例。
    -   MongoDB实例ID：配置迁移的目标MongoDB实例的实例ID。
    -   DTS支持经典网络的MongoDB实例。如果您的MongoDB实例为VPC网络的实例，那么需要切换到经典网络模式后，再使用DTS进行迁移。
    -   数据库名称：云数据库MongoDB的默认数据库名。
    -   数据库账号：连接MongoDB实例的连接账号。
    -   数据库密码：上面数据库账号对应的密码。
 |

2.  当配置完连接信息后，单击右下角**授权白名单**。

    这个步骤DTS会将DTS服务器的IP地址添加到目标MongoDB云数据库的白名单中，避免因为MongoDB实例设置了白名单，DTS服务器连接不上MongoDB实例导致迁移失败。

3.  选择迁移对象及迁移类型。

    |迁移对象及迁移类型|
    |:--------|
    |迁移类型|     -   MongoDB，支持全量数据迁移、增量数据迁移。
    -   如果只需要进行全量迁移，那么迁移类型选择：全量数据迁移。
    -   如果需要进行不停机迁移，那么迁移类型选择：全量数据迁移＋增量数据迁移。
 |
    |迁移对象|     -   迁移对象选择的粒度可以为：库、collection/function 两个粒度。
    -   默认情况下，对象迁移到MongoDB实例后，对象名跟本地MongoDB数据库一致。

**说明：** 如果您迁移的对象在源数据库跟目标实例上名称不同，那么需要使用DTS提供的对象名映射功能，使用方法请参考：[库表列映射](https://help.aliyun.com/document_detail/26628.html)。

 |

4.  预检查。

    在迁移任务正式启动之前，会先进行前置预检查，只有预检查通过后，才能成功启动迁移。预检查的内容及修复方式请参考[预检查](https://help.aliyun.com/document_detail/60037.html?spm=a2c4g.11186623.6.582.66804442QK1D58#yjc)。

    如果预检查失败，可以单击具体检查项后的按钮，查看具体的失败详情，并根据失败原因修复后，重新进行预检查。![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26625/cn_zh/1470308924221/MongoDB%E8%BF%81%E7%A7%BB_%E6%AD%A5%E9%AA%A43.jpg)

5.  启动迁移任务。

    当预检查通过后，可以启动迁移任务，在任务列表中可以查看迁移的具体状态及迁移进度。

    至此，完成本地MongoDB数据库到云数据库MongoDB的全部迁移任务。


## 预检查 {#section_z3t_k21_kfb .section}

DTS在启动迁移之前，会进行前置预检查，下表简单介绍MongoDB-\>云数据库MongoDB的预检查内容：

|检查项|检查内容|备注|
|:--|:---|:-|
|源库连接性检查|检查DTS服务器跟本地MongoDB实例的连通性| -   填写信息是否有误？如果填写信息有误，请修改后重新预检查。
-   检查端口是否配置从其他服务器连接访问。

 |
|目标库连接性检查|检查DTS服务器跟目标MongoDB实例的连通性|检查填写信息是否有误，如果有误请先修改后重新预检查。|
|源库版本检查|检查本地MongoDB的版本DTS是否支持|请先升级版本到3.2后，重新预检查。|
|源库权限检查|检查本地MongoDB提供的迁移账号的权限是否满足需求|如果检查失败，请参照创建迁移账号中的授权后，重新预检查。|
|目的库权限检查|检查目的MongoDB数据库提供的迁移账号的权限是否满足需求|如果检查失败，请参照创建迁移账号中的授权后，重新预检查。|
|增量拓扑冲突检查|检查MongoDB实例上是否有其他增量迁移任务正在运行|如果检查失败，那么需要结束或删除其他的增量迁移任务后，重新预检查。|

