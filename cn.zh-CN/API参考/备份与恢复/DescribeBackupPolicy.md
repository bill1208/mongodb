# DescribeBackupPolicy {#doc_api_Dds_DescribeBackupPolicy .reference}

调用DescribeBackupPolicy接口查询MongoDB实例的备份策略。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeBackupPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBackupPolicy|要执行的操作，取值：**DescribeBackupPolicy**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BackupRetentionPeriod|String|7|备份保留天数。

 |
|PreferredBackupPeriod|String|Monday,Wednesday,Friday,Sunday|备份周期。

 -   **Monday**：周一。
-   **Tuesday**：周二。
-   **Thursday**：周四。
-   **Friday**：周五。
-   **Saturday**：周六。
-   **Sunday**：周日。

 |
|PreferredBackupTime|String|20:00Z-21:00Z|备份时间，格式为*HH:mm*Z-*HH:mm*Z。

 |
|RequestId|String|C2C283A1-1CC4-4DD9-B985-3811E0244A45|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeBackupPolicy
DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeBackupPolicyResponse>
  <PreferredBackupPeriod>Monday,Wednesday,Friday,Sunday</PreferredBackupPeriod>
  <RequestId>C2C283A1-1CC4-4DD9-B985-3811E0244A45</RequestId>
  <PreferredBackupTime>20:00Z-21:00Z</PreferredBackupTime>
  <BackupRetentionPeriod>7</BackupRetentionPeriod>
</DescribeBackupPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PreferredBackupPeriod":"Monday,Wednesday,Friday,Sunday",
	"RequestId":"C2C283A1-1CC4-4DD9-B985-3811E0244A45",
	"BackupRetentionPeriod":"7",
	"PreferredBackupTime":"20:00Z-21:00Z"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

