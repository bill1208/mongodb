# DestroyInstance {#reference_w2s_m4c_l2b .reference}

## 描述 {#section_ctk_cpc_l2b .section}

该接口用于销毁MongoDB实例，要求实例状态为锁定中。

## 请求参数 {#section_ws2_vpc_l2b .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|系统规定参数，取值为：DestroyInstance。|
|InstanceId|String|是|实例的ID。|
|AccessKeyId|String|否|阿里云颁发给用户访问服务所用的密钥ID。|
|ClientToken|String|否|用于保证幂等性。|
|OwnerAccount|String|否|您登陆阿里云RDS管理控制台的主账号。|

## 返回参数 {#section_q42_tqc_l2b .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|请求ID。|

## 请求示例 {#section_f3z_vqc_l2b .section}

```
https://mongodb.aliyuncs.com/?Action=DestroyInstance
&amp;InstanceId=rdsaiiabnaiiabn
&amp;&lt;[公共请求参数]&gt;
```

## 返回示例 {#section_xhy_zqc_l2b .section}

**JSON格式**

```
{
"RequestId":" 65BDA532-28AF-4122-AA39-B382721EEE64"
}
```

