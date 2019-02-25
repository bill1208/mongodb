# DescribeParameters {#reference1216 .reference}

该接口用于查询当前实例参数信息。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeParameters。|
|DBInstanceId|String|是|实例名，集群传入逻辑实例名。|
|NodeId|String|否|集群子节点ID 可传入mongos id或shard id。|

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|Engine|String|数据库引擎,默认返回MongoDB。|
|EngineVersion|String|数据库版本号。|
|ConfigParameters|List<Parameter\>|当前运行的参数列表。|
|RunningParameters|List<Parameter\>|正在同步的参数列表。|

## Parameter参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|ParameterName|String|参数名。|
|ParameterValue|String|参数值。|
|ModifiableStatus|Boolean|参数是否可修改的状态： -   Flase：不可修改。
-   True：可修改。

 |
|ForceRestart|String|是否需要重启生效： -   Flase：无需重启，提交后即生效。
-   True：需要重启生效。

 |
|CheckingCode|String|校验代码，参数的可选范围。|
|ParameterDescription|String|参数描述。|

