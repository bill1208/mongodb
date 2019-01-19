# 使用DTS将腾讯云MongoDB数据库迁移至阿里云 {#concept_dx2_w5x_ggb .concept}

使用[数据传输服务DTS（Data Transmission Service）](https://dts.console.aliyun.com/)，您可以将腾讯云MongoDB副本集实例的3.2版本数据库，迁移至阿里云实例的数据库中。

## 注意事项 {#section_dww_lmr_zfb .section}

-   本文适用于数据库版本为3.2版本的腾讯云MongoDB副本集实例。

    数据库版本为3.6版本的腾讯云MongoDB副本集实例或腾讯云MongoDB分片实例迁移至阿里云请参考[腾讯云MongoDB数据库迁移至阿里云](cn.zh-CN/用户指南/数据迁移/第三方云迁移到阿里云/腾讯云MongoDB数据库迁移至阿里云.md#)。

-   不支持使用DTS进行[增量迁移](https://help.aliyun.com/knowledge_detail/39252.html)。

    **说明：** 使用DTS进行全量数据迁移，迁移开始前需要停止腾讯云MongoDB数据库的相关业务。同时为了保障数据一致性，迁移期间请勿在腾讯云MongoDB数据库中写入新的数据。

-   支持跨数据库版本迁移。（阿里云MongoDB实例支持3.2、3.4和4.0版本）
-   支持跨存储引擎迁移。（阿里云MongoDB实例支持WiredTiger、RocksDB、TerarkDB三种存储引擎）
-   阿里云MongoDB实例的存储空间应大于腾讯云MongoDB数据库的存储空间。
-   为避免影响您的正常业务使用，请在业务低峰期进行数据迁移。

## 费用说明 {#section_brm_q21_1gb .section}

|迁移类型|链路配置费用|公网流量费用|
|:---|:-----|:-----|
|全量数据迁移|不收取|不收取|

## 迁移类型说明 {#section_zjf_5fs_zfb .section}

全量数据迁移：将腾讯云MongoDB实例数据库迁移对象的存量数据全部迁移到阿里云MongoDB实例数据库中。

-   支持database迁移。
-   支持collection迁移。
-   支持index迁移。

## 迁移权限要求 {#section_mfq_xmr_zfb .section}

|迁移对象|全量数据迁移|
|:---|:-----|
|腾讯云MongoDB副本集实例|read权限|
|阿里云MongoDB实例|readWrite权限|

## 迁移前准备工作一 {#section_y4p_ztk_5fb .section}

创建阿里云MongoDB实例。详情请参考[创建副本集实例](../../../../../cn.zh-CN/副本集快速入门/创建副本集实例.md#)或[创建分片集群实例](../../../../../cn.zh-CN/分片集群快速入门/创建分片集群实例.md#)。（如已创建实例，可忽略本步骤）

**说明：** 

-   阿里云MongoDB实例的存储空间要大于腾讯云MongoDB数据库的存储空间。
-   如迁移至阿里云MongoDB分片集群实例，建议对数据进行分片，详情请参考[设置数据分片](../../../../../cn.zh-CN/最佳实践/设置数据分片以充分利用Shard性能.md#)。

## 迁移前准备工作二 {#section_pcx_yhs_zfb .section}

由于腾讯云MongoDB实例只有内网连接地址，没有公网连接地址。此时需要创建一个具有公网地址的腾讯云服务器用作端口数据转发，以完成数据库的迁移操作。迁移操作完成后如不再需要，可释放腾讯云服务器。

**说明：** 为保障腾讯云服务器和腾讯云MongoDB实例可正常通信。创建腾讯云服务器时，腾讯云服务器的地域、可用区、私有网络和子网保持与腾讯云MongoDB实例一致。

本次演示的案例中，创建腾讯云服务器时使用的是Linux系统。

1.  创建腾讯云服务器。
2.  在腾讯云控制台，查看腾讯云服务器的内网IP地址与公网IP地址。

    ![查看云服务器的内外网IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154788232735509_zh-CN.png)

3.  在腾讯云控制台，查看腾讯云MongoDB实例的内网IP地址。

    ![查看MongoDB实例的内网IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154788232735670_zh-CN.png)

4.  登录腾讯云服务器，使用如下命令开启腾讯云服务器的iptables服务。

    ```
    service iptables start
    ```

5.  对腾讯云服务器的内网IP地址与腾讯云MongoDB的内网IP地址添加iptables规则。

    ```
    iptables -t nat -A PREROUTING -d <CVM_IP>  -p tcp --dport 27017 -j DNAT --to-destination <MongoDB_IP>:27017
    iptables -t nat -A POSTROUTING -d <MongoDB_IP> -p tcp --dport 27017 -j SNAT --to-source <CVM_IP>
    ```

    **说明：** 

    -   <CVM\_IP\>：腾讯云服务器的内网IP地址。
    -   <MongoDB\_IP\>：腾讯云MongoDB数据库的内网IP地址
    示例：

    ```
    iptables -t nat -A PREROUTING -d 10.10.0.5  -p tcp --dport 27017 -j DNAT --to-destination 10.10.0.7:27017
    iptables -t nat -A POSTROUTING -d 10.10.0.7 -p tcp --dport 27017 -j SNAT --to-source 10.10.0.5
    ```

6.  开启腾讯云服务器的路由转发功能。

    ```
    echo 1 > /proc/sys/net/ipv4/ip_forward
    ```

7.  返回腾讯云服务器控制台，在左侧导航栏，单击**安全组**。
8.  在入站规则页签，单击**添加规则**，将MongoDB数据库端口27017放通，允许外网访问。

    ![安全组配置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154788232835723_zh-CN.png)


## 数据迁移操作步骤 {#section_lnt_knr_zfb .section}

1.  登录[DTS数据传输服务控制台](https://dts.console.aliyun.com/)。
2.  在左侧导航栏，单击**数据迁移**。
3.  单击数据迁移页面右侧的**创建迁移任务**。
4.  配置迁移任务的**源库及目标库**信息。

    ![源库及目标库配置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84333/154788232836005_zh-CN.png)

    |源库及目标库信息说明表|
    |:----------|
    |任务名称|     -   DTS为每个任务自动生成一个任务名称，任务名称没有唯一性要求。
    -   您可以根据需要修改任务名称，建议为任务配置具有业务意义的名称，便于后续的任务识别。
 |
    |源实例信息|     -   实例类型：选择**有公网IP的自建数据库**。
    -   实例地区：选择腾讯云MongoDB数据库所在地域。
    -   数据库类型：选择**MongoDB**
    -   主机名或IP地址：填入腾讯云服务器的公网IP地址。
    -   端口号：填入腾讯云MongoDB数据库的端口号，本案例中填入27017。
    -   数据库名称：填入腾讯云MongoDB数据库中，用于账号验证的鉴权数据库名称，默认为admin。
    -   数据库账号：填入登录腾讯云MongoDB数据库的数据库账号，默认为mongouser。权限要求请参见[迁移账号权限要求](#)。
    -   数据库密码：填入登录腾讯云MongoDB数据库账号对应的密码。
 |
    |目标实例信息|     -   实例类型：选择**MongoDB实例**。
    -   实例地区：选择阿里云MongoDB实例所在地域。
    -   MongoDB实例ID：选择阿里云MongoDB实例的实例ID。
    -   数据库名称：填入阿里云MongoDB实例中，用于账号验证的鉴权数据库名称，默认为admin。
    -   数据库账号：填入连接阿里云MongoDB实例数据库的账号，权限要求请参见[迁移账号权限要求](#)。
    -   数据库密码：填入连接阿里云MongoDB实例数据库账号对应的密码。
 |

5.  配置完成后，单击页面右下角的**授权白名单并进入下一步**。

    **说明：** 此步骤会将DTS服务器的IP地址自动添加阿里云MongoDB实例的白名单中，用于保障DTS服务器能够正常连接MongoDB实例。迁移完成后如不再需要可手动删除，详情请参考[白名单设置](cn.zh-CN/用户指南/数据安全性/设置白名单.md#)。

6.  选择**迁移对象**和**迁移类型**。

    ![迁移对象和迁移类型配置](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83046/154788232835725_zh-CN.png)

    |迁移对象及迁移类型|
    |:--------|
    |迁移类型|迁移类型选择**全量数据迁移**。**说明：** 为保障数据一致性，全量数据迁移期间请勿在腾讯云MongoDB数据库中写入新的数据。

|
    |迁移对象|     -   在**迁移对象**框中将想要迁移的数据库选中，单击![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/154788232833712_zh-CN.png)移动到**已选择对象**框。
    -   迁移对象选择的粒度可以为：库、collection/function 两个粒度。
    -   默认情况下，对象迁移到阿里云MongoDB数据库后，对象名跟腾讯云MongoDB数据库一致。

**说明：** 如果您迁移的对象在腾讯云MongoDB数据库与阿里云MongoDB数据库上名称不同，那么需要使用DTS提供的对象名映射功能，使用方法请参考[库表列映射](https://help.aliyun.com/document_detail/26628.html)。

 |

7.  上述配置完成后，单击页面右下角的**预检查并启动**。

    **说明：** 

    -   在迁移任务正式启动之前，会先进行预检查。只有预检查通过后，才能成功启动迁移任务。
    -   如果预检查失败，单击具体检查项后的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/75938/154788232833661_zh-CN.png)，查看具体的失败详情。根据失败原因修复后，重新进行预检查。
8.  预检查通过后，单击**下一步**。
9.  在**购买配置确认**页面，选择**链路规格**并勾选**数据传输（按量付费）服务条款**。
10. 单击**购买并启动**，迁移任务正式开始。

    等待迁移任务完成即可，迁移任务会自动停止。


