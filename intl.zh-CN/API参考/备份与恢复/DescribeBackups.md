# DescribeBackups {#reference_e3p_2yw_kfb .reference}

该接口用于查看备份列表，同时支持副本集实例和分片集群实例。

## 输入参数 {#section_rr1_5yw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeBackups。|
|DBInstanceId|String|是|实例ID。|
|StartTime|String|是|查询开始时间，格式如：2011-06-11T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2011-06-11T16:00Z，且大于查询开始时间。|
|BackupId|Integer|否|备份ID。|
|NodeId|String|否|实例类型为集群版时此参数为必须，传入shard节点的实例ID。|
|PageSize|Integer|否|每页记录数，取值：30/50/100默认值：30。|
|PageNumberds|Integer|否|页码，大于0，且不超过Integer的最大值，默认值：1。|

## 返回参数 {#section_ckh_xzw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|Items|List<Backup\>|由Backup组成的数组。|
|PageNumber|Integer|页码。|
|TotalCount|Integer|备份总个数。|
|PageSize|Integer|每页记录数。|

## Backup数据结构 {#section_lsv_21x_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|BackupId|Integer|备份ID。|
|BackupStatus|String|备份状态：-   Success：完成备份。
-   Failed：备份失败。

|
|BackupStartTime|String|本次备份开始时间，格式为YYYY-MM-DD’T’hh:mm:ssZ。|
|BackupEndTime|String|本次备份结束时间，格式为YYYYMM-DD’T’hh:mm:ssZ。|
|BackupType|String|备份类型：-   FullBackup：全量备份。
-   IncrementalBackup：增量备份。

|
|BackupMode|String|备份模式：-   Automated：系统自动备份。
-   Manual：手动备份。

|
|BackupMethod|String|备份方法：-   Snapshot：快照备份。
-   Physical：物理备份。

|
|BackupDownloadURL|String|下载链接的地址，若当前不可下载，则为空串。|
|BackupSize|Long|备份文件大小，单位：Byte。|

