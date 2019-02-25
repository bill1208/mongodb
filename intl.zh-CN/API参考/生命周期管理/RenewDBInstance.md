# RenewDBInstance {#reference_sz1_3zp_kfb .reference}

该接口用于实例的续费。

## 输入参数 {#section_zvd_kbq_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：RenewDBInstance。|
|DBInstanceId|String|是|实例ID。|
|Period|String|是|续费时长，取值为：1-9，12，24，36，单位：月。|
|ClientToken|String|是|用于保证幂等性。|

## 返回参数 {#section_nz1_tbq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|
|OrderId|String|订单ID。|

