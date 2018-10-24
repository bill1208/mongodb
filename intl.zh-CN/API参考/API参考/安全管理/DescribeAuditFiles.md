# DescribeAuditFiles {#reference_u5l_vsw_kfb .reference}

该接口用于查询审计文件，仅支持副本集实例。

## 请求参数 {#section_um2_2tw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeAuditFiles。|
|DBInstanceId|String|是|主实例名。|
|NodeId|String|否| -   Sharding可传入Mongos ID或shard ID不传则显示全部。
-   副本集无需传入。

 |

## 返回参数 {#section_jyh_4tw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页记录数。|
|Items|List<LogFile\>|由审计文件组成的数组。|

## LogFile参数 {#section_jjx_ttw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|FileID|Interger|文件ID。|
|DBInstanceId|String|实例名。|
|LogStatus String|String| -   Success：归档完成。
-   Failed：归档失败。
-   Generating：归档中。
-   Initializing：未开始。

 |
|LogStartTime|String|审计日志起始时间。|
|LogEndTime|String|审计日志结束时间。|
|LogDownloadURL|String|下载链接的地址。若当前不可下载，则为空串。|
|LogSize|Long|日志文件大小，单位：Byte。|

