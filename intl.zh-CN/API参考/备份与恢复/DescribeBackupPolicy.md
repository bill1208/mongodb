# DescribeBackupPolicy {#reference_qxv_3vw_kfb .reference}

该接口用于查询备份测量，同时支持副本集和分片集群实例。

## 输入参数 {#section_lbn_pvw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeBackupPolicy。|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_kn3_5vw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|BackupRetentionPeriod|String|备份保留天数。|
|PreferredBackupTime|String|备份时间，格式：HH:mmZ- HH:mm Z。|
|PreferredBackupPeriod|String|备份周期：-   Monday：周一。
-   Tuesday：周二。
-   Wednesday：周三。
-   Thursday：周四。
-   Friday：周五。
-   Saturday：周六。
-   Sunday：周日。

|

