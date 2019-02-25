# ModifyParameters {#reference_dpk_smx_kfb .reference}

修改实例的参数信息。

## 说明 {#section_tsf_ymx_kfb .section}

修改当前实例参数信息，实例需满足以下状态，否则将调用失败：

-   当前实例状态：使用中。
-   当前实例锁定模式：正常。

若所提交的修改参数中，有需要重启才能生效的参数，则提交后将自动进行实例重启。

## 请求参数 {#section_o1h_cnx_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifyParameters。|
|DBInstanceId|String|是|实例名，集群传入逻辑实例名。|
|NodeId|String|否|集群子实例ID可传入mongos id或shard id，当实例类型为Sharding时，该参数必传。|
|Parameters|String|是|所修改的参数的Json串\{“name”:”value”,”name”:”value2”\}。|

## 返回参数 {#section_jrc_jnx_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

