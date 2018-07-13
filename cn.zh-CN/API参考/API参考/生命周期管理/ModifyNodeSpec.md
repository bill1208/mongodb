# ModifyNodeSpec {#reference_epx_mhp_k2b .reference}

## 描述 {#section_idp_r44_k2b .section}

该接口用于变配集群版实例。

## 输入参数 {#section_k5t_t44_k2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：ModifyNodeSpec。|
|DBInstanceId|String|是|主实例的ID。|
|NodeId|String|是|子节点的ID。|
|NodeClass|String|是|子节点的规格。|
|NodeStorage|String|否|子节点的磁盘空间。当节点（主实例）为Shard时，需传入该参数。|
|ClientToken|String|否|Token，用于保证幂等性。|
|EffectiveTime|String|否|生效时间：-   Immediately：立即生效；
-   MaintainTime：实例可运维时间段内生效。

|

## 返回参数 {#section_m5j_w44_k2b .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

