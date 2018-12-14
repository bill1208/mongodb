# MongoDB分片集群实例设置主备切换 {#concept_wcc_cc5_cgb .concept}

MongoDB分片集群实例的每个Shard节点都默认含有三个节点，当某个节点发生故障时，云数据库MongoDB的高可用系统会自动触发主备切换，保障整体的可用性。同时您也可以在日常容灾演练等场景中，手动触发云数据库MongoDB主备切换功能。

## 主备切换注意事项 {#section_ind_2c5_cgb .section}

分片集群实例Shard节点中的Primary节点及Secondary节点对外提供访问地址，Hidden节点作为日常备节点保障高可用。通过控制台或[API](../../../../cn.zh-CN/API参考/实例管理/SwitchDBInstanceHA.md#)操作MongoDB分片集群实例的主备切换后，系统将实现Shard节点中Primary节点和Secondary节点的角色互换。

**说明：** 

-   云数据库MongoDB主备切换操作只支持副本集实例和分片集群实例，单节点实例因架构因素，不支持主备切换。
-   分片集群实例的主备切换要求进行切换的Shard节点处于正常运行状态。
-   触发主备切换后，会产生1次30秒内的连接闪断，请在业务低峰期操作并确保应用具备重连机制。

## MongoDB主备切换操作步骤 {#section_qlp_fc5_cgb .section}

1.  登录MongoDB[管理控制台](https://mongodb.console.aliyun.com/#/mongodb/list)。
2.  单击目标实例ID或者单击**![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/54529/cn_zh/1520491271114/dd.png)** \> **管理**进入基本信息页面。
3.  在Shard列表栏，查找需要切换的Shard节点，单击**![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/54529/cn_zh/1520491271114/dd.png)** \> **主备切换**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/6741/154476848313849_zh-CN.png)

    每个Shard节点都单独提供主备切换入口，主备切换仅对当前操作的Shard节点有效，不影响集群下其他Shard节点。

4.  在弹出的主备切换对话框中单击**确定**。
5.  约1分钟左右，Shard节点会完成主备切换。MongoDB分片集群实例中其他Shard节点如有主备切换需求，可重复上述步骤操作 。

