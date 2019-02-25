# ModifyDBInstanceSSL {#reference_bcw_qbw_y2b .reference}

为实例设置SSL加密。

实例需满足以下条件，否则操作将失败。

-   实例类型为三节点副本集实例。
-   实例状态为运行中。

**说明：** 在开通、更新以及关闭SSL过程中，实例会重启一次，建议您在业务低峰期做以上操作。

## 请求参数 {#section_fpt_41w_y2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：ModifyDBInstanceSSL。

|
|DBInstanceId|String|是|实例ID。|
|SSLAction|String|是|设置SSL。可进行以下三种设置。-   Open：开启SSL加密；
-   Close：关闭SSL加密；
-   Update：更新SSL证书。

|

## 返回参数 {#section_stp_lbw_y2b .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>| |详情，请参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|

