# ModifyDBInstanceMaintainTime {#reference_z1w_kj4_k2b .reference}

## 描述 {#section_h4x_1k4_k2b .section}

该接口用于修改实例可维护时间。

## 请求参数 {#section_f4k_3k4_k2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：ModifyDBInstanceMaintainTime。|
|DBInstanceId|String|是|实例ID。|
|MaintainStartTime|String|是|实例可运维时间段的开始时间，格式：HH:mmZ。|
|MaintainEndTime|String|是|实例可运维时间段的结束时间，格式：HH:mmZ。**说明：** 开始时间-结束时间范围为1小时，如：MaintainStartTime：01:00Z，MaintainEndTime：02:00Z。

|

## 返回参数 {#section_fkq_5k4_k2b .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|

