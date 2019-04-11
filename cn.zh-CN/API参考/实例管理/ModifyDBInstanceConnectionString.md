# ModifyDBInstanceConnectionString {#doc_api_Dds_ModifyDBInstanceConnectionString .reference}

调用ModifyDBInstanceConnectionString接口修改实例的连接地址。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=ModifyDBInstanceConnectionString)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyDBInstanceConnectionString|要执行的操作，取值： **ModifyDBInstanceConnectionString**。

 |
|CurrentConnectionString|String|是|s-bpxxxxxxxx.mongodb.rds.aliyuncs.com|当前连接地址，即待修改的连接地址。

 |
|NewConnectionString|String|是|aliyuntest111|新的连接地址，以小写字母开头，由字母、数字组成，长度为8~64个字符。

 **说明：** 仅需传入连接地址的前缀部分，前缀以外的部分不可修改。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 **说明：** 当本参数传入的是分片集群实例ID时，还需要传入**NodeId**参数。

 |
|NodeId|String|否|s-bpxxxxxxxx|分片集群实例中的Mongos节点ID，每次调用仅能传入一个Mongos节点ID。

 **说明：** 当**DBInstanceId**参数传入的是分片集群实例ID时，本参数才可用。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|FF36A84C-0694-42D0-861D-C383E8E4FAAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=ModifyDBInstanceConnectionString
&CurrentConnectionString=s-bpxxxxxxxx.mongodb.rds.aliyuncs.com
&NewConnectionString=aliyuntest111
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyDBInstanceConnectionStringResponse>
  <RequestId>FF36A84C-0694-42D0-861D-C383E8E4FAAF</RequestId>
</ModifyDBInstanceConnectionStringResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"FF36A84C-0694-42D0-861D-C383E8E4FAAF"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

