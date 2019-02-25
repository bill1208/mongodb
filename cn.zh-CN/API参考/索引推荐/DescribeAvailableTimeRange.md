# DescribeAvailableTimeRange {#concept_drn_xlt_qfb .concept}

该接口用于查询可以离线查看索引优化建议的时间范围，并查询相应的报告生成状态。

## 说明 {#section_zmg_xmt_qfb .section}

您可通过CreateRecommendationTask接口创建3天内任意时间段（精确到小时）内的在线分析任务。分析完成后，自动将对应时间段内的结果转换为离线可查询数据。

默认生成最近3天的离线数据（每天24小时为一个生成单位）。

只返回大于审计日志的开启时间的任务列表。

## 请求参数 {#section_pjw_fmt_qfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeAvailableTimeRange。|
|InstanceId|String|是|实例ID。 实例类型为分片集群实例时，传入其逻辑实例ID，而不是某个节点的实例ID。

|
|NodeId|String|否|分片集群实例中节点的ID，即某个Mongos节点或者Shard节点的ID。|

## 返回参数 {#section_ifx_3mt_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|TimeRange|List<TimeRange\>|由时间范围组成的数组。|

## TimeRange {#section_jxt_kmt_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|StartTime|String|查询开始时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ。|
|EndTime|String|查询结束时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ。|
|Status|String|报告生成状态。-   Success:生成成功
-   Creating:生成中
-   Failure：生成失败

|
|NodeId|String|分片集群实例中节点的ID，即某个Mongos节点或者Shard节点的ID。|
|TaskId|String|任务ID。|

