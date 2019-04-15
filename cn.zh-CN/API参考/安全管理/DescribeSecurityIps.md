# DescribeSecurityIps {#doc_api_Dds_DescribeSecurityIps .reference}

调用DescribeSecurityIps接口查询MongoDB实例的IP白名单。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeSecurityIps)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSecurityIps|要执行的操作，取值：**DescribeSecurityIps**。

 |
|DBInstanceId|String|是|dds-bpxxxxxxxx|实例ID。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|SecurityIpGroups| | |IP白名单分组列表。

 |
|└SecurityIpGroupAttribute|String|hidden|IP白名单分组属性，默认为空。

 |
|└SecurityIpGroupName|String|default|分组名。

 |
|└SecurityIpList|String|47.xxx.xxx.xx,100.xxx.xxx.0/24|分组中包含的IP白名单列表。

 |
|SecurityIps|String|47.xxx.xxx.xx,100.xxx.xxx.0/24|默认分组中包含的IP白名单。

 |
|RequestId|String|FC724D23-2962-479E-ABB1-606C935AE7FD|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeSecurityIps
DBInstanceId=dds-bpxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSecurityIpsResponse>
  <SecurityIpGroups>
    <SecurityIpGroup>
      <SecurityIpList>114.xxx.xxx.xx</SecurityIpList>
      <SecurityIpGroupAttribute/>
      <SecurityIpGroupName>allowserver</SecurityIpGroupName>
    </SecurityIpGroup>
    <SecurityIpGroup>
      <SecurityIpList>47.xxx.xxx.xx,100.xxx.xxx.0/24</SecurityIpList>
      <SecurityIpGroupAttribute/>
      <SecurityIpGroupName>default</SecurityIpGroupName>
    </SecurityIpGroup>
  </SecurityIpGroups>
  <SecurityIps>47.xxx.xxx.xx,100.xxx.xxx.0/24</SecurityIps>
  <RequestId>FC724D23-2962-479E-ABB1-606C935AE7FD</RequestId>
</DescribeSecurityIpsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"SecurityIpGroups":{
		"SecurityIpGroup":[
			{
				"SecurityIpList":"114.xxx.xxx.xx",
				"SecurityIpGroupAttribute":"",
				"SecurityIpGroupName":"allowserver"
			},
			{
				"SecurityIpList":"47.xxx.xxx.xx,100.xxx.xxx.0/24",
				"SecurityIpGroupAttribute":"",
				"SecurityIpGroupName":"default"
			}
		]
	},
	"SecurityIps":"47.xxx.xxx.xx,100.xxx.xxx.0/24",
	"RequestId":"FC724D23-2962-479E-ABB1-606C935AE7FD"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

