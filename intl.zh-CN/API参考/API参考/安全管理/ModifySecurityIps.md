# ModifySecurityIps {#reference_bcl_x1w_kfb .reference}

该接口用于修改实例白名单。

## 输入参数 {#section_llj_bbw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifySecurityIps。|
|DBInstanceId|String|是|实例ID。|
|SecurityIps|String|是|IP白名单分组下的IP列表，最多允许添加1000个IP地址，以逗号隔开，格式如下：0.0.0.0/0，10.23.12.24（IP）。|
|ModifyMode|String|否|修改方式，取值：-   Cover：覆盖原白名单，默认值。
-   Append：追加白名单。
-   Delete：删除该白名单。

|
|SecurityIpGroupName|String|否|所修改的分组的名，默认为default分组。|
|SecurityIpGroupAttribute|String|否|分组属性，不传则不修改返回参数。|

## 返回参数 {#section_q2c_pbw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

