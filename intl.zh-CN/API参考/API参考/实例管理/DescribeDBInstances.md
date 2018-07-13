# DescribeDBInstances {#reference_mzq_pyw_k2b .reference}

## 描述 {#section_pjs_nww_k2b .section}

该接口用于查询实例列表。

## 请求参数 {#section_gqn_tww_k2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：DescribeDBInstances。|
|RegionId|String|是|实例所属地域ID，通过函数DescribeRegions查看。|
|Engine|String|否|数据库类型，取值为MongoDB。|
|DBInstanceType|String|否|实例类型，取值如下：-   sharding：分片集群实例；
-   replicate：副本集实例，默认值为replicate。

|
|PageSize|Integer|否|每页记录数，取值：-   30，默认值为30；
-   50；
-   100。

|
|PageNumber|Integer|否|页码，取值为大于0且不超过Integer数据类型的的最大值，默认值为1。|

## 返回参数 {#section_ffw_dxw_k2b .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数| |详见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|DBInstances|List<DBInstance\>|由DBInstance组成的数组。|
|DestroyTime |String|实例数据销毁时间：-   包年包月实例释放8天后，数据彻底销毁，且不可找回。
-   按量付费实例，自欠费日起，实例锁定24小时后将被释放，释放同时数据将全部销毁。

 |
|LockMode |String|实例的锁定状态。取值范围如下：-   Unlock：正常；
-   ManualLock：手动触发锁定；
-   LockByExpiration：实例过期自动锁定；
-   LockByRestoration：实例回滚前自动锁定；
-   LockByDiskQuota：实例空间满自动锁定；
-   Released：实例已释放。此时实例无法进行解锁，只能使用备份数据重新创建新实例，重建时间较长，请耐心等待。

|

## DBInstance数据结构 {#section_ick_h4x_k2b .section}

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|实例ID。|
|ReplicationFactor|String|副本集实例节点个数：-   1：单节点；
-   3：三节点。

|
|DBInstanceDescription|String|实例描述。|
|RegionId|String|实例所属地域ID。|
|ZoneId|String|实例所属可用区ID。|
|Engine|String|数据库类型。|
|EngineVersion|String|数据库版本。|
|DBInstanceClass|String|实例规格。|
|DBInstanceStorage|Integer|实例存储空间。|
|DBInstanceStatus|String|实例状态，参见[实例状态表](https://www.alibabacloud.com/help/zh/doc-detail/63870.htm)。|
|ChargeType|String|实例付费类型：-   PrePaid：预付费，包年包月；
-   PostPaid：按量付费。

|
|NetworkType|String|实例网络类型：-   Classic：经典网络；
-   VPC：VPC网络。

|
|CreationTime|String|实例创建时间，格式：YYYY-MM-DDThh:mm:ssZ，如2011-05-30T12:11:4Z。|
|ExpireTime|String|实例到期时间。|
|DBInstanceType|String|实例类型，取值如下：-   sharding：分片集群实例；
-   replicate：副本集实例，默认值为replicate。

|
|MongosList|List<Mongos\>|由Mongos组成的数组。|
|ShardList|List<Shard\>|由Shard组成的数组。|
|LastDowngradeTime|Integer|实例最后一次降配时间。|

## Mongos {#section_ymg_hqx_k2b .section}

|名称|类型|描述|
|--|--|--|
|NodeId|String|Mongos的实例ID。|
|NodeDescription|String|Mongos的实例描述。|
|NodeClass|String|Mongos的实例规格。|

## Shard {#section_tgd_lqx_k2b .section}

|名称|类型|描述|
|--|--|--|
|NodeId|String|Shard的实例ID。|
|NodeDescription|String|Shard的实例描述。|
|NodeClass|String|Shard的实例规格。|
|NodeStorage|Integer|Shard的实例磁盘。|

