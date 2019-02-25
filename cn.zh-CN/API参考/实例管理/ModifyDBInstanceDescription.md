# ModifyDBInstanceDescription {#reference_vbk_1w4_kfb .reference}

该接口用于修改实例备注，同时支持副本集实例和分片集群实例。

## 输入参数 {#section_f5f_plp_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数，取值为：ModifyDBInstanceDescription。|
|DBInstanceId|String|是|实例名。|
|NodeId|String|否|实例类型为Shard时，传入mongos或者shard节点的实例id。|
|DBInstanceDescription|String|是| -   实例描述信息。
-   不能以`http://`，`https`开头。
-   以中文、英文字母开头。
-   可以包含中文、英文字符、”\_”，” -”，数字，字符长度2~256。

 |

## 返回参数 {#section_zt4_m54_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

