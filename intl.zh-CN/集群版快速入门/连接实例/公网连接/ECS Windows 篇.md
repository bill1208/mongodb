# ECS Windows 篇 {#task787 .task}

目前云数据库MongoDB是需要通过 ECS 的内网进行连接访问，如果您本地需要通过公网访问云数据库 MongoDB，可以在 ECS Windows 云服务器中通过 netsh 进行端口映射实现。

1.     

    登录 ECS Windows 服务器，在 CMD 中执行以下命令：

    ```language-shell
    netsh interface portproxy add v4tov4 listenaddress=ECS服务器的公网IP地址 listenport=3717 connectaddress=云数据库MongoDB的连接地址 connectport=3717
    ```

    如下图：

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/44651/cn_zh/1476755412890/1.png)

     `netsh interface portproxy show all`可以查看当前服务器中存在的映射。

2.     

    设置完成后进行验证测试。

    在本地 MongoDB shell 连接 ECS Windows 服务器后进行数据写入和查询验证，ECS Windows 服务器的 IP 是1.1.1.1，即 `telnet 1.1.1.1 3717`。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/44651/cn_zh/1476755571477/1.png)

    通过上述步骤即可实现：您本地的 PC 或服务器通过公网连接 ECS Windows 3717端口，对云数据库 MongoDB 进行访问。

     **注意**：因 portproxy 由微软官方提供，未开源使用，您如果配置使用过程中遇到疑问，可参看 netsh 的 portproxy 使用说明或向微软官方咨询确认。或者您也可以考虑通过其他的方案实现，比如通过 portmap 配置代理映射。

3.     

    完成相关操作后，如需删除公网转发，可用`netsh interface portproxy delete v4tov4 listenaddress=ECS服务器的公网IP地址 listenport=3717`删除不需要的映射。


