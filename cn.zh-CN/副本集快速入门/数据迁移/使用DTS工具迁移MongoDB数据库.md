# 使用DTS工具迁移MongoDB数据库 {#concept_rcw_511_kfb .concept}

使用数据传输服务 Data Transmission Service （以下简称 DTS），您可以将自建的本地MongoDB数据库数据迁移至云数据库MongoDB中。DTS支持全量数据迁移及增量数据迁移，使用增量数据迁移可以实现在本地应用不停服的情况下，平滑地完成MongoDB数据库的迁移工作。

## 注意事项 {#section_a3z_x11_kfb .section}

-   本地MongoDB数据库的架构类型不能为分片集群架构。

    **说明：** 分片集群架构请参考[使用mongodump和mongorestore工具迁移数据库](../intl.zh-CN/分片集群快速入门/数据迁移/使用自带命令行工具迁移数据.md#)。

-   支持跨存储引擎迁移（云数据库MongoDB支持WiredTiger、RocksDB、TerarkDB三种存储引擎）。
-   目标实例的存储空间须大于本地MongoDB数据库的存储空间。
-   为避免影响您的正常业务使用，请在业务低峰期进行数据迁移。

## 费用说明 {#section_m3c_t5f_cgb .section}

|迁移类型|链路配置费用|公网流量费用|
|:---|:-----|:-----|
|全量数据迁移|不收取|不收取|
|增量数据迁移|收取，费用详情请参考DTS产品定价。|不收取|

## 迁移类型说明 {#section_zjf_5fs_zfb .section}

-   全量数据迁移：将本地MongoDB数据库迁移对象的存量数据，全部迁移到目标MongoDB实例数据库中。
    -   支持database迁移。
    -   支持collection迁移。
    -   支持index迁移。
-   增量数据迁移：在全量迁移的基础上，将本地MongoDB数据库的增量更新数据同步到目标MongoDB实例数据库中。
    -   支持database新建、删除操作的同步。
    -   支持document新增、删除、更新操作的同步。
    -   支持collection新建、删除操作的同步。
    -   支持index新建、删除操作的同步。

## 迁移账号权限要求 {#section_kvw_kb1_kfb .section}

使用DTS迁移MongoDB数据时，选用不同的迁移类型所需的账号权限不同，具体如下。

|迁移类型|全量数据迁移|增量数据迁移|
|:---|:-----|------|
|本地MongoDB数据库|read| -   待迁移库的read
-   admin的read权限
-   local的read权限

 |
|目的MongoDB实例|readWrite|readWrite|

**说明：** 关于MongoDB数据库迁移账号的创建及授权操作请参考[MongoDB Create User说明](https://docs.mongodb.com/manual/reference/method/db.createUser/)。

## 操作步骤 {#section_njl_2c1_kfb .section}

1.  登录[DTS控制台](https://dts-intl.console.aliyun.com/)。
2.  在左侧导航栏，单击**数据迁移**。
3.  单击数据迁移页面右侧的**创建迁移任务**。
4.  配置迁移任务的**源库及目标库**信息。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6682/154502575734129_zh-CN.png)

    |源库及目标库信息说明表|
    |:----------|
    |任务名称|     -   DTS为每个任务自动生成一个任务名称，任务名称没有唯一性要求。
    -   您可以修改任务名称，建议为任务配置具有业务意义的名称，便于后续的任务识别。
 |
    |源实例信息|     -   实例类型：选择**有公网IP的自建数据库**。
    -   数据库类型：选择**MongoDB**。
    -   主机名或IP地址：填入本地MongoDB数据库的访问地址，这个地址必须为公网地址。
    -   端口：填入本地MongoDB数据库的服务端口。
    -   数据库名称：填入本地MongoDB数据库中，用于账号验证的鉴权数据库名称。
    -   数据库账号：填入本地MongoDB数据库的连接账号，权限要求请参见[迁移账号权限要求](#section_kvw_kb1_kfb)。
    -   数据库密码：填入本地MongoDB数据库账号对应的密码。
 |
    |目标实例信息|     -   实例类型：选择**MongoDB实例**。
    -   实例地区：选择目标MongoDB实例所在地域。
    -   MongoDB实例ID：选择目标MongoDB实例的实例ID。
    -   数据库名称：填入目标MongoDB实例中，用于账号验证的鉴权数据库名称，默认为admin。
    -   数据库账号：填入连接目标MongoDB实例数据库的账号，权限要求请参见[迁移账号权限要求](#section_kvw_kb1_kfb)。
    -   数据库密码：填入连接目标MongoDB实例数据库账号对应的密码。
 |

5.  配置完成后，单击页面右下角的**授权白名单并进入下一步**。

    **说明：** 

    -   此步骤会将DTS服务器的IP地址自动添加到目标MongoDB实例的白名单中，用于保障DTS服务器能够正常连接目标MongoDB实例。迁移完成后如不再需要可手动删除，详情请参考[白名单设置](intl.zh-CN/副本集快速入门/设置白名单.md#)。
    -   如果您的本地MongoDB数据库进行了白名单安全设置，您需要在**源库信息**栏目中，单击**获取DTS IP段**来获取到DTS服务器的IP地址，并将获取到的IP地址加入本地MongoDB数据库的白名单安全设置中。
6.  选择迁移对象及迁移类型。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/154502575733659_zh-CN.png)

    |迁移对象及迁移类型|
    |:--------|
    |迁移类型|     -   如果只需要进行全量迁移，那么迁移类型选择**全量数据迁移**。

**说明：** 为保障数据一致性，全量数据迁移期间请勿在本地MongoDB数据库中写入新的数据。

    -   如果需要进行不停机迁移，迁移类型同时选择**全量数据迁移**和**增量数据迁移**。
 |
    |迁移对象|     -   在**迁移对象**框中将想要迁移的数据库选中，单击移动到**已选择对象**框。
    -   迁移对象选择的粒度可以为：库、collection/function 两个粒度。
    -   默认情况下，迁移对象迁移到MongoDB实例后，对象名跟本地MongoDB数据库一致。

**说明：** 如果您迁移的对象在本地MongoDB数据库跟目标实例上名称不同，那么需要使用DTS提供的对象名映射功能。使用方法请参考[库表列映射](https://www.alibabacloud.com/help/zh/doc-detail/26628.htm)。

 |

7.  上述配置完成后，单击页面右下角的**预检查并启动**。

    **说明：** 

    -   在迁移任务正式启动之前，会先进行预检查。只有预检查通过后，才能成功启动迁移任务。
    -   如果预检查失败，单击具体检查项后的![](https://dts.console.aliyun.com/styles/images/info.png)，查看具体的失败详情。根据失败原因修复后，重新进行预检查。
8.  预检查通过后，单击**下一步**。
9.  在购买配置确认页面，选择**链路规格**并勾选**数据传输（按量付费）服务条款**。
10. 单击**购买并启动**，迁移任务正式开始。
    -   全量数据迁移

        等待迁移任务完成即可，迁移任务会自动停止。

    -   增量数据迁移

        迁移任务不会自动结束，观察迁移任务的状态显示为**增量迁移无延迟**的状态时，将源库停写几分钟，等待增量迁移再次进入**增量迁移无延迟**状态，手动停止迁移任务。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/154502575733674_zh-CN.png)


检查校验数据无误后即可将业务切换至云数据库MongoDB实例。

