# DescribeParameterModificationHistory {#reference1072 .reference}

查询当前实例参数修改历史信息。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeParameterModificationHistroy。|
|DBInstanceId|String|是|实例ID， 集群传入逻辑实例名。|
|NodeId|String|否|集群子实例ID，可传入mongos id或shard id。|
|StartTime|String|是|查询开始时间，格式yyyy-MM-dd’T’HH:mmZ。|
|EndTime|String|是|查询结束时间，格式yyyy-MM-dd’T’HH:mmZ。|

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|HistoricalParameters|List<HistoricalParameter\>|被修改的参数列表。|

## HistoricalParameter { .section}

|名称|类型|描述|
|:-|:-|:-|
|ParameterName|String|被修改的参数名。|
|ModifyTime|String|修改时间，UTC时间，精确到秒。|
|OldParameterValue|String|修改前的参数值。|
|NewParameterValue|String|修改后的参数值。|

