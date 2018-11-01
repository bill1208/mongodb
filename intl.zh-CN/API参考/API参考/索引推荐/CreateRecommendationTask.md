# CreateRecommendationTask {#reference_wtr_ljt_qfb .reference}

该接口用于创建优化任务。

## 说明 {#section_ep2_5jt_qfb .section}

-   触发语句分析任务，下达触发任务后，可在可用时间范围中，看到对应的任务及状态。
-   若对应任务已经存在（生成成功后生成中，则创建失败，返回错误）。
-   每个实例每日最多可执行10次。

## 请求参数 {#section_q4y_jkt_qfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：CreateRecommendationTask。|
|InstanceId|String|是|实例ID。实例类型为分片集群实例时，传入其逻辑实例ID，而不是某个节点的实例ID。

|
|NodeId|String|否|分片集群实例中节点的ID，即某个Mongos节点或者Shard节点的ID。|
|StartTime|String|是|查询开始时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ。**说明：** StartTime要求大于审计日志的开启时间。

|
|EndTime|String|是|查询结束时间，精确到小时，格式如：yyyy-MM-dd’T’HHZ，时间范围为3天内。|

## 返回参数 {#section_cxh_4kt_qfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

