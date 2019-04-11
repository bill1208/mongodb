# CreateBackup {#doc_api_Dds_CreateBackup .reference}

调用CreateBackup接口手动备份MongoDB实例。

调用该接口时，要求实例状态为运行中。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=CreateBackup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateBackup|要执行的操作，取值： **CreateBackup**。

 |
|DBInstanceId|String|是|d-bpxxxxxxxx|实例ID。

 |
|BackupMethod|String|否|Logical|实例的备份方式，取值：

 -   **Logical**：逻辑备份。
-   **Physical**：物理备份，默认为物理备份。

 **说明：** 仅副本集和分片集群实例支持选择备份方式。单节点实例无需传入本参数，固定为快照备份。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BackupId|String|5664xxxx|备份ID。

 |
|RequestId|String|7016B12F-7F64-40A4-BAFF-013F02AC82FC|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=CreateBackup
DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateBackupResponse>
  <RequestId>7016B12F-7F64-40A4-BAFF-013F02AC82FC</RequestId>
  <BackupId>5664xxxx</BackupId>
</CreateBackupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"7016B12F-7F64-40A4-BAFF-013F02AC82FC",
	"BackupId":"5664xxxx"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

