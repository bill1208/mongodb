# DeleteDBInstance {#doc_api_1159100 .reference}

调用DeleteDBInstance接口释放实例。

调用该接口时，实例必须满足以下条件。

-   实例状态为运行中；
-   实例付费类型为按量付费。

**说明：** 实例释放后数据将无法找回，请谨慎操作。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DeleteDBInstance)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteDBInstance|要执行的操作，取值**DeleteDBInstance**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|ClientToken|String|否|ETnLKlblzczshOTUbOCzxxxxxxxxxx|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符，且该参数值中不能包含非ASCII字符。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|72651AF9-7897-41A7-8B67-6C15C7F26A0A|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DeleteDBInstance
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteDBInstanceResponse>
  <RequestId>72651AF9-7897-41A7-8B67-6C15C7F26A0A</RequestId>
</DeleteDBInstanceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"72651AF9-7897-41A7-8B67-6C15C7F26A0A"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

