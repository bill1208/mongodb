# DescribeSlowLogRecords {#concept_i2s_jbj_wgb .concept}

用于查询数据库运行出现的慢操作日志明细，您可以根据时间段和数据库进行查询。该接口适用于副本集实例和分片集群实例。

## 输入参数 {#section_zzp_wbj_wgb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeSlowLogRecords。|
|StartTime|String|是| 查询开始时间。

 格式为*yyyy-MM-dd*T*HH:mm*Z，例如2011-05-30T12:10Z。

 |
|EndTime|String|是| 查询结束时间，必须晚于查询开始时间。

 格式为*yyyy-MM-dd*T*HH:mm*Z，例如2011-05-30T12:11Z。

 |
|DBInstanceId|String|是|实例ID。|
|NodeId|String|否| Shard节点ID。

 实例为分片集群实例时，该参数必传。

 |
|PageSize|Integer|是|每页记录数，取值：\[30-100\]|
|PageNumber|Integer|是|页码，大于0。|

## 返回参数 {#section_y5n_d2j_wgb .section}

|参数|类型|说明|
|:-|:-|:-|
|LogRecords|List|慢操作的日志明细，格式为\[sql1,sql2,sql3, …\]。|
|PageNumber|Integer|页码。|
|TotalRecordCount|Integer|总记录数。|
|Engine|String|数据库引擎，MongoDB。|
|PageRecordCount|Integer|总页数。|
|公共参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

## LogRecords {#section_a2k_f2j_wgb .section}

|参数|类型|说明|
|:-|:-|:-|
|ReturnRowCounts|Long|返回行数。|
|KeysExamined|Long|索引扫描行数。|
|HostAddress|String|用户连接数据库的主机地址。|
|SQLText|String|慢操作执行的语句。|
|ExecutionStartTime|String| 执行开始时间。

 格式为*yyyy-MM-dd*T*HH:mm:ss*Z，例如2011-05-30T12:11:20Z。

 |
|AccountName|String|执行该操作的数据库用户名。|
|QueryTimes|Long|执行时长，单位为毫秒。|
|DocsExamined|Long|文档扫描行数。|
|DBName|String|数据库名。|

