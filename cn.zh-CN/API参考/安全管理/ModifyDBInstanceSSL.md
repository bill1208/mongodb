# ModifyDBInstanceSSL {#doc_api_Dds_ModifyDBInstanceSSL .reference}

调用ModifyDBInstanceSSL接口修改SSL配置。

调用该接口时，实例必须满足以下条件：

-   实例状态为运行中。
-   实例类型为副本集实例。
-   实例的数据库版本为3.4或4.0版本。

**说明：** 在开通、更新和关闭SSL过程中，实例会重启一次，建议您在业务低峰期操作。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=ModifyDBInstanceSSL)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyDBInstanceSSL|要执行的操作，取值： **ModifyDBInstanceSSL**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|SSLAction|String|是|Open|对SSL功能执行的操作，取值：

 -   **Open**：开启SSL加密。
-   **Close**：关闭SSL加密。
-   **Update**：更新SSL证书。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6D806B11-078F-4154-BF9F-844F56D08964|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=ModifyDBInstanceSSL
&DBInstanceId=dds-bpxxxxxxxx
&SSLAction=Open
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyDBInstanceSSLResponse>
  <RequestId>6D806B11-078F-4154-BF9F-844F56D08964</RequestId>
</ModifyDBInstanceSSLResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"6D806B11-078F-4154-BF9F-844F56D08964"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|IncorrectDBInstanceState|Current DB instance state does not support this operation.|实例状态不支持此操作，请您检查输入的参数是否正确。|
|403|IncorrectDBInstanceLockMode|Current DB instance lock mode does not support this operation.|实例已经被锁定。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

