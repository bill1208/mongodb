# DescribeSecurityIps {#reference_pk5_hcw_kfb .reference}

该接口用于查询实例白名单。

## 输入参数 {#section_wj1_lcw_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：DescribeSecurityIps。|
|DBInstanceId|String|是|实例ID。|

## 返回参数 {#section_fdb_tcw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|
|SecurityIps|String|默认白名单。|
|SecurityIpGroups|List<SecurityIpGroup\>|分组白名单。|

## SecurityIpGroup {#section_pxm_zcw_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|SecurityIpGroupName|String|分组名。|
|SecurityIpList|String|IP列表。|
|SecurityIpAttribute|String|分组属性，默认不展示hidden属性的分组。|

