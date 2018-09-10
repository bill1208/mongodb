# UpgradeDBInstanceKernelVersion {#reference_btz_3km_1fb .reference}

升级数据库小版本。

实例需满足以下条件，否则操作将失败。

-   实例类型为三节点副本集实例或者分片集群实例。
-   实例状态为运行中。

**说明：** 数据库小版本升级过程中，实例会被重启一次，实例重启过程中完成数据库小版本升级。建议您在业务低峰期升级数据库小版本。

## 请求参数 {#section_hs4_wtg_1fb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：UpgradeDBInstanceKernelVersion。

|
|DBInstanceId|String|是|实例ID。|

