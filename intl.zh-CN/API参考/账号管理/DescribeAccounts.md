# DescribeAccounts {#reference_q3m_qgq_kfb .reference}

该接口用于查询实例的数据库账号。

## 输入参数 {#section_kqp_vgq_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数，取值为：DescribeAccounts。|
|DBInstanceId|String|是|实例ID。|
|AccountName|String|是|账号名。|

## 返回参数 {#section_smb_dhq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|Accounts|List<Account\>|由Account组成的数组。|

## Account数据结构 {#section_h4k_phq_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|DBInstanceId|String|帐号所属实例名称。|
|AccountName|String|账号名称。|
|AccountStatus|String|帐号状态：-   Unavailable：不可用。
-   Available：可用。

|
|AccountDescription|String|账号备注信息。|

