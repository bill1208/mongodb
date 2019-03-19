# MongoDB数据迁移方案概览 {#concept_ujv_lml_cgb .concept}

云数据库MongoDB提供了多种数据迁移方案，可满足不同业务场景下MongoDB数据库的数据迁移需求。

## MongoDB数据迁移概述 {#section_s1y_xz2_qgb .section}

-   通过使用阿里云[数据传输服务（DTS）](https://www.alibabacloud.com/help/zh/doc-detail/26592.htm)工具，您可以实现MongoDB数据库的全量数据迁移和增量数据迁移，其中增量数据迁移可以在不影响业务的情况下平滑地将MongoDB数据库迁移上云。
-   云数据库MongoDB支持使用官方的 Mongodump 和 Mongorestore 工具全量迁移数据库。
-   另外，云数据库MongoDB还支持通过物理备份文件和逻辑备份文件两种途径，将云上数据迁移到本地数据库。

## 将自建/本地数据库迁移到云数据库MongoDB {#section_bys_1yp_dgb .section}

|迁移方案|适用场景|
|:---|:---|
|[使用DTS工具迁移自建/本地MongoDB数据库](../../../../../intl.zh-CN/副本集快速入门/数据迁移/使用DTS工具迁移MongoDB自建数据库上云.md#)|单节点或副本集架构的MongoDB数据库迁移上云|
|使用Mongodump和Mongorestore工具迁移自建/本地数据库-   -   [自建/本地MongoDB数据库迁移至副本集实例](../../../../../intl.zh-CN/副本集快速入门/数据迁移/使用MongoDB工具迁移自建数据库上云.md#)
-   [自建/本地MongoDB数据库迁移至分片集群实例](../../../../../intl.zh-CN/分片集群快速入门/数据迁移/使用MongoDB工具迁移自建数据库上云.md#)

|-|

## 第三方云迁移至阿里云 {#section_im3_jyp_dgb .section}

[Azure Cosmos DB API for MongoDB 迁移到阿里云](../../../../../intl.zh-CN/最佳实践/Azure Cosmos DB API for MongoDB 迁移到阿里云.md#)

## 云数据库MongoDB实例间的数据迁移 {#section_gvb_nyp_dgb .section}

[副本集实例迁移至分片集群实例](intl.zh-CN/用户指南/数据迁移/MongoDB实例间迁移/副本集实例迁移至分片集群实例.md#)

## 将云数据库MongoDB迁移到自建/本地MongoDB数据库 {#section_swy_4yp_dgb .section}

|迁移方案|适用场景|
|:---|:---|
|[将逻辑备份迁移/恢复至本地MongoDB数据库](intl.zh-CN/用户指南/数据恢复/逻辑备份恢复至自建数据库.md#)|副本集实例或分片集群实例迁移至自建/本地MongoDB数据库|
|[将物理备份迁移/恢复至本地MongoDB数据库](intl.zh-CN/用户指南/数据恢复/物理备份恢复至自建数据库/将MongoDB物理备份文件恢复至自建数据库.md#)|副本集实例迁移至自建/本地MongoDB数据库|

