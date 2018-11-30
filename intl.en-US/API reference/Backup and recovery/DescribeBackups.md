# DescribeBackups {#reference_e3p_2yw_kfb .reference}

You can call this operation to view the backup list. This operation supports both replica set instances and sharded cluster instances.

## Request parameters {#section_rr1_5yw_kfb .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Set the value toDescribeBackups.|
|DBInstanceId|String|Yes|The ID of the instance.|
|StartTime|String|Yes|The start time of the time frame specified for querying backups. Format: 2011-06-11T15:00Z.|
|EndTime|String|Yes|The end time of the time frame specified for querying backups. It must be later than the start time. Format: 2011-06-11T16:00Z.|
|BackupId|Integer|No|The ID of the backup.|
|NodeId|String|No|This parameter is required when the instance type is cluster. It specifies the ID of the shard that you want to query.|
|PageSize|Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumberds|Integer|No|The page number. It must be greater than 0 and smaller than or equal to the maximum value of Integer. Default value: 1.|

## Response parameters {#section_ckh_xzw_kfb .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|Common response parameters|-|For more information, see [Common response parameters](https://www.alibabacloud.com/help/doc-detail/61711.htm).|
|Items|List<Backup\>|Array composed of backups.|
|PageNumber|Integer|The number of the page.|
|TotalCount|Integer|The total number of backups.|
|PageSize|Integer  |The number of records on each page.|

## Backup data structure {#section_lsv_21x_kfb .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|BackupId|Integer|The ID of the backup.|
|BackupStatus|String|The status of the backup:-   Success: The backup process is complete.
-   Failed: The backup process has failed.

|
|BackupStartTime|String|The start time of the backup process. Format: YYYY-MM-DD’T’hh:mm:ssZ.|
|BackupEndTime|String|The end time of the backup process. Format: YYYYMM-DD’T’hh:mm:ssZ.|
|BackupType|String|The following backup types are available:-   FullBackup: Full backup.
-   IncrementalBackup: Incremental backup.

|
|BackupMode|String|The following backup modes are available:-   Automated: Automatic backup.
-   Manual: Manual backup.

|
|BackupMethod|String|The following backup methods are available:-   Snapshot: Create a snapshot.
-   Physical: Create a physical backup.

|
|BackupDownloadURL|String|The download URL of the backup. If the backup cannot be downloaded, this parameter is set to an empty string.|
|BackupSize|Long|The size of the backup file. Unit: Bytes.|

