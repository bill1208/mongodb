# RAM中可授权的MongoDB资源类型 {#concept_61755_zh .concept}

目前，可以在RAM中进行授权的资源类型仅一种：dbinstance。在通过RAM进行授权时，资源的描述方式如下：

|资源类型|授权策略中的资源描述方式|
|:---|:-----------|
|Instance| acs:dds:$regionid:$accountid:dbinstance/$dbinstanceid

 acs:dds:$regionid:$accountid:dbinstance/

 acs:dds:::dbinstance/

 |

其中：

-   所有$regionid应为某个region的id，或者"\*"。
-   所有$dbinstanceid应为某个instance的id，或者“\*”。
-   以此类推，$account-id是您云帐号的数字ID，可以用"\*"代替。

