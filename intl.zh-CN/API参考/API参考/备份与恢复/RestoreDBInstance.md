# RestoreDBInstance {#reference_g3x_z1x_kfb .reference}

该接口用于数据恢复，仅支持副本集实例。

## 输入参数 {#section_nhk_jbx_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：RestoreDBInstance。|
|DBInstanceId|String|是|实例名，只支持副本集实例。|
|BackupId|String|是|备份ID。|

## 返回参数 {#section_ptw_4bx_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

