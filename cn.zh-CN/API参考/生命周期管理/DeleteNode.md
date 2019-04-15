# DeleteNode {#doc_api_Dds_DeleteNode .reference}

调用DeleteNode接口删除MongoDB分片集群实例中的Shard节点或Mongos节点。

调用本接口时，实例必须满足以下条件：

-   实例状态为运行中。
-   实例类型为分片集群实例。
-   实例付费类型为按量付费。
-   实例中Shard节点或Mongos节点的数量必须大于2。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DeleteNode)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteNode|要执行的操作，取值：**DeleteNode**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|NodeId|String|是|s-bpxxxxxxxx|待删除的Shard节点ID或Mongos节点ID，您可以通过[DescribeDBInstanceAttribute](~~61923~~)接口查询节点ID。

 |
|ClientToken|String|否|ETnLKlblzczshOTUbOCzxxxxxxxxxx|用于保证请求的幂等性，防止重复提交请求。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符，且该参数值中不能包含非ASCII字符。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9F9BDE64-BF30-41F3-BD29-C19CE4AB3404|请求ID。

 |
|TaskId|Integer|111111111|任务ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DeleteNode
&NodeId=s-bpxxxxxxxx
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteNodeResponse>
  <RequestId>9F9BDE64-BF30-41F3-BD29-C19CE4AB3404</RequestId>
  <TaskId>111111111</TaskId>
</DeleteNodeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9F9BDE64-BF30-41F3-BD29-C19CE4AB3404",
	"TaskId":111111111
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

