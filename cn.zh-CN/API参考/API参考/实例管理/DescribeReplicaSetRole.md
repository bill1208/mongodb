# DescribeReplicaSetRole {#reference_frb_xmp_kfb .reference}

该接口用于查询副本集角色及连接信息，仅支持副本集实例。

## 输入参数 {#section_zgj_bnp_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeReplicaSetRole。|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_n5r_5np_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|DBInstanceId|String|实例ID。|
|ReplicaSets|List<ReplicaSet\>|复制集角色列表。|

## ReplicaSetRole数据结构 {#section_enq_14p_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|ReplicaSetRole|String|复制集角色：Primary或Secondary。|
|RoleId|String|角色ID，用于唯一表示角色为Secondary的各个子节点。|
|ConnectionDomain|String|实例连接域名。|
|ConnectionPort|String|实例连接端口。|
|ExpiredTime String|String|经典网络地址剩余时长，以秒为单位。|
|NetworkType|String|网络类型-   VPC：专有网络。
-   Classic：经典网络。
-   Public：公网。

|

