# ReleasePublicNetworkAddress {#reference_oz4_4tr_gfb .reference}

该接口用于释放公网连接地址。

## 请求参数 {#section_rzp_5tr_gfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：ReleasePublicNetworkAddress。|
|DBInstanceId|String|是|实例ID。|
|NodeId|String|否|分片集群实例Mongos节点的ID。-   实例类型为分片集群实例则该值为必须。
-   实例类型为副本集实例则该值不可使用。

|

## 返回参数 {#section_yym_v4q_gfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

