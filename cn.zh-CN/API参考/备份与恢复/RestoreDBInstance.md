# RestoreDBInstance {#doc_api_Dds_RestoreDBInstance .reference}

调用RestoreDBInstance接口恢复数据至当前实例。

本接口仅适用于副本集实例，暂不支持单节点实例和分片集群实例。单节点实例可通过[从备份点新建实例](~~55013~~)克隆当前实例，分片集群实例可通过调用[CreateShardingDBInstance](~~61884~~)接口克隆当前实例。

**说明：** 调用该接口将覆盖当前实例的原有数据且无法恢复，请谨慎操作。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=RestoreDBInstance)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RestoreDBInstance|要执行的操作，取值：**RestoreDBInstance**。

 |
|BackupId|Integer|是|11111111|备份ID。

 **说明：** 您可以通过调用[DescribeBackups](~~62172~~)接口查询备份ID。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|973DCB8F-56B3-4102-8777-3A90495927F7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=RestoreDBInstance
&BackupId=11111111
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RestoreDBInstanceResponse>
  <RequestId>973DCB8F-56B3-4102-8777-3A90495927F7</RequestId>
</RestoreDBInstanceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"973DCB8F-56B3-4102-8777-3A90495927F7"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

