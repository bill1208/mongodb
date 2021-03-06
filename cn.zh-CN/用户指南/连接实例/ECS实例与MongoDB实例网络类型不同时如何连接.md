# ECS实例与MongoDB实例网络类型不同时如何连接 {#concept_pqx_xcv_hhb .concept}

当ECS实例是经典网络而MongoDB实例是专有网络（VPC），或者MongDB实例是经典网络而ECS实例是专有网络，您可根据本文中的办法快速实现不同网络类型的ECS实例连接至MongoDB实例的需求。

## 前提条件 {#section_jjc_ml5_hhb .section}

-   ECS实例和MongoDB实例在同一阿里云账号中，且属于同一地域。
-   已将ECS实例的IP地址加入MongoDB实例的白名单中，详情请参考[设置白名单](cn.zh-CN/用户指南/数据安全性/设置白名单.md#)。

    **说明：** 关于获取ECS实例IP地址信息，请参考[如何查询ECS实例的IP地址](https://help.aliyun.com/knowledge_detail/40637.html#section-vpl-qbg-qgb)。


## 经典网络的ECS实例连接专有网络的MongoDB实例 {#section_nty_b25_hhb .section}

![经典网络的ECS连接专有网络的MongoDB](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/154587/155477262543423_zh-CN.png)

通过下述三种方法均可以实现经典网络的ECS实例连接专有网络的MongoDB实例，您可以根据业务规划自行选择。

-   将ECS实例迁移至MongoDB实例所属的专有网络中，详情请参考[将ECS实例迁移至专有网络](https://help.aliyun.com/document_detail/57954.html)。
-   将MongoDB实例的网络类型切换为经典网络，详情请参考[从专有网络切换为经典网络](cn.zh-CN/用户指南/管理网络连接/切换实例网络类型.md#section_wjx_2yl_2fb)。
-   使用[ClassicLink](https://help.aliyun.com/document_detail/65412.html)实现互通。

    **说明：** 基于ClassicLink互访方案为特殊情况下的临时解决方案，生产环境中为了实现高速连接，建议您将ECS实例和MongoDB实例创建在同一VPC网络内。

    在建立ClassicLink前确保您已经了解建立连接的限制，详情请参见[ClassicLink概述](https://help.aliyun.com/document_detail/65412.html)。

    **开启ClassicLink操作步骤：**

    1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/)。
    2.  选择目标专有网络的地域，然后单击目标专有网络的ID。
    3.  在专有网络详情页面，单击**开启ClassicLink**， 然后在弹出的对话框，单击**确定**。
    4.  登录[ECS管理控制台](https://ecs.console.aliyun.com/)。
    5.  在左侧导航栏，单击目标**实例**。
    6.  在页面左上角选择实例的所属地域。
    7.  在目标ECS实例的**操作**列中，单击**更多** \> **网络和安全组** \> **设置专有网络连接状态** 。
    8.  在弹出的对话框中选择MongoDB实例所属的专有网络，单击**确定**
    9.  在新弹出的连接专有网络对话框中，单击**前往实例安全组列表添加classicLink安全组规则**。

        ![经典网络的ECS连接专有网络](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/154587/155477262543386_zh-CN.png)

    10. 单击**添加ClassicLink安全组规则**，根据以下信息配置ClassicLink安全组规则，然后单击**确定**。

        |配置|说明|
        |:-|:-|
        |经典网络安全组|显示经典网络安全组的名称。|
        |选择专有网络安全组|选择专有网络的安全组。|
        |授权方式|选择一种授权方式：        -   经典网络 <=\> 专有网络：相互授权访问，推荐使用这种授权方式。
        -   经典网络 =\> 专有网络：授权经典网络ECS访问专有网络内的云资源。
        -   专有网络 =\> 经典网络：授权专有网络内的云资源访问经典网络ECS。
|
        |协议类型|选择授权通信的协议和端口。|
        |端口范围|端口的输入格式为xx/xx，此处放通的端口为MongoDB实例的端口3717，填入**3717/3717**。|
        |优先级|设置该规则的优先级。数字越小，优先级越高。|
        |描述|填入安全组描述，长度为2-256个字符，不能以 http:// 或 https:// 开头。|


## 专有网络的ECS实例连接经典网络的MongDB实例 {#section_tnd_w25_hhb .section}

![专有网络的ECS连接经典网络的MongoDB](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/154587/155477262643421_zh-CN.png)

将MongoDB实例切换到ECS实例所属的专有网络中，详情请参考[从经典网络切换为专有网络](cn.zh-CN/用户指南/管理网络连接/切换实例网络类型.md#section_tp1_1sl_2fb)。

**说明：** 

-   单节点实例暂不支持切换网络类型。
-   切换网络时，实例将会出现一次闪断。请您尽量在业务低峰期执行切换操作，或确保您的应用有自动重连机制，以避免闪断造成的影响。

