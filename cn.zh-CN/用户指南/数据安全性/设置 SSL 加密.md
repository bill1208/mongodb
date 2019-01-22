# 设置 SSL 加密 {#concept_v1g_vyv_y2b .concept}

为提高数据链路的安全性，您可以启用 SSL（Secure Sockets Layer）加密，并安装SSL CA证书到您的应用服务。通过 SSL 加密功能在传输层对网络连接进行加密，提升通信数据安全性的同时，保证数据的完整性。本章节介绍如何通过控制台查看 SSL 加密功能的详情、开通、更新、关闭SSL以及下载 SSL CA 证书。

## 注意事项 {#section_ztb_1zz_ggb .section}

-   目前仅3.4版本或4.0版本的副本集实例支持SSL加密功能。
-   在开通、更新和关闭SSL过程中，实例会重启一次，建议您在业务低峰期做以上操作。
-   SSL CA证书只能通过控制台下载。
-   由于SSL加密的固有缺陷，启用SSL加密会显著增加CPU使用率，建议您仅在外网链路有加密需求的时候启用SSL加密。内网链路相对较安全，一般无需对链路加密。

## 开通SSL加密 {#section_qcd_4dv_y2b .section}

**说明：** 开通SSL加密时，实例会重启一次，建议您在业务低峰期操作。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在页面左上角，选择实例所在的地域。
3.  在左侧导航栏，单击**副本集实例列表**。
4.  找到目标实例，单击实例ID。
5.  在左侧导航栏，选择**数据安全性** \> **SSL** 。
6.  在SSL区域框，打开**SSL状态**开关。
7.  在弹出的重启实例对话框，单击**确定**。

## 更新SSL证书有效期 {#section_tzm_dfv_y2b .section}

SSL证书的有效期为一年，超出有效期或者在有效期内，您都可以更新SSL证书。

**说明：** 更新SSL证书，实例会重启一次，建议您在业务低峰期操作。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在页面左上角，选择实例所在的地域。
3.  在左侧导航栏，单击**副本集实例列表**。
4.  找到目标实例，单击实例ID。
5.  在左侧导航栏，选择**数据安全性** \> **SSL** 。
6.  在SSL区域框，单击**更新证书**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/154814543710641_zh-CN.png)

7.  在弹出的重启实例对话框，单击**确定**。

## 下载SSL CA证书 {#section_ajh_sdv_y2b .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在页面左上角，选择实例所在的地域。
3.  在左侧导航栏，单击**副本集实例列表**。
4.  找到目标实例，单击实例ID。
5.  在左侧导航栏，选择**数据安全性** \> **SSL** 。
6.  单击**下载证书**，将CA证书下载至本地。

## 关闭SSL加密 {#section_rvt_jhv_y2b .section}

当您不需要SSL时，您可以关闭SSL加密。

**说明：** 关闭SSL加密时，实例会重启一次，建议您在业务低峰期操作。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在页面左上角，选择实例所在的地域。
3.  在左侧导航栏，单击**副本集实例列表**。
4.  找到目标实例，单击实例ID。
5.  在左侧导航栏，选择**数据安全性** \> **SSL** 。
6.  在SSL区域框，关闭**SSL状态**开关。
7.  在弹出的重启实例对话框，单击**确定**。

