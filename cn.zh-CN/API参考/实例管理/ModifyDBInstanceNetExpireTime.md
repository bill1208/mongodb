# ModifyDBInstanceNetExpireTime {#reference_xyk_xd4_4fb .reference}

该接口用于延长经典网络保留时长，同时支持副本集实例和分片集群实例。

## 请求参数 {#section_jf5_c24_4fb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifyDBInstanceNetExpireTime。|
|DBInstanceId|String|是|实例ID。|
|ConnectionString|String|是|连接串。|
|ClassicExpendExpiredDays|Integer|是|保留天数。|

## 返回参数 {#section_qpr_sdq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

