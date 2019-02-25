# DescribeParameterTemplates {#reference1287 .reference}

查询默认的参数模板列表。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeParameterTemplates。|
|RegionId|String|是|实例所在region|
|Engine|String|是|数据库类型|
|EngineVersion|String|是|数据库版本号|

## 返回参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|Engine|String|数据库类型|
|EngineVersion|String|数据库版本号|
|ParameterCount|String|参数个数|
|Parameters|List<TemplateRecord\>|参数列表|

## TemplateRecord参数 { .section}

|名称|类型|描述|
|:-|:-|:-|
|ParameterName|String|参数名。|
|ParameterValue|String|参数默认值。|
|ForceModify|String|参数是否可修改： -   Flase：不可修改。
-   True：可修改。

 |
|ForceRestart|String|是否需要重启生效： -   Flase：无需重启，提交后即生效。
-   True：需要重启生效。

 |
|CheckingCode|String|校验代码，参数的可选范围。|
|ParameterDescription|String|参数描述。|

