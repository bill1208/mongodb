# ResetAccountPassword {#reference_rlp_42q_kfb .reference}

该接口用于实例的数据库密码。

## 输入参数 {#section_nxf_sfq_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ResetAccountPassword。|
|DBInstanceId|String|是|实例ID。|
|AccountName|String|是|帐号名。|
|AccountPassword|String|是|新密码，由字母、数字或下划线组成，长度为6~32个字符。|

## 返回参数 {#section_vmd_ngq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

