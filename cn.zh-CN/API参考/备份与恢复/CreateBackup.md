# CreateBackup {#reference_ox1_p22_l2b .reference}

为实例创建备份。

## 请求参数 {#section_ws2_vpc_l2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：CreateBackup。

|
|DBInstanceId|String|是|实例ID。|
|BackupMethod|String|否|实例的备份方式。-   Logical：逻辑备份；
-   Physical：物理备份，默认为物理备份。

|

## 返回参数 {#section_q42_tqc_l2b .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详情，请参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|BackupId|String|备份ID。|

