# AllocatePublicNetworkAddress {#doc_api_Dds_AllocatePublicNetworkAddress .reference}

调用AllocatePublicNetworkAddress接口为MongoDB实例申请公网连接地址。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=AllocatePublicNetworkAddress)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 **说明：** 当本参数传入的是分片集群实例ID时，还需要传入**NodeId**参数。

 |
|Action|String|否|AllocatePublicNetworkAddress|要执行的操作，取值：**AllocatePublicNetworkAddress**。

 |
|NodeId|String|否|s-bpxxxxxxxx|分片集群实例中Mongos节点ID。

 **说明：** 当**DBInstanceId**传入的是分片集群实例ID时，本参数才可用。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B6D17591-B48B-4D31-9CD6-9B9796B2270A|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=AllocatePublicNetworkAddress
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AllocatePublicNetworkAddressResponse>
  <RequestId>B6D17591-B48B-4D31-9CD6-9B9796B2270A</RequestId>
</AllocatePublicNetworkAddressResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"B6D17591-B48B-4D31-9CD6-9B9796B2270A"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

