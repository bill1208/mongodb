# DescribeDBInstanceSSL {#reference_k41_12w_y2b .reference}

查看实例的SSL设置详情。

实例需满足以下条件，否则操作将失败。

-   实例类型为三节点副本集实例。
-   实例状态为运行中。

## 请求参数 {#section_jsh_1dw_y2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DescribeDBInstanceSSL。

|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_lyx_mdw_y2b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|详情，请参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|SSLExpireTime|String|SSL证书过期的时间。格式为：YYYY-MM-DD’T’hh:mm:ssZ。

|
|SSLStatus|String|SSL的启用状态。-   Open：SSL已开启；
-   Closed：SSL已关闭。

|

