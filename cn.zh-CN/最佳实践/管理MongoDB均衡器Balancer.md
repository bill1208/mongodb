# 管理MongoDB均衡器Balancer {#concept_w2f_kbl_2gb .concept}

云数据库支持均衡器 Balancer 管理操作。在一些特殊的业务场景下，您可以启用或者关闭 Balancer 功能，设置活动窗口等操作。

## 注意事项 {#section_qjg_dwl_2gb .section}

-   Balancer 属于分片集群架构中的功能，该操作仅适用于分片集群实例。
-   Balancer 的相关操作可能会占用实例的资源，请在业务低峰期操作。

## 关闭 Balancer 功能 {#section_k3j_4wl_2gb .section}

云数据库MongoDB的 Balancer 功能默认是开启状态。特殊业务场景下需要关闭，请参考下述操作步骤。

1.  [通过 Mongo Shell 登录数据库](../../../../cn.zh-CN/分片集群快速入门/连接实例/通过DMS登录MongoDB数据库.md#)。
2.  在 mongos 节点命令窗口中，切换至 config 数据库。

    ```
    use config
    ```

3.  执行如下命令查看 Balancer 运行状态，如返回值为空。

    ```
    while( sh.isBalancerRunning() ) {
              print("waiting...");
              sleep(1000);
    }
    ```

    -   返回值为空，表示 Balancer 没有处于执行任务的状态，此时可执行下一步的操作，关闭 Balancer 。
    -   返回值 waiting 表示 Balancer 正在执行块迁移，此时不能执行关闭 Balancer 的命令，否则可能引起数据不一致。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81256/155538190134744_zh-CN.png)

4.  确认执行第3步的命令后返回的值为空，可执行关闭 Balancer 命令。

    ```
    sh.stopBalancer()
    ```


## 开启 Balancer 功能 {#section_dyr_pcm_2gb .section}

如果您设置了数据分片，开启 Balancer 功能后可能会立即触发均衡任务。这将占用实例的资源，请在业务低峰期执行该操作。

1.  [通过 Mongo Shell 登录数据库](../../../../cn.zh-CN/分片集群快速入门/连接实例/通过DMS登录MongoDB数据库.md#)。
2.  在 mongos 节点命令窗口中，切换至 config 数据库。

    ```
    use config
    ```

3.  执行如下命令开启 Balancer功能。

    ```
    sh.setBalancerState(true)
    ```


## 设置 Balancer 的活动窗口 {#section_xss_lbl_2gb .section}

为避免 Balancer 执行块迁移操作影响您的业务，您可以通过设置 Balancer 的活动窗口，让 Blancer 在指定的时间段工作。

**说明：** 执行该操作须确保 Balancer 功能处于开启状态。如未开启，请参考[开启 Balancer 功能](#section_dyr_pcm_2gb)。

1.  [通过 Mongo Shell 登录数据库](../../../../cn.zh-CN/分片集群快速入门/连接实例/通过DMS登录MongoDB数据库.md#)。
2.  在 mongos 节点命令窗口中，切换至 config 数据库。

    ```
    use config
    ```

3.  执行如下命令设置 Balancer 的活动窗口。

    ```
    db.settings.update(
       { _id: "balancer" },
       { $set: { activeWindow : { start : "<start-time>", stop : "<stop-time>" } } },
       { upsert: true }
    )
    ```

    **说明：** 

    -   <start-time\>：开始时间，时间格式为 HH:MM，HH取值范围为00 - 23，MM取值范围为00 - 59。
    -   <stop-time\>：结束时间，时间格式为 HH:MM，HH取值范围为00 - 23，MM取值范围为00 - 59。
    您可以通过执行`sh.status()`命令查看 Balancer 的活动窗口。如下示例中，活动窗口设置为01:00- 03:00。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81256/155538190134738_zh-CN.png)


相关操作：如您需要 balancer 始终处于运行状态，您可以使用如下命令去除活动窗口的设置。

```
db.settings.update({ _id : "balancer" }, { $unset : { activeWindow : true } })
				
```

