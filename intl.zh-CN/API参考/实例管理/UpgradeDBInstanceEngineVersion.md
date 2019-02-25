# UpgradeDBInstanceEngineVersion {#reference_ycb_w5p_kfb .reference}

该接口用于升级引擎版本。

## 说明 {#section_v3w_z5p_kfb .section}

-   支持副本集和集群实例。
-   实例状态要求为运行中。
-   输入的数据库版本号必须大于当前实例的版本号。

## 请求参数 {#section_a1n_cvp_kfb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作，取值：UpgradeDBInstanceEngineVersion。|
|DBInstanceId|String|是|实例名，集群传入逻辑实例名。|
|EngineVersion|String|是|目标引擎版本，当前MongoDB仅支持升级至3.4。|

## 返回参数 {#section_djz_mvp_kfb .section}

|名称|类型|描述|
|:-|:-|:-|
|公共返回参数|-|详见[公共返回参数](cn.zh-CN/API参考/公共参数.md#)。|

