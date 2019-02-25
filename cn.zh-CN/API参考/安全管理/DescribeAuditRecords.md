# DescribeAuditRecords {#reference_agk_3dw_kfb .reference}

该接口用于查询审计日志，同时支持副本集实例和集群版实例。

## 请求参数 {#section_h2l_nqw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeAuditRecords。|
|DBInstanceId|String|是|Sharding实例传入逻辑实例ID。|
|NodeId|String|否|Sharding可取值为每个mongos或者shard的ID，否则无结果返回副本集实例无需传入该值。|
|StartTime|String|是|查询开始时间，格式如：yyyy-MM-dd’T’HH:mm:ssZ。|
|EndTime|String|是|查询结束时间，格式如：yyyy-MM-dd’T’HH:mm:ssZ，且大于查询开始时间。|
|Database|String|否|默认为所有。|
|User|String|否|默认为所有。|
|Form|String|否| -   File，触发审计日志文件的生成，若传入这个值，只返回公共参数，需再调用DescribeSQLLogFiles接口获取文件的最终下载地址。
-   Stream，返回数据流，默认为Stream。

 |
|QueryKeywords|String|否|关键字查询，多个关键字以空格分隔，不超过10个关键字。|
|PageSize|Integer|否|每页记录数，取值：30/50/100，默认值：30。|
|PageNumber|Integer|否|页码，大于0，且不超过Integer的最大值，默认值：1。|

## 返回参数 {#section_jx1_krw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|TotalRecordCount|Integer|总记录数。|
|PageNumber|Integer|页码。|
|PageRecordCount|Integer|本页SQL日志明细个数。|
|Items|List<SQLRecord\>|SQL日志详情。|
|TotalRecordCount|Integer|总记录数。|

## SQLRecord参数 {#section_jrn_dsw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|DBName|String|数据库名称。|
|AccountName|String|总记录数。|
|HostAddress|String|客户端IP地址。|
|Syntax|String|执行语句。|
|TotalExecutionTimes|Long|消耗时间，单位：微秒。|
|ReturnRowCounts|Long|返回记录数。|
|ExecuteTime|String|执行时间，格式：yyyy-MM-dd’T’HH:mm:ssZ，如2011-05-30 T12:11:20Z。|
|ThreadID|String|线程ID。|

