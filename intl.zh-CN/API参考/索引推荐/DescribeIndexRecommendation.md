# DescribeIndexRecommendation {#reference_kfm_t5s_qfb .reference}

可用于查询CloudDBA中索引推荐项目。

## 请求参数 {#section_kvj_42t_qfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeIndexRecommendation。|
|RegionId|String|是|实例所属地域ID，可通过DescribeRegions查询。|
|InstanceId|String|是|实例ID。实例类型为分片集群实例时，传入其逻辑实例ID，而不是某个节点的实例ID。

|
|NodeId|String|否|分片集群实例中节点的ID，即某个Mongos节点或者Shard节点的ID。|
|StartTime|String|是|查询开始时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ。**说明：** StartTime要求大于审计日志的开启时间。

|
|EndTime|String|是|查询结束时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ。|
|TaskId|String|是|任务ID,可通过DescribeAvailableTimeRange接口查获取。|
|Database|String|否|数据库名。|
|Collection|String|否|集合名。|
|OperationType|String|否|操作类型：query\\delete\\update等。|
|PageSize|Int|否|每页记录数，取值：30/50/100；默认值：30。|
|PageNumber|Int|否| 页码。

 大于0且不超过Integer的最大值；默认值：1。

 |

## 返回参数 {#section_mdz_4ft_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|TotalRecordCount|Int|总记录数。|
|PageNumber|Int|页码。|
|PageRecordCount|Int|该页记录数。|
|Analyzations|List|查询分析组成的数组。|

## Analyzation {#section_bnq_vgt_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|Database|​String|​数据库名。|
|Namespace|String|集合名。|
|Operation|String|操作类型：增删改查。|
|Query|String|查询命令。|
|Sort|String|排序命令。|
|IndexRecommendations|List<Recommendation\>|索引建议组成的数组。|
|IndexCombines|List<String\>|合并后的索引数组。|
|Count|Long|执行次数。|
|TotalExecutionTime|Long|总执行时间（毫秒）。|
|AverageExecutionTime|Long|平均执行时间（毫秒）。|
|AverageReturnRowCount|Long|平均返回行数。|
|AverageDocsExaminedCount|Long|平均文档扫描次数。|
|AverageKeysExaminedCount|Long|平均索引扫描次数。|
|InMemorySort|Boolean|是否使用内存查询。|
|LastExecutionTime|String|最近一次执行时间,精确到秒,格式如：yyyy-MM-dd’T’HH:mm:ssZ。|
|ExecutionPlan|String|查询的执行计划。|

## Recommendation {#section_abs_3ht_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RecmdType|String|建议的类型：Index/Refactor/WhereUse/NoRecommendation。|
|Content|String|建议的内容。|

