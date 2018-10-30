# 已有MongoDB切换网络类型 {#concept_f3s_fys_2fb .concept}

云数据库MongoDB支持创建两种网络类型的实例：经典网络或者专有网络（Virtual Private Cloud）VPC类型的实例。通过MongoDB控制台或者API，您可以方便地在两种网络类型间进行切换。

-   经典网络：实例之间不通过网络进行隔离，只能依靠实例自身的白名单策略来阻挡非法访问。
-   VPC：一个VPC就是一个隔离的网络环境。VPC的安全性较高，我们推荐您使用VPC。

    您可以自定义VPC中的路由表、IP地址以及网关。此外，您还可以通过专线或者VPN的方式将自建机房与阿里云VPC内的云资源组合成一个虚拟机房，实现应用平滑上云。


通过API切换网络类型，请参见[ModifyDBInstanceNetworkType](../../../../intl.zh-CN/API参考/API参考/实例管理/ModifyDBInstanceNetworkType.md#)。

## 前提条件 {#section_nnp_1ws_2fb .section}

目前只有三节点副本集实例和分片集群实例支持切换网络类型，单节点实例暂不支持切换网络类型。

## 从经典网络切换为VPC {#section_tp1_1sl_2fb .section}

您可以在切换时选择保留经典网络，实现无闪断的平滑切换，请参见[经典网络平滑迁移到VPC的混访方案](intl.zh-CN/用户指南/网络类型/经典网络平滑迁移到VPC的混访方案.md#)。

1.  创建与MongoDB实例所在地域相同的VPC实例，请参见[创建专有网络](https://www.alibabacloud.com/help/zh/doc-detail/27710.htm)。
2.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
3.  在控制台左上方选择地域。
4.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6716/154086929612276_zh-CN.png)** \> **管理**。

5.  在实例基本信息页面，单击左侧导航栏中的**数据库连接**。
6.  在内网连接-经典网络页面，单击**切换为专有网络**。
7.  在打开的专有网络对话框中，选择**专有网络**和**交换机**。

    此处您可以选择**保留经典网络**，在生成新的VPC地址时，设置经典网络保留时长，保留现有经典网络地址，实现网络混访，在网络无闪断的情况下将经典网络平滑迁移到VPC上。经典网络到期后，其网络地址将自动释放。详情，请参见[经典网络平滑迁移到VPC的混访方案](intl.zh-CN/用户指南/网络类型/经典网络平滑迁移到VPC的混访方案.md#)。

    经典网络的保留时长可以设置为14天、30天、60天或者120天。在经典网络的保留时长内，可以过[修改经典网络到期时间](intl.zh-CN/用户指南/网络类型/修改经典网络到期时间.md#)，调整经典网络地址保留时长。

    若此处您选择不**保留经典网络**，在切换为VPC时，MongoDB服务会出现一次闪断，而且经典网络内的云产品（如ECS）将无法连接该MongoDB实例。请您尽量在业务低峰期执行切换操作，或确保您的应用有自动重连机制，以避免闪断造成的影响。

8.  单击**确定**，完成设置。

## 从VPC切换为经典网络 {#section_wjx_2yl_2fb .section}

切换为经典网络后，原VPC网络下的内网IP地址会被释放（原VPC中的ECS将不能再通过内网访问该MongoDB实例），MongoDB重新生成经典网络下的IP地址，外网IP不变，请注意变更应用端的连接地址。

1.  登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  在控制台左上方选择地域。
3.  单击目标实例ID。

    您也可以单击目标实例右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6716/154086929612276_zh-CN.png)** \> **管理**。

4.  在实例基本信息页面，单击左侧导航栏中的**数据库连接**。
5.  在内网连接-专有网络页面，单击**切换为经典网络**。
6.  在打开的切换为经典网络对话框中，单击**确定**。

    **说明：** 切换为经典网络后，VPC内的ECS将无法连接MongoDB实例。网络切换期间MonoDB服务会出现一次闪断，请您尽量在业务低峰期执行切换操作，或确保您的应用有自动重连机制，以避免闪断造成的影响。


