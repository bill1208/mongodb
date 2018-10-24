# DescribeShardingNetworkAddress {#reference1241 .reference}

该接口用于查询分片集群实例连接信息，仅支持分片集群实例。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeShardingNetworkAddress。|
|DBInstanceId|String|是|Sharding逻辑实例名。|
|NoId|String|否| -   传入sharding实例的mongos的ID。
-   若不传，则返回sharding下所有mongos的连接信息。

 |

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|-|
|NetworkAddresses|List<NetworkAddress\>|实例的连接地址信息。|

## NetworkAddress { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|NetworkAddress|String|DNS连接串。|
|IPAddress|String|IP地址。|
|NetworkType|String|网络类型：-   VPC：专有网络连接地址。
-   Classic：经典网络连接地址。
-   Public：公网连接地址。

|
|Port|String|端口|
|VPCId|String|VPC ID，VPC地址返回该信息。|
|VswitchId|String|Vswitch ID，VPC地址返回该信息。|
|NodeId|String|Sharding时返回所对应的节点ID\(mongos ID\)。|
|ExpiredTime|String|经典网络地址剩余时长，以秒为单位。|

