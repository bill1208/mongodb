# DescribeRegions {#reference_ans_qt4_kfb .reference}

该接口用于查询可用地域列表，同时支持副本集实例和分片集群实例。

## 输入参数 {#section_hpy_5t4_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数，取值DescribeRegions。|
|RegionId|String|否|RegionId。|
|ZoneId|String|否|可用区。|

## 返回参数 {#section_zt4_m54_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

## Region数据结构 {#section_xm4_p54_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RegionId|String|地域Id，如:cn-beijing。|
|Zones|List<Zones\>|可用区信息。|

## Zones {#section_c1p_z54_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|ZoneId|String|可用区Id，如:cn-beijing-a。|
|VpcEnabled|String|是否支持VPC。|

