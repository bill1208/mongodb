# ModifyBackupPolicy {#reference_onj_3ww_kfb .reference}

该接口用于修改备份策略，同时支持副本集实例和分片集群实例。

## 输入参数 {#section_u14_fxw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifyBackupPolicy。|
|DBInstanceId|String|是|实例ID。|
|PreferredBackupTime|String|是|备份时间，格式：HH:mmZ-HH:mmZ。|
|PreferredBackupPeriod|String|是|备份周期：-   Monday：周一。
-   Tuesday：周二。
-   Wednesday：周三。
-   Thursday：周四。
-   Friday：周五。
-   Saturday：周六。
-   Sunday：周日。

|

## 返回参数 {#section_dlc_zxw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

