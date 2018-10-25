# DescribeAuditPolicy {#reference_j5z_ktn_y2b .reference}

查询审计日志是否开通，以及审计日志的保存时间。

实例需满足以下条件，否则查询操作将失败。

-   实例类型为副本集实例或者分片集群实例。
-   实例状态为运行中。

## 请求参数 {#section_kvq_kln_y2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是| 要执行的操作，取值：

 DescribeAuditPolicy。

 |
|DBInstanceId|String|是| 实例ID。

 |

## 返回参数 {#section_tgn_xrn_y2b .section}

|名称|类型|描述|
|<公共返回参数\>|-|详情，请参见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)|
|LogAuditStatus|String| 审计日志的状态。

 -   Enable：开启；
-   Disabled：关闭，默认为关闭状态。

 |
|StoragePeriod|Int| 审计日志的存储时间。

 审计日志为开启状态时，返回该参数。

 审计日志为关闭状态时，该参数不返回。

 |

