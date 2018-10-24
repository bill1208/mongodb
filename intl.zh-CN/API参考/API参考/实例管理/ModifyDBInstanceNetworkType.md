# ModifyDBInstanceNetworkType {#reference894 .reference}

切换实例的网络类型。

目前只有三节点副本集实例和分片集群实例支持切换网络类型，单节点实例暂不支持切换网络类型。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：ModifyDBInstanceNetworkType。

|
|DBInstanceId|String|是|实例ID。|
|NetworkType|String|是|实例要切换的目标网络类型。-   VPC：将网络类型切换为VPC；
-   Classic：将网络类型切换为经典网络。

|
|RetainClassic|String|否|切换网络类型为VPC时，设置是否保留原经典网络地址。-   True：保留原经典网络地址；
-   False：不保留原经典网络地址。

|
|ClassicExpiredDays|Integer|否|切换网络类型为VPC，且RetainClassic=True时，设置保留原经典网络地址的时长。 经典网络的保留时长可以设置为14天、30天、60天或者120天。

|
|VpcId|String|否|VPC Id 从经典网络切换至VPC时，该参数为必传参数。

|
|VSwitchId|String|否|Vswitch Id 从经典网络切换至VPC时，该参数为必传参数。

|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|公共返回参数|-|详情，请参见[公共参数](intl.zh-CN/API参考/API参考/公共参数.md#)。|

