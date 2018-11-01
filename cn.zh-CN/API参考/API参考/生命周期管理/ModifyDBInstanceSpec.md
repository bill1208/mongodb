# ModifyDBInstanceSpec {#reference_hvc_4p4_k2b .reference}

## 描述 {#section_idp_r44_k2b .section}

该接口用于变配副本集实例。

## 输入参数 {#section_k5t_t44_k2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：ModifyDBInstanceSpec。|
|DBInstanceId|String|是|待变更配置实例的实例ID。|
|DBInstanceClass|String|否|实例规格，参数值请参见[实例规格表](intl.zh-CN/API参考/API参考/附表/实例规格表.md#)。|
|OrderType|String|否|变配类型：-   UPGRADE：升配；
-   DOWNGRADE：降配，默认为降配；
-   仅当实例付费方式为包年包月时需传入该值。

|
|DBInstanceStorage|Integer|否|自定义存储空间：-   取值范围：\[5,1000\]，每5G递增；
-   单位：GB。

|
|ReplicationFactor|String|否| 副本集节点个数。

-   可传入范围为：3，5，7
-   如不传入，则默认为3。

 |
|EffectiveTime|String|否|生效时间：-   Immediately：立即生效；
-   MaintainTime：可运维时间段内生效。

|

## 返回参数 {#section_m5j_w44_k2b .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|OrderId|String|订单ID。|

