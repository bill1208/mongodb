# API概览 {#reference_gwx_tss_l2b .reference}

本文汇总了云数据库 MongoDB 所有可调用 API，具体接口信息请参阅相关文档。

您可以通过 [OpenAPI Explorer](https://help.aliyun.com/document_detail/74407.html) 可视化地调用云数据库 MongoDB 开放的 API ，查看 API 请求和返回结果。此外， OpenAPI Explorer 会自动生成相应 API 的 SDK 调用示例代码，帮助您快速了解并使用云数据库 MongoDB 的 API 。

## 生命周期管理 {#section_xrj_kts_l2b .section}

|API|描述|
|---|--|
|[CreateDBInstance](cn.zh-CN/API参考/生命周期管理/CreateDBInstance.md#)|创建副本集实例|
|[ModifyDBInstanceSpec](cn.zh-CN/API参考/生命周期管理/ModifyDBInstanceSpec.md#)|变配副本集实例|
|[DeleteDBInstance](cn.zh-CN/API参考/生命周期管理/DeleteDBInstance.md#)|释放实例|
|[RenewDBInstance](cn.zh-CN/API参考/生命周期管理/RenewDBInstance.md#)|续费副本集实例|
|[CreateShardingDBInstance](cn.zh-CN/API参考/生命周期管理/CreateShardingDBInstance.md#)|创建分片集群实例|
|[CreateNode](cn.zh-CN/API参考/生命周期管理/CreateNode.md#)|新增集群实例组件|
|[DeleteNode](cn.zh-CN/API参考/生命周期管理/DeleteNode.md#)|删除集群实例组件|
|[ModifyNodeSpec](cn.zh-CN/API参考/生命周期管理/ModifyNodeSpec.md#)|集群实例变配|

## 实例管理 {#section_ndz_lts_l2b .section}

|API|描述|
|---|--|
|[DescribeRegions](cn.zh-CN/API参考/实例管理/DescribeRegions.md#)|查询可用地域列表|
|[DescribeDBInstances](cn.zh-CN/API参考/实例管理/DescribeDBInstances.md#)|查询实例列表|
|[RestartDBInstance](cn.zh-CN/API参考/实例管理/RestartDBInstance.md#)|重启实例|
|[ModifyDBInstanceMaintainTime](cn.zh-CN/API参考/实例管理/ModifyDBInstanceMaintainTime.md#)|修改实例可维护时间|
|[ModifyDBInstanceDescription](cn.zh-CN/API参考/实例管理/ModifyDBInstanceDescription.md#)|修改实例备注|
|[DescribeDBInstanceAttribute](cn.zh-CN/API参考/实例管理/DescribeDBInstanceAttribute.md#)|查询实例详情|
|[DescribeReplicaSetRole](cn.zh-CN/API参考/实例管理/DescribeReplicaSetRole.md#)|查询复制集角色及连接信息|
|[DescribeShardingNetworkAddress](cn.zh-CN/API参考/实例管理/DescribeShardingNetworkAddress.md#)|查询分片集群连接信息|
|[ModifyDBInstanceNetworkType](cn.zh-CN/API参考/实例管理/ModifyDBInstanceNetworkType.md#)|切换实例类型|
|[ModifyDBInstanceNetExpireTime](cn.zh-CN/API参考/实例管理/ModifyDBInstanceNetExpireTime.md#)|延长经典网络保留时长|
|[SwitchDBInstanceHA](cn.zh-CN/API参考/实例管理/SwitchDBInstanceHA.md#)|MongoDB实例主备切换|
|[AllocatePublicNetworkAddress](cn.zh-CN/API参考/实例管理/AllocatePublicNetworkAddress.md#)|申请公网连接地址|
|[ReleasePublicNetworkAddress](cn.zh-CN/API参考/实例管理/ReleasePublicNetworkAddress.md#)|释放公网连接地址|
|[ModifyDBInstanceConnectionString](cn.zh-CN/API参考/实例管理/ModifyDBInstanceConnectionString.md#)|修改实例连接地址|
|[UpgradeDBInstanceEngineVersion](cn.zh-CN/API参考/实例管理/UpgradeDBInstanceEngineVersion.md#)|升级引擎版本|
|[UpgradeDBInstanceKernelVersion](cn.zh-CN/API参考/实例管理/UpgradeDBInstanceKernelVersion.md#)|升级数据库小版本|
|[DescribeKernelReleaseNotes](cn.zh-CN/API参考/实例管理/DescribeKernelReleaseNotes.md#)|查询数据库小版本发布日志|
|[DestroyInstance](cn.zh-CN/API参考/实例管理/DestroyInstance.md#)|销毁MongoDB实例|

## 账号管理 {#section_ggn_rts_l2b .section}

|API|描述|
|---|--|
|[DescribeAccounts](cn.zh-CN/API参考/账号管理/DescribeAccounts.md#)|查询账号|
|[ResetAccountPassword](cn.zh-CN/API参考/账号管理/ResetAccountPassword.md#)|重置密码|
|[ModifyAccountDescription](cn.zh-CN/API参考/账号管理/ModifyAccountDescription.md#)|修改账户备注|

## 数据库安全管理 {#section_r1v_sts_l2b .section}

|API|描述|
|---|--|
|[DescribeSecurityIps](cn.zh-CN/API参考/安全管理/DescribeSecurityIps.md#)|查询实例访问白名单|
|[ModifySecurityIps](cn.zh-CN/API参考/安全管理/ModifySecurityIps.md#)|修改实例访问白名单|
|[DescribeAuditRecords](cn.zh-CN/API参考/安全管理/DescribeAuditRecords.md#)|查询审计日志|
|[DescribeAuditFiles](cn.zh-CN/API参考/安全管理/DescribeAuditFiles.md#)|查询审计日志文件|
|[DescribeAuditPolicy](cn.zh-CN/API参考/安全管理/DescribeAuditPolicy.md#)|查询审计日志开通状态及日志保存时间|
|[DescribeAuditLogFilter](cn.zh-CN/API参考/安全管理/DescribeAuditLogFilter.md#)|查询审计日志的采集类型|
|[ModifyAuditLogFilter](cn.zh-CN/API参考/安全管理/ModifyAuditLogFilter.md#)|设置审计日志的采集类型|
|[ModifyDBInstanceSSL](cn.zh-CN/API参考/安全管理/ModifyDBInstanceSSL.md#)|为实例设置SSL加密|
|[DescribeDBInstanceSSL](cn.zh-CN/API参考/安全管理/DescribeDBInstanceSSL.md#)|查询实例的SSL设置详情|

## 备份与恢复 {#section_kdg_5ts_l2b .section}

|API|描述|
|---|--|
|[DescribeBackupPolicy](cn.zh-CN/API参考/备份与恢复/DescribeBackupPolicy.md#)|查看备份策略|
|[ModifyBackupPolicy](cn.zh-CN/API参考/备份与恢复/ModifyBackupPolicy.md#)|修改备份策略|
|[CreateBackup](cn.zh-CN/API参考/备份与恢复/CreateBackup.md#)|创建备份|
|[DescribeBackups](cn.zh-CN/API参考/备份与恢复/DescribeBackups.md#)|查看备份列表|
|[RestoreDBInstance](cn.zh-CN/API参考/备份与恢复/RestoreDBInstance.md#)|数据恢复|

## 监控报警管理 {#section_qjs_vts_l2b .section}

|API|描述|
|---|--|
|[DescribeDBInstancePerformance](cn.zh-CN/API参考/性能监控管理/DescribeDBInstancePerformance.md#)|查询实例性能数据|

## 参数管理 {#section_l21_xts_l2b .section}

|API|描述|
|---|--|
|[DescribeParameters](cn.zh-CN/API参考/参数管理/DescribeParameters.md#)|查询参数信息|
|[ModifyParameters](cn.zh-CN/API参考/参数管理/ModifyParameters.md#)|修改参数信息|
|[DescribeParameterModificationHistory](cn.zh-CN/API参考/参数管理/DescribeParameterModificationHistory.md#)|查询参数历史修改信息|
|[DescribeParameterTemplates](cn.zh-CN/API参考/参数管理/DescribeParameterTemplates.md#)|查看参数模板列表|

## 相关文档 {#section_rfg_yts_l2b .section}

-   [API资源导航](https://developer.aliyun.com/)
-   [API Explorer](https://api.aliyun.com/)
-   [API错误中心](https://error-center.aliyun.com/)

