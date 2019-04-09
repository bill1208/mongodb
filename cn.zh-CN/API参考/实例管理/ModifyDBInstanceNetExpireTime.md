# ModifyDBInstanceNetExpireTime {#doc_api_Dds_ModifyDBInstanceNetExpireTime .reference}

调用ModifyDBInstanceNetExpireTime接口延长经典网络保留时长。

调用该接口时实例须满足以下条件：

-   实例状态处于运行中。
-   实例的网络处于混访模式。

**说明：** 本接口适用于副本集实例和分片集群实例，暂不支持单节点实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=ModifyDBInstanceNetExpireTime)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyDBInstanceNetExpireTime|要执行的操作，取值：**ModifyDBInstanceNetExpireTime**。

 |
|ClassicExpendExpiredDays|Integer|是|30|设置保留原经典网络地址的时长，取值：**14**、**30**、**60**、**120**，单位为天。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|ConnectionString|String|否|dds-bpxxxxxxxx.mongodb.rds.aliyuncs.com|实例的连接地址。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|459E7D5C-38DA-4E14-9C82-5B5AF693DBAB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=ModifyDBInstanceNetExpireTime
&ClassicExpendExpiredDays=30
&DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyDBInstanceNetExpireTimeResponse>
  <RequestId>459E7D5C-38DA-4E14-9C82-5B5AF693DBAB</RequestId>
</ModifyDBInstanceNetExpireTimeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"459E7D5C-38DA-4E14-9C82-5B5AF693DBAB"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

