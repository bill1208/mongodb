# 使用DTS工具迁移分片集群数据库上云 {#concept_fdj_twz_zfb .concept}

当前[数据传输服务DTS](https://help.aliyun.com/product/26590.html)暂不支持直接迁移本地自建的MongoDB分片集群数据库。您可以依次将本地MongoDB分片集群数据库中的各个Shard节点，迁移至阿里云MongoDB分片集群实例来实现迁移上云。通过DTS的增量迁移功能，可以实现在本地应用不停服的情况下，平滑完成MongoDB数据库的迁移上云工作。

## 前提条件 {#section_jx1_5wy_ngb .section}

-   本地MongoDB数据库的各Shard节点具有公网地址或服务端口开放至公网。
-   本地MongoDB数据库版本为3.0、3.2、3.4或3.6版本，暂不支持4.0版本。

    **说明：** 4.0版本的本地MongoDB数据库请参考[使用MongoDB工具迁移自建数据库上云](cn.zh-CN/分片集群快速入门/数据迁移/使用MongoDB工具迁移自建数据库上云.md#)。

-   阿里云MongoDB实例的存储空间应大于本地MongoDB数据库的存储空间。

## 注意事项 {#section_dww_lmr_zfb .section}

-   不支持迁移admin数据库，即使被选择为迁移对象，该库中的数据也不会被迁移。
-   config数据库属于系统内部数据库，如无特殊需求，请勿迁移config数据库。
-   阿里云MongoDB实例支持的数据库版本为3.4版本和4.0版本。
-   阿里云MongoDB实例支持的存储引擎为 WiredTiger 、 RocksDB 和 TerarkDB。
-   为避免影响您的正常业务使用，请在业务低峰期进行数据迁移。

## 费用说明 {#section_brm_q21_1gb .section}

|迁移类型|链路配置费用|公网流量费用|
|:---|:-----|:-----|
|全量数据迁移|不收取|不收取|
|增量数据迁移|收取，费用详情请参考[数据传输服务DTS定价](https://cn.aliyun.com/price/product#/dts/detail)。|不收取|

## 迁移类型说明 {#section_zjf_5fs_zfb .section}

-   全量数据迁移：将本地MongoDB数据库迁移对象的存量数据全部迁移到目标MongoDB实例数据库中。
    -   支持database迁移。
    -   支持collection迁移。
    -   支持index迁移。
-   增量数据迁移：在全量迁移的基础上，将本地MongoDB数据库的增量更新数据同步到目标MongoDB实例数据库中。
    -   支持database新建、删除操作的同步。
    -   支持document新增、删除、更新操作的同步。
    -   支持collection新建、删除操作的同步。
    -   支持index新建、删除操作的同步。

## 迁移权限要求 {#section_mfq_xmr_zfb .section}

|实例类型|全量数据迁移|增量数据迁移|
|:---|:-----|:-----|
|本地MongoDB数据库|read权限| -   待迁移库的read权限
-   admin的read权限
-   local的read权限

 |
|目标MongoDB实例|readWrite权限|readWrite权限|

## 迁移前准备工作 {#section_pcx_yhs_zfb .section}

为避免影响您的正常业务使用，请在业务低峰期进行操作。

1.  关闭本地MongoDB数据库的均衡器 Balancer，详情请参考[关闭Mongodb分片集群均衡器](../cn.zh-CN/最佳实践/管理MongoDB均衡器Balancer .md#section_k3j_4wl_2gb) 。
2.  清除本地MongoDB数据库中，因块迁移失败产生的孤立文档。详情请参考[cleanupOrphaned](https://docs.mongodb.com/manual/reference/command/cleanupOrphaned/)。

    示例：

    在某个 shard 节点清除 test 数据库中 user 集合的所有孤立文档。

    ```
    var nextKey = { };
    var result;
    
    while ( nextKey != null ) {
      result = db.adminCommand( { cleanupOrphaned: "test.user", startingFromKey: nextKey } );
    
      if (result.ok != 1)
         print("Unable to complete at this time: failure or timeout.")
    
      printjson(result);
    
      nextKey = result.stoppedAtKey;
    }
    ```

    **说明：** 

    -   该操作需要在每个 Shard 节点中执行。
    -   如未清除孤立文档，可能影响迁移的性能。且在迁移过程中可能会遇到 \_id 冲突，导致迁移了错误的数据
3.  根据业务需要设置数据分片，详情请参考[设置数据分片以充分利用Shard性能](../cn.zh-CN/最佳实践/设置数据分片以充分利用Shard性能.md#)（可选）。

    **说明：** 您可以迁移前，在目标MongoDB实例中建立需要数据分片的数据库和集合，配置数据分片。也可以在迁移后配置数据分片。


## 迁移数据库操作步骤 {#section_lnt_knr_zfb .section}

1.  登录[DTS数据传输控制台](https://dts.console.aliyun.com/)。
2.  在左侧导航栏，单击**数据迁移**。
3.  单击数据迁移页面右侧的**创建迁移任务**。
4.  配置迁移任务的**源库及目标库**信息。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80861/155506281934677_zh-CN.png)

    |源库及目标库信息说明表|
    |:----------|
    |任务名称|     -   DTS为每个任务自动生成一个任务名称，任务名称没有唯一性要求。
    -   您可以根据需要修改任务名称，建议为任务配置具有业务意义的名称，便于后续的任务识别。
 |
    |源实例信息|     -   实例类型：选择**有公网IP的自建数据库**。
    -   实例地区：选择本地MongoDB数据库所在地区。
    -   数据库类型：选择**MongoDB**。
    -   主机名或IP地址：填入单个Shard节点的域名或IP地址。

**说明：** DTS通过依次迁移分片集群数据库的各Shard节点来实现整体迁移，此处先填入第一个Shard节点的域名或IP地址。稍后创建第二个迁移任务时，此处填入第二个Shard节点的域名或IP地址。以此类推，直至迁移所有Shard节点。

    -   数据库名称：填入本地MongoDB数据库中，用于账号验证的鉴权数据库名称。
    -   数据库账号：填入登录本地MongoDB数据库的数据库账号，权限要求请参见[迁移账号权限要求](#)。
    -   数据库密码：填入登录本地MongoDB数据库的数据库账号对应的密码。
 |
    |目标实例信息|     -   实例类型：选择**MongoDB实例**。
    -   实例地区：选择目标MongoDB实例所在地域。
    -   MongoDB实例ID：选择一个分片集群实例的ID作为目标MongoDB实例。
    -   数据库名称：填入目标MongoDB实例中，用于账号验证的鉴权数据库名称，默认为admin。
    -   数据库账号：填入连接目标MongoDB实例数据库的账号，权限要求请参见[迁移账号权限要求](#)。
    -   数据库密码：填入连接目标MongoDB实例数据库账号对应的密码。
 |

    **说明：** 如果本地MongoDB数据库设置了访问限制，请先放开DTS服务器的公网IP地址段的访问权限。IP地址段详情请单击源库及目标库页面中的**获取DTS IP段**。

5.  配置完成后，单击页面右下角的**授权白名单并进入下一步**。

    此步骤会将DTS服务器的IP地址自动添加到目标MongoDB实例的白名单中，用于保障DTS服务器能够正常连接MongoDB实例。迁移完成后如不再需要可手动删除，详情请参考[白名单设置](../cn.zh-CN/用户指南/数据安全性/设置白名单.md#)。

6.  选择**迁移对象**和**迁移类型**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80861/155506281934699_zh-CN.png)

    |迁移对象及迁移类型|
    |:--------|
    |迁移类型|     -   如果只需要进行全量迁移，迁移类型选择**全量数据迁移**。

**说明：** 为保障数据一致性，全量数据迁移期间请勿在源MongoDB数据库中写入新的数据。

    -   如果需要进行不停机迁移，迁移类型同时选择**全量数据迁移**和**增量数据迁移**。
 |
    |迁移对象|     -   在**迁移对象**框中将想要迁移的数据库选中，单击![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/155506281933712_zh-CN.png)移动到**已选择对象**框。

**说明：** 

        -   不支持迁移admin数据库，即使被选择为迁移对象，该库中的数据也不会被迁移。
        -   config数据库属于系统内部数据库，如无特殊需求，请勿迁移config数据库。
    -   迁移对象选择的粒度可以为：库、collection/function 两个粒度。
    -   默认情况下，对象迁移到MongoDB实例后，对象名跟本地MongoDB数据库一致。

**说明：** 

        -   每个Shard节点存储的数据可能不一样，也可能只有整个数据库的某一部分，这是由于Shard节点的特性决定的，迁移时选择需要迁移的数据即可。
        -   如果您迁移的对象在源数据库跟目标实例上名称不同，需要使用DTS提供的对象名映射功能，使用方法请参考[库表列映射](https://help.aliyun.com/document_detail/26628.html)。
 |

7.  上述配置完成后，单击页面右下角的**预检查并启动**。

    **说明：** 

    -   在迁移任务正式启动之前，会先进行预检查。只有预检查通过后，才能成功启动迁移任务。
    -   如果预检查失败，单击具体检查项后的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/155506281933661_zh-CN.png)，查看具体的失败详情。根据失败原因修复后，重新进行预检查。
8.  预检查通过后，单击**下一步**。
9.  在**购买配置确认**页面，选择**链路规格**并勾选**数据传输（按量付费）服务条款**。
10. 单击**购买并启动**，迁移任务正式开始。
    -   全量数据迁移

        等待迁移任务完成即可，迁移任务会自动停止。

    -   增量数据迁移

        迁移任务的状态显示为**增量迁移无延迟**，代表数据已同步至最新。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80861/155506281934686_zh-CN.png)

11. 重复第1步到第10步的操作步骤，创建其他Shard节点的迁移任务，并等待所有迁移任务迁移完成。

    **说明：** 

    1.  迁移任务不会自动结束，您可以不停单击**刷新**查看迁移任务的最新状态。当所有Shard节点的迁移任务均显示为**增量迁移无延迟**的状态时，将源库停写几分钟。
    2.  等待所有Shard节点的迁移任务再次进入**增量迁移无延迟**状态手动停止迁移任务。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80861/155506281934689_zh-CN.png)


检查校验数据无误后即可将业务切换至目标MongoDB实例。

