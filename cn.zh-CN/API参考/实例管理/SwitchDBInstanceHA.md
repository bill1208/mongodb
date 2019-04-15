# SwitchDBInstanceHA {#doc_api_Dds_SwitchDBInstanceHA .reference}

调用SwitchDBInstanceHA接口切换MongoDB实例中的主备节点。

调用本接口时，实例状态要求为运行中。

**说明：** 

 

-   本接口适用于副本集实例和分片集群实例，暂不支持单节点实例。

-   副本集实例以实例单位进行切换，分片集群实例以Shard为单位进行切换。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=SwitchDBInstanceHA)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SwitchDBInstanceHA|要执行的操作，取值：**SwitchDBInstanceHA**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|NodeId|String|否|d-bpxxxxxxxx|分片集群实例中Shard节点的ID。

 **说明：** 当**DBInstanceId**参数传入的是分片集群实例ID时，本参数必须传入。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|26BD4E5F-BDB4-47BA-B232-413AA78CFA8F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=SwitchDBInstanceHA
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SwitchDBInstanceHAResponse>
  <RequestId>26BD4E5F-BDB4-47BA-B232-413AA78CFA8F</RequestId>
</SwitchDBInstanceHAResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"26BD4E5F-BDB4-47BA-B232-413AA78CFA8F"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

