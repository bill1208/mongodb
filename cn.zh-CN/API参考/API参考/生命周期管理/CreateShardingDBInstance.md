# CreateShardingDBInstance {#reference_glg_kkk_bfb .reference}

创建或者克隆分片集群实例。

## 请求参数 {#section_wyf_jbk_bfb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：CreateShardingDBInstance。

|
|RegionId|String|是|实例所属地域ID。可以通过接口DescribeRegions查看可用的地域ID。

|
|ZoneId|String|是|实例所属可用区ID。可以通过接口DescribeRegions查看可用的可用区ID。

|
|Engine|String|是|数据库类型，取值：MongoDB。

|
|StorageEngine|String|否|存储引擎，取值：WiredTiger或RocksDB。

默认值为WiredTiger。

|
|EngineVersion|String|是|数据库版本号，取值：3.2或3.4。

|
|DBInstanceDescription|String|否|实例的描述或备注信息。以中文或字母开头，可以包含中文、英文字符、下划线（\_）、连字符（-）和数字。长度为2~256个字符。

|
|Mongos.N.Class|String|是|mongos节点的规格。一个分片集群实例中mongos节点数量为2~32个。

详情，请参见[实例规格附表](https://help.aliyun.com/document_detail/57141.html)。

|
|ReplicaSet.N.Class|String|是|shard节点的规格。详情，请参见[实例规格附表](https://help.aliyun.com/document_detail/57141.html)。

个分片集群实例中shard节点数量为2~32个。

|
|ReplicaSet.N.Storage|Integer|是|分片集群实例中每个shard节点的存储空间。shard节点的存储空间大小为10~1000GB。

|
|ConfigServer.1.Class|String|是|CongfigServer的规格。configserver的规格配置固定为1核2GB。

|
|ConfigServer.1.Storage|Integer|是|ConfigServer的存储空间。configserver的存储空间固定为20GB。

|
|SecurityIPList|String|否|允许访问该实例下所有数据库的主机IP名单。若您需要添加多个IP地址或IP段，请用英文逗号隔开（逗号前后都不能有空格）。

**说明：** 若将白名单设置为%或者0.0.0.0/0，表示允许任何IP地址访问该MongoDB实例。该设置将极大降低数据库的安全性，如非必要请勿使用。

|
|AccountPassword|String|否|root账号密码。密码由字母、数字、特殊符号组成，长度为8~32位。特殊字符为英文感叹号（!）、（@）、井号（\#）、美元符号（$）、百分号（%）、（^）、（&）、星号（\*）、圆括号（\(\)）、下划线（\_）、加号（+）、连字符（-）、等号（=）。

|
|ChargeType|String|否|实例的付费类型。-   PrePaid：预付费，包年包月；
-   PostPaid：按量付费。默认值为PostPaid。

|
|ClientToken|String|是|用于保证请求的幂等性。由客户端生成该参数值，在不同请求间该参数值唯一，最大值不超过64个ASCII字符。

|
|NetworkType|String|否|实例的网络类型。-   CLASSIC：经典网络，默认值为CLASSIC；
-   VPC：VPC网络。

|
|VpcId|String|否|VPCID。实例网络类型为VPC时，该参数为必传参数。

|
|VSwitchId|String|否|VSwitchId。实例类型为VPC时，该参数为必传参数。

|
|SrcDBInstanceId|String|否|源实例ID。克隆分片集群实例时，需传入该参数。

|
|RestoreTime|String|否|7天内的一个任意时间点的UTC时间，精确到秒级。|

## 返回参数 {#section_pyz_2rk_bfb .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详情，请参见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

