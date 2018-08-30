# SSL加密 {#concept_v1g_vyv_y2b .concept}

为提高数据链路的安全性，您可以启用SSL（Secure Sockets Layer）加密，并安装SSL CA证书到您的应用服务。

SSL在传输层对网络连接进行加密，提升通信数据安全性的同时，保证数据的完整性。

关于SSL的设置（查看SSL设置详情、开通SSL、更新SSL、关闭SSL），您可以通过控制台或者API [DescribeDBInstanceSSL](../../../../intl.zh-CN/API参考/API参考/安全管理/DescribeDBInstanceSSL.md#)、[ModifyDBInstanceSSL](../../../../intl.zh-CN/API参考/API参考/安全管理/ModifyDBInstanceSSL.md#)操作。SSL CA证书只能通过控制台来下载。本章节介绍如何通过控制台查看SSL详情、开通、更新、关闭SSL以及下载SSL CA证书。

**说明：** 

-   目前仅副本集实例支持SSL加密。
-   在开通、更新、下载以及关闭SSL过程中，实例会重启一次，建议您在业务低峰期做以上操作。

## 开通SSL {#section_qcd_4dv_y2b .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在控制台左上方选择地域。
3.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153410641_zh-CN.png)** \> **管理** 。

4.  在实例基本信息页面，单击左侧导航栏中的**数据安全性** \> **SSL** 。
5.  在SSL页面，单击**未开通**旁边的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153410646_zh-CN.png)。
6.  在打开的重启实例对话框中，单击**确定**。

    **说明：** 开通SSL加密时，实例会重启一次，建议您在业务低峰期开通SSL。


## 更新SSL证书有效期 {#section_tzm_dfv_y2b .section}

SSL证书的有效期为一年，过了有效期或者在有效期内，您都可以更新SSL证书。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在控制台左上方选择地域。
3.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153410641_zh-CN.png)** \> **管理** 。

4.  在实例基本信息页面，单击左侧导航栏中的**数据安全性** \> **SSL** 。
5.  在SSL页面，单击**更新证书**。
6.  在打开的重启实例对话框中，单击**确定**。

    **说明：** 更新过程中，实例会重启一次，建议您在业务低峰期更新SSL证书。


## 下载SSL CA证书 {#section_ajh_sdv_y2b .section}

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在控制台左上方选择地域。
3.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153410641_zh-CN.png)** \> **管理** 。

4.  在实例基本信息页面，单击左侧导航栏中的**数据安全性** \> **SSL** 。
5.  在SSL页面，单击**下载证书**，将CA证书下载至本地。

## 关闭SSL {#section_rvt_jhv_y2b .section}

当您不需要SSL时，您可以关闭SSL证书。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在控制台左上方选择地域。
3.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153410641_zh-CN.png)** \> **管理** 。

4.  在实例基本信息页面，单击左侧导航栏中的**数据安全性** \> **SSL** 。
5.  在SSL页面，单击**已开通**旁边的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18857/153560153510648_zh-CN.png)。
6.  在打开的重启实例对话框中，单击**确定**。

    **说明：** 关闭SSL加密时，实例会重启一次，建议您在业务低峰期关闭SSL。


## 相关文档 {#section_e3t_kkw_y2b .section}

[MongoDB客户端SSL连接示例](intl.zh-CN/用户指南/安全/MongoDB客户端SSL连接示例.md#)

