# DescribeDBInstancePerformance {#reference_j4j_wbx_kfb .reference}

该接口用于查询实例性能数据，同时支持副本集实例和分片集群实例。

## 输入参数 {#section_pd3_bcx_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeDBInstancePerformance。|
|DBInstanceId|String|是|实例ID。|
|RoleID|String|否|实例类型为副本集实例可传入该参数，返回以RoleID的监控数据。|
|NodeId|String|否| -   Sharding实例类型时需要传入该参数，传入mongos或者shard节点的实例id，查询单个组件的性能情况。
-   单节点实例及副本集实例无需传入该值。

 |
|StartTime|String|是|查询开始时间格式：yyyy-MM-dd’T’HH:mmZ，如：2011-05-30T12:11Z时间格式：格林威志时间。|
|EndTime|String|是|查询结束时间格式：yyyy-MM-dd’T’HH:mmZ，如：2011-05-30T12:11Z时间格式：格林威志时间。|
|ReplicaSetRole|String|否| -   实例类型为副本集实例时，传入Primary节点或Secondary节点
-   单节点实例只能传入Primary节点

 |
|Key|String|是|性能指标，多个用英文半角“,”分隔，请参见[性能参数表](cn.zh-CN/API参考/附表/性能监控表.md#)。|

## 返回参数 {#section_a1r_4cx_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|DBInstanceId|String|实例ID。|
|Engine|String|数据库类型。|
|StartTime|String|查询开始时间，格式：YYYYMM-DD’T’HH:mmZ，如2011- 05-30T03:29Z。|
|EndTime|String|查询结束时间，格式：YYYYMM-DD’T’HH:mmZ，如2011- 05-30T03:29Z，大于查询开始时间。|
|PerformanceKeys|List<PerformanceKey\>|数组格式：\{perf1, perf2, perf3, …\}。|

## PerformanceKey参数 {#section_mw5_wcx_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|Key|String|性能参数。|
|Unit|String|展示单位。|
|ValueFormat|String|值格式：-   如果是null，则是 VALUE是一个最终值。
-   如果不是null，则需要解析VALUE，以 “&”分隔，如：com\_delete&com\_insert&com\_insert\_select&com\_replace

|
|Values|List<PerformanceValue\>|数组格式：\{value1, value2, …\}。|

## 性能参数值列表PerformanceValue {#section_uvq_ddx_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|Value|String|性能值。|
|Date|String|计算日期，格式：”yyyy-MMdd’T’HH:mm:ssZ”。如，2011- 05-30T03:29:00Z。|

