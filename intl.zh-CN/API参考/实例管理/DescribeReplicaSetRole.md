# DescribeReplicaSetRole {#doc_api_Dds_DescribeReplicaSetRole .reference}

调用DescribeReplicaSetRole接口查询MongoDB实例中的角色信息及连接信息。

本接口适用于副本集实例和单节点实例，不适用于分片集群实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeReplicaSetRole)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeReplicaSetRole|要执行的操作，取值：**DescribeReplicaSetRole**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DB4A0595-FCA9-437F-B2BB-25DBFC009D3E|请求ID。

 |
|DBInstanceId|String|dds-bpxxxxxxxx|实例ID。

 |
|ReplicaSets| | |副本集角色信息列表。

 |
|└ConnectionDomain|String|dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com|节点的连接地址。

 |
|└ConnectionPort|String|3717|节点的连接端口。

 |
|└ExpiredTime|String|1209582|保留的经典网络地址剩余时长，单位为秒。

 |
|└NetworkType|String|VPC|网络类型。

 -   **VPC**：专有网络。
-   **Classic**：经典网络。
-   **Public**：公网。

 |
|└ReplicaSetRole|String|Primary|该节点在副本集中的角色。

 -   **Primary**：主节点。
-   **Secondary**：从节点。

 |
|└RoleId|String|651xxxxx|节点的角色ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeReplicaSetRole
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeReplicaSetRoleResponse>
  <RequestId>7762D0FF-F34D-4DAF-9D06-6C1C28CC98CD</RequestId>
  <DBInstanceId>dds-bpxxxxxxxx</DBInstanceId>
  <ReplicaSets>
    <ReplicaSet>
      <NetworkType>Classic</NetworkType>
      <ConnectionPort>3717</ConnectionPort>
      <ReplicaSetRole>Primary</ReplicaSetRole>
      <ConnectionDomain>dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com</ConnectionDomain>
      <ExpiredTime>12xxxxx</ExpiredTime>
      <RoleId>55xxxxx</RoleId>
    </ReplicaSet>
    <ReplicaSet>
      <NetworkType>Classic</NetworkType>
      <ConnectionPort>3717</ConnectionPort>
      <ReplicaSetRole>Secondary</ReplicaSetRole>
      <ConnectionDomain>dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com</ConnectionDomain>
      <ExpiredTime>12xxxxx</ExpiredTime>
      <RoleId>55xxxxx</RoleId>
    </ReplicaSet>
    <ReplicaSet>
      <NetworkType>VPC</NetworkType>
      <ConnectionPort>3717</ConnectionPort>
      <ReplicaSetRole>Primary</ReplicaSetRole>
      <ConnectionDomain>dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com</ConnectionDomain>
      <RoleId>55xxxxx</RoleId>
    </ReplicaSet>
    <ReplicaSet>
      <NetworkType>VPC</NetworkType>
      <ConnectionPort>3717</ConnectionPort>
      <ReplicaSetRole>Secondary</ReplicaSetRole>
      <ConnectionDomain>dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com</ConnectionDomain>
      <RoleId>55xxxxx</RoleId>
    </ReplicaSet>
  </ReplicaSets>
</DescribeReplicaSetRoleResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ReplicaSets":{
		"ReplicaSet":[
			{
				"NetworkType":"Classic",
				"ConnectionPort":"3717",
				"ReplicaSetRole":"Primary",
				"ConnectionDomain":"dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com",
				"ExpiredTime":"12xxxxx",
				"RoleId":"55xxxxx"
			},
			{
				"NetworkType":"Classic",
				"ConnectionPort":"3717",
				"ReplicaSetRole":"Secondary",
				"ConnectionDomain":"dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com",
				"ExpiredTime":"12xxxxx",
				"RoleId":"55xxxxx"
			},
			{
				"NetworkType":"VPC",
				"ConnectionPort":"3717",
				"ReplicaSetRole":"Primary",
				"ConnectionDomain":"dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com",
				"RoleId":"55xxxxx"
			},
			{
				"NetworkType":"VPC",
				"ConnectionPort":"3717",
				"ReplicaSetRole":"Secondary",
				"ConnectionDomain":"dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com",
				"RoleId":"55xxxxx"
			}
		]
	},
	"DBInstanceId":"dds-bpxxxxxxxx",
	"RequestId":"7762D0FF-F34D-4DAF-9D06-6C1C28CC98CD"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

