# ModifyAccountDescription {#reference_kjv_f3q_kfb .reference}

该接口用于修改账户备注。

## 输入参数 {#section_cmv_m3q_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ModifyAccountDescription。|
|DBInstanceId|String|是|实例名。|
|AccountName|String|是|操作帐号名。|
|AccountDescription|String|是|修改帐号备注。-   不能以`http://,https`开头。
-   以中文、英文字母开头。
-   可以包含中文、英文字符、”\_”，” -”，数字字符长度2~256个字符。

|

## 返回参数 {#section_usl_x3q_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

