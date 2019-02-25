# SwitchDBInstanceHA {#reference573 .reference}

该接口用于切换MongoDB实例主备角色，支持副本集实例和分片集群实例。

## 说明 { .section}

-   单节点副本集不支持此功能。
-   切换MongoDB实例主备，primary与secondary角色进行互切。
-   副本集实例以实例单位进行切换，分片集群实例以每个Shard为单位去维护。
-   实例状态要求为运行中。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值为：SwitchDBInstanceHA。|
|DBInstanceId|String|是| -   副本集传入实例ID。
-   集群传入逻辑实例ID。

 |
|NodeId|String|否|集群Shard ID，若为集群模式，该参数必填。 nodeId只能是shardId|

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

