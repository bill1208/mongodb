# MongoDB API的鉴权规则 {#concept_61757_zh .concept}

当子用户通过MongoDB Open API进行资源访问时，MongoDB后台向RAM进行权限检查，以确保调用者拥有响应权限。

每个不同的MongoDB API会根据涉及到的资源以及API的语义来确定需要检查哪些资源的权限。具体每个API的鉴权规则见下表。

|Action|鉴权规则|
|:-----|:---|
|CreateDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyDBInstanceSpec|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DeleteDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|RenewDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|CreateShardingDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DeleteNode|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|CreateNode|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyNodeSpec|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeDBInstances|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|RestartDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyDBInstanceMaintainTime|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyDBInstanceDescription|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeDBInstanceAttribute|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeReplicaSetRole|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeShardingNetworkAddress|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyDBInstanceNetworkType|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyDBInstanceNetExpireTime|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeDBInstancePerformance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeAccounts|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ResetAccountPassword|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeSecurityIps|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifySecurityIps|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeAuditRecords|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeAuditFiles|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeBackupPolicy|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|ModifyBackupPolicy|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|CreateBackup|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|RestoreDBInstance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeBackups|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|
|DescribeDBInstancePerformance|acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid|

