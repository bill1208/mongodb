# CreateNode {#reference_rfp_kcq_kfb .reference}

该接口用于新增集群实例组件，仅支持分片集群实例。

## 输入参数 {#section_ssb_rcq_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：CreateNode。|
|DBInstanceId|String|是|实例ID，主实例的ID。|
|NodeClass|String|是|Node的规格。|
|NodeStorage|String|否|Node的磁盘空间，当实例类型为Shard时，该参数为必传参数。|
|NodeType|String|否|Node的类型，Mongos或Shard。|
|ClientToken|String|是|用于保证幂等性。|

## 返回参数 {#section_qpr_sdq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

