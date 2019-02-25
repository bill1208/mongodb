# ModifyAuditLogFilter {#reference_bjh_yxn_y2b .reference}

设置审计日志的采集类型。

实例需满足以下条件，否则操作将失败。

-   实例类型为三节点副本集实例。
-   实例状态为运行中。

## 请求参数 {#section_rjh_yvn_y2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：ModifyAuditLogFilter。

|
|DBInstanceId|String|是|实例ID。|
|Filter|String|是|采集类型。实例类型为三副本集实例时，可传入以下采集类型。

-   admin：运维管控操作；
-   slow：慢日志；
-   query：查询操作；
-   insert：插入操作；
-   update：更新操作；
-   delete：删除操作；
-   command：协议命令。例如，aggregate聚合方法等。

|

## 返回参数 {#section_gwg_sxn_y2b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详情，请参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|

