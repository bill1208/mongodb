# DescribeShardingNetworkAddress {#doc_api_Dds_DescribeShardingNetworkAddress .reference}

调用DescribeShardingNetworkAddress接口查询分片集群实例的连接信息。

该接口仅支持分片集群实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeShardingNetworkAddress)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeShardingNetworkAddress|要执行的操作，取值：**DescribeShardingNetworkAddress**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|NodeId|String|否|d-bpxxxxxxxx|分片集群实例中的Shard节点ID或Mongos节点ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NetworkAddresses| | |实例连接地址信息列表。

 |
|└ExpiredTime|String|2591963|保留的经典网络地址剩余时长，单位为秒。

 |
|└IPAddress|String|10.140.xxx.xx|IP地址。

 |
|└NetworkAddress|String|s-bpxxxxxxxx.mongodb.rds.aliyuncs.com|域名连接地址。

 |
|└NetworkType|String|VPC|网络类型。

 -   **VPC**：专有网络。
-   **Classic**：经典网络。
-   **Public**：公网。

 |
|└NodeId|String|s-bpxxxxxxxx|Mongos节点ID。

 |
|└Port|String|3717|连接端口。

 |
|└VPCId|String|vpc-bpxxxxxxxx|专有网络ID。

 **说明：** 当网络类型为**VPC**时返回该参数。

 |
|└VswitchId|String|vsw-bpxxxxxxxx|专有网络中交换机ID。

 **说明：** 当网络类型为**VPC**时返回该参数。

 |
|RequestId|String|18D8AAFD-6BEB-420F-8164-810CB0C0AA39|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeShardingNetworkAddress
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeShardingNetworkAddressResponse>
  <NetworkAddresses>
    <NetworkAddress>
      <NetworkType>VPC</NetworkType>
      <NodeId>s-bpxxxxxxxx</NodeId>
      <Port>3717</Port>
      <VPCId>vpc-bpxxxxxxxx</VPCId>
      <IPAddress>192.168.xxx.xx</IPAddress>
      <VswitchId>vsw-bpxxxxxxxx</VswitchId>
      <NetworkAddress>s-bp1xxxxxxxx.mongodb.rds.aliyuncs.com</NetworkAddress>
    </NetworkAddress>
    <NetworkAddress>
      <NetworkType>VPC</NetworkType>
      <NodeId>s-bpxxxxxxxx</NodeId>
      <Port>3717</Port>
      <VPCId>vpc-bpxxxxxxxx</VPCId>
      <IPAddress>192.168.xxx.xx</IPAddress>
      <VswitchId>vsw-bpxxxxxxxx</VswitchId>
      <NetworkAddress>s-bpxxxxxxxx.mongodb.rds.aliyuncs.com</NetworkAddress>
    </NetworkAddress>
  </NetworkAddresses>
  <RequestId>B4B78989-6D75-4930-BC26-635C3BB3A33B</RequestId>
</DescribeShardingNetworkAddressResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"NetworkAddresses":{
		"NetworkAddress":[
			{
				"NetworkType":"VPC",
				"Port":"3717",
				"NodeId":"s-bpxxxxxxxx",
				"VPCId":"vpc-bpxxxxxxxx",
				"IPAddress":"192.168.xxx.xx",
				"NetworkAddress":"s-bp1xxxxxxxx.mongodb.rds.aliyuncs.com",
				"VswitchId":"vsw-bpxxxxxxxx"
			},
			{
				"NetworkType":"VPC",
				"Port":"3717",
				"NodeId":"s-bpxxxxxxxx",
				"VPCId":"vpc-bpxxxxxxxx",
				"IPAddress":"192.168.xxx.xx",
				"NetworkAddress":"s-bpxxxxxxxx.mongodb.rds.aliyuncs.com",
				"VswitchId":"vsw-bpxxxxxxxx"
			}
		]
	},
	"RequestId":"B4B78989-6D75-4930-BC26-635C3BB3A33B"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

