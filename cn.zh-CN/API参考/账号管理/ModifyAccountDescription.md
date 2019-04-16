# ModifyAccountDescription {#doc_api_Dds_ModifyAccountDescription .reference}

调用ModifyAccountDescription接口修改MongoDB实例中root账号的备注信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=ModifyAccountDescription)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyAccountDescription|要执行的操作，取值：**ModifyAccountDescription**。

 |
|AccountName|String|是|root|待修改备注信息的账号名。

 |
|AccountDescription|String|是|superadmin|设置账号的备注信息。

 -   不能以http:// 或者 https:// 开头。
-   以中文、英文字母开头。
-   可以包含中文、英文字符、下划线（\_）、连接号（-）和数字，长度为2~256个字符。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|59DE9FC2-7B40-45CF-9011-7327A8A771A2|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=ModifyAccountDescription
&AccountName=root
&AccountDescription=superadmin
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RestoreDBInstanceResponse>
  <RequestId>59DE9FC2-7B40-45CF-9011-7327A8A771A2</RequestId>
</RestoreDBInstanceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"59DE9FC2-7B40-45CF-9011-7327A8A771A2"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

