# 关于MongoDB控制台 {#concept_pp1_vyq_52b .concept}

[MongoDB管理控制台](https://mongodb.console.aliyun.com/)是用于管理MongoDB实例的Web应用程序，您可以在MongoDB管理控制台上创建实例、设置IP白名单、设置连接数据库的密码、设置网络等操作。

MongoDB管理控制台是阿里云管理控制台的一部分，关于控制台的通用设置和基本操作请参见：[使用阿里云管理控制台](https://www.alibabacloud.com/help/zh/doc-detail/47605.html)。

## 前提条件 {#section_a3c_t2h_hfb .section}

使用阿里云账号登录MongoDB管理控制台。若没有阿里云账号，请单击[注册](https://account.aliyun.com/register/register.htm)。

## 控制台首页 {#section_bnm_4gh_hfb .section}

对于MongoDB所有分片集群实例而言，控制台首页的界面信息都是相同的。

登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)，进入实例列表页面，如下图所示（仅为示例，请以实际界面为准）。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6687/154017025713822_zh-CN.png)

参考说明

|序号|名称|说明|
|:-|:-|:-|
|1|分片集群实例列表|MongoDB控制台的首页，显示同一账户中某个地区下的分片集群实例信息。|
|2|地域|下拉选择某个地域，该地域下的所有实例就会显示在实例列表中。|
|3|刷新|刷新实例信息页面。|
|4|新建实例|[新建实例入口](https://www.alibabacloud.com/help/zh/doc-detail/55137.htm)|
|5|实例ID| -   单击进入该实例详情页面
-   单击实例ID后的铅笔图标可以修改实例的备注名

 |
|6|运行状态|实例运行状态，根据实例的不同情况也会有不同的状态。|
|7|管理|点击展开后，可快捷对实例进行管理、重启、释放等操作。|

## MongoDB实例控制台 {#section_r2s_zhh_hfb .section}

登录[MongoDB管理控制台](https://mongodb.console.aliyun.com/)，单击**实例ID**操作栏下的**管理**，即可进入MongoDB实例的管理详情页面，详情如下表所示：

|控制台页面名称|区块名称|描述|常用操作链接|
|:------|:---|:-|:-----|
|界面上方操作区|-|可进行备份实例、重启实例操作。| -   备份实例
-   [重启实例](../../../../intl.zh-CN/用户指南/管理实例/重启实例.md#)

 |
|基本信息|基本信息|查看实例的基本信息，如实例ID、地域、可用区、网络类型、存储引擎等。|-|
|规格信息|查看MongoDB版本、可维护时间段、付费方式、创建时间、到期时间等|[设置可维护时间段](../../../../intl.zh-CN/用户指南/管理实例/设置可维护时间段.md#)。|
|Mongos列表或者Shard列表| -   在Mongos列表中，选择目标ID，单击![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6689/154017025713802_zh-CN.png)可以变配、登录、重启。
-   在Shard列表中，选择目标ID，单击![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6689/154017025713802_zh-CN.png)可以变配、登录、重启实例的Shard节点。
-   重启节点时，可能会导致数据库的读写操作失败，所以不建议用户在重启数据库，或者是重启节点的时候进行数据库的增删改查等操作。

 | -   变更配置
-   登录数据库
-   重启节点
-   查看Mongos节点或者Shard节点的运行监控信息。

 |
|备份与恢复|-|查看选定时间的数据备份列表、按照时间范围恢复数据、从备份点创建实例、按时间点新建实例等。| -   [下载备份数据](../../../../intl.zh-CN/.md#)。
-   按时间点新建实例。

 |
|监控信息|-|根据选定的数据指标和查询时间查看Mongos节点和Shard节点的监控信息。|-|
|数据安全性|白名单设置|可进行IP白名单设置。|[IP白名单设置](intl.zh-CN/集群版快速入门/设置白名单.md#)。|
|审计日志|查看审计日志。|-|

