# DescribeKernelReleaseNotes {#reference_ncy_lqn_1fb .reference}

查询数据库小版本发布日志。

实例类型为三节点副本集实例或者分片集群实例，否则操作将失败。

## 请求参数 {#section_r5w_yqn_1fb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DescribeKernelReleaseNotes。

|
|KernelVersion|String|否|小版本号。格式如mongodb\_20171116\_0.4.7。

不传该参数，返回所有版本的小版本号列表。

传入该参数，返回大于该版本的小版本号列表。

|

## 返回参数 {#section_gtt_trn_1fb .section}

|名称|类型|描述|
|--|--|--|
|ReleaseNotes|List|由版本号和发布日志组成的数组。|

**ReleaseNotes**

|名称|类型|描述|
|--|--|--|
|KernelVersion|String|版本号。|
|ReleaseNote|String|发布日志。|

