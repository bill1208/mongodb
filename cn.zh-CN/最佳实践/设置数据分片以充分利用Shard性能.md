# 设置数据分片以充分利用Shard性能 {#concept_tbb_vzp_bgb .concept}

您可以对分片集群实例中数据库的集合设置数据分片，以充分利用各 Shard 节点的存储空间和计算性能。

## 注意事项 {#section_mpp_hxq_bgb .section}

-   该操作仅适用于分片集群实例。
-   进行数据分片操作后，均衡器会对满足条件的现有数据进行分片，这将占用实例的性能，请在业务低峰期操作。
-   分片的片键一经设置后不可修改。
-   分片的片键选取将影响分片集群实例性能，片键的选取可参考[如何选择Shard Key](https://help.aliyun.com/document_detail/64561.html#h2--shard-key-3)。
-   若未进行数据分片，数据写入将被集中在 PrimaryShard 节点中。这将导致其他 Shard 节点的存储空间和计算性能无法被充分利用。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/78547/155228071033995_zh-CN.png)


## 操作示例 {#section_g4t_fxq_bgb .section}

本文进行操作演示的示例中，数据库为mongodbtest，集合为customer。

1.  [通过Mongo Shell登录分片集群实例](../../../../../cn.zh-CN/分片集群快速入门/连接实例/通过 Mongo Shell 登录MongoDB数据库.md#)。
2.  对集合所在的数据库启用分片功能。

    ```
    sh.enableSharding("<database>")
    ```

    说明：<database\>：数据库名。

    操作示例：

    ```
    sh.enableSharding("mongodbtest")
    ```

    **说明：** 您可以通过`sh.status()`查看分片状态。

3.  对集合的某个字段建立索引。

    ```
    db.<collection>.createIndex(<keys>,<options>)
    ```

    说明：

    -   <collection\>：集合名。
    -   <keys\>：包含用于建立索引的字段和排序方式。

        排序方式设置为1表示按升序来创建索引，设置为-1表示按照降序来创建索引。

    -   <options\>：表示接收可选参数，详情请参考[db.collection.createIndex\(\)](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/)，本操作示例中暂未使用到该字段。
    操作示例：

    ```
    db.customer.createIndex({"name":1})
    ```

4.  对集合设置数据分片。

    ```
    sh.shardCollection("<database>.<collection>",{ "<key>":<value> } ) 
    ```

    说明：

    -   <database\>：数据库名。
    -   <collection\>：集合名。
    -   <key\>：分片的键，MongoDB将根据该值进行数据分片。
    -   <value\>
        -   1：表示索引升序，通常能很好的支持基于 Shard Key 的范围查询。
        -   -1：表示索引降序，通常能很好的支持基于 Shard Key 的范围查询。
        -   hashed：表示使用Hash分片，通常能将写入均衡分布到各个 Shard 节点中。
    操作示例：

    ```
    sh.shardCollection("mongodbtest.customer",{"name":1})
    ```


如数据库中该集合拥有实际数据，等待后台的均衡器自动执行即可，该过程对用户透明。

## 后续操作 {#section_w5t_4jr_bgb .section}

经过一段时间的运行或数据写入后，您可以在Mongo Shell中执行`sh.status()`，查看数据分片信息和Shard上的块存储信息。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/78547/155228071034049_zh-CN.png)

您也可以通过执行`db.stats()`查看该数据库在各Shard节点的数据存储情况。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/78547/155228071033949_zh-CN.png)

