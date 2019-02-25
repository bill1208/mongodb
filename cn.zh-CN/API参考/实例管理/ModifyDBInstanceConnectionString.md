# ModifyDBInstanceConnectionString {#reference_wg5_qck_bfb .reference}

修改实例的连接地址。

## 请求参数 {#section_wyf_jbk_bfb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：ModifyDBInstanceConnectionString。

|
|DBInstanceId|String|是|实例ID。|
|NoId|String|否|实例为分片集群实例时，传入mongos节点的ID。每次仅能传入一个mongos节点的ID。

|
|CurrentConnectionString|String|是|实例当前连接地址。|
|NewConnectionString|String|是|实例的新地址。只能修改连接地址的前缀部分。

连接地址以小写字母开头，由字母、数字组成，长度为8~64个字符。

|

