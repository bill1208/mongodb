# CreateDBInstance {#reference2375 .reference}

该接口用于创建副本集实例，同时也用于创建克隆实例。

## 输入参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值为CreateDBInstance。|
|RegionId|String|是| -   地域ID，长度不超过50个字符。
-   通过函数DescribeRegions查看可用的地域ID。

 |
|ZoneId|String|否|可用区id，通过函数DescribeRegions查看可用的可用区。|
|Engine|String|是|数据库类型，取值为MongoDB。|
|EngineVersion|String|是|数据库版本号，取值为3.2、3.4或4.0。|
|StorageEngine|String|否|存储引擎，取值为WiredTiger或RocksDB，默认值为WiredTiger。克隆实例时，该值只能与主实例保持一致。|
|ReplicationFactor|String|否| 副本集节点个数。

 -   可传入范围为：3，5，7
-   默认值为3

 |
|DBInstanceClass|String|是|实例规格，可选值：见[实例规格表](cn.zh-CN/API参考/附表/实例规格表.md#)。|
|DBInstanceStorage|Integer|是| -   自定义存储空间，取值范围：\[10,2000\]。
-   每10GB进行递增，单位：GB。

 |
|DBInstanceDescription|String|否|实例的描述或备注信息，长度为\[2，256\]个字符。以中文、英文字母开头，可以包含中文、英文字符、”\_”、”-”和数字。|
|SecurityIPList|String|否| -   允许访问该实例下所有数据库的IP名单，以逗号隔开，不可重复，可添加IP数量最多1000个。
-   支持格式：%，0.0.0.0/0，10.23.12.24（IP），或者10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1，32\]）其中，0.0.0.0/0表示不限制。默认不限制

 |
|AccountPassword|String|否| root账号密码。

 -   密码由大写、小写、数字、特殊字符中的任意三种组成，特殊字符为!\#$%^&\*\(\)\_+-=
-   密码长度为8-32位。

 |
|ChargeType|String|否|付费类型：PrePaid和PostPaid，分别表是包年包月和按量付费。默认值：PostPaid。|
|Period|Integer|否|包年包月到期时间，ChargeTtype为PrePaid时必传，取值范围为：1-9，12，24，36，单位：月。|
|ClientToken|String|是|用于保证请求的幂等性，由客户端生成该参数值，且在不同请求间该参数值唯一，最大值不超过64个ASCII字符。 具体参见附录：如何保证幂等性。|
|NetworkType |String|否|实例的网络类型。 取值：CLASSIC或VPC 默认值：CLASSIC。|
|VpcId|String|否|专有网络（VPC）ID。如果NetworkType参数为VPC，则该参数为必须参数。|
|VSwitchId|String|否|虚拟交换机ID。如果NetworkType参数为VPC，则该参数为必须参数。|
|DBInstanceId|String|否|基于一个实例的备份集创建付费实例，指定该实例的ID。|
|BackupId|String|否|具体的备份集Id。|
|RestoreTime|String|否|克隆实例时所恢复的时间点。|

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|DBInstanceId|String|实例ID。|
|OrderId|String|订单ID。|

