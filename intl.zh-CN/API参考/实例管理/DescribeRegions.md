# DescribeRegions {#doc_api_Dds_DescribeRegions .reference}

调用DescribeRegions接口查看MongoDB实例可用的地域和可用区。

调用[CreateDBInstance](~~61763~~)或[CreateShardingDBInstance](~~61884~~)接口创建实例之前，请先用本接口查询可用的地域和可用区信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Dds&api=DescribeRegions)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRegions|要执行的操作，取值： **DescribeRegions**。

 |
|AccessKeyId|String|否|LTAIgbTGpxxxxxx|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Regions| | |地域信息列表。

 |
|└RegionId|String|cn-qingdao|地域ID。

 **说明：** 地域ID对应的地域名称信息请参考[地域和可用区](~~40654~~)。

 |
|└Zones| | |可用区信息列表。

 |
|└VpcEnabled|Boolean|true|是否支持专有网络。

 |
|└ZoneId|String|cn-hangzhou-b|可用区ID。

 |
|RequestId|String|4E46C22C-D3B7-4DB8-9C76-63851BE68E20|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://mongodb.aliyuncs.com/?Action=DescribeRegions
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRegionsResponse>
  <RequestId>4E46C22C-D3B7-4DB8-9C76-63851BE68E20</RequestId>
  <Regions>
    <DdsRegion>
      <RegionId>cn-hangzhou</RegionId>
      <Zones>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-i</ZoneId>
        </Zone>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-b</ZoneId>
        </Zone>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-d</ZoneId>
        </Zone>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-f</ZoneId>
        </Zone>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-MAZ5(b,e,f)</ZoneId>
        </Zone>
        <Zone>
          <VpcEnabled>true</VpcEnabled>
          <ZoneId>cn-hangzhou-g</ZoneId>
        </Zone>
      </Zones>
    </DdsRegion>
  </Regions>
</DescribeRegionsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"4E46C22C-D3B7-4DB8-9C76-63851BE68E20",
	"Regions":{
		"DdsRegion":[
			{
				"RegionId":"cn-hangzhou",
				"Zones":{
					"Zone":[
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-i"
						},
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-b"
						},
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-d"
						},
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-f"
						},
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-MAZ5(b,e,f)"
						},
						{
							"VpcEnabled":true,
							"ZoneId":"cn-hangzhou-g"
						}
					]
				}
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dds)

