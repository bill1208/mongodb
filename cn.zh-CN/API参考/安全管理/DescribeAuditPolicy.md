# DescribeAuditPolicy {#doc_api_Dds_DescribeAuditPolicy .reference}

调用DescribeAuditPolicy接口查询实例的审计日志是否开启。

调用本接口时，要求实例状态为运行中。

**说明：** 本接口适用于副本集实例和分片集群实例，暂不支持单节点实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeAuditPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAuditPolicy|要执行的操作，取值： **DescribeAuditPolicy**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LogAuditStatus|String|Enable|审计日志的状态。

 -   Enable：开启。
-   Disabled：关闭。

 默认为关闭状态。

 |
|RequestId|String|111E7B16-0A87-4CBA-B271-F34AD61E099F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeAuditPolicy
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAuditPolicyResponse>
  <LogAuditStatus>Enable</LogAuditStatus>
  <RequestId>111E7B16-0A87-4CBA-B271-F34AD61E099F</RequestId>
</DescribeAuditPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"LogAuditStatus":"Enable",
	"RequestId":"111E7B16-0A87-4CBA-B271-F34AD61E099F"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

