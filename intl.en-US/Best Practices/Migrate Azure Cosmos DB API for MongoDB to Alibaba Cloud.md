# Migrate Azure Cosmos DB API for MongoDB to Alibaba Cloud {#concept_dwb_4rk_5fb .concept}

MongoDB provides native backup utilities that you can use to migrate Azure Cosmos DB API for MongoDB to Alibaba Cloud.

## Notes {#section_j3k_5sk_5fb .section}

-   This data migration is a full migration. To avoid data inconsistencies, we recommend that you stop all write operations to the database before migration.
-   If you have used mongodump commands to back up the database, move the files in the dump folder to other directories. Make sure that the default dump folder is empty before data migration. Otherwise, existing backup files in this folder will be overwritten.
-   Run mongodump and mongorestore commands on servers on which MongoDB is installed. Do not run these commands in the mongo shell.

## Required database permissions {#section_oyv_j2l_5fb .section}

|Migration type|Full migration|
|:-------------|:-------------|
|Azure Cosmos DB|Read|
|Target MongoDB instance|Read and write|

## Environment configuration {#section_y4p_ztk_5fb .section}

1.  Create an ApsaraDB for MongoDB instance. For more information, see [Create an instance.](https://www.alibabacloud.com/help/doc-detail/26572.htm)

    **Note:** 

    -   The instance storage capacity must be larger than Azure Cosmos DB.
    -   Select MongoDB version 3.4.
2.  Set a password for the ApsaraDB for MongoDB instance. For more information, see [Set a password](https://www.alibabacloud.com/help/doc-detail/54956.htm).
3.  Install MongoDB on a server. For more information, see [Install MongoDB](https://docs.mongodb.com/manual/administration/install-community/).

    **Note:** 

    -   Install MongoDB 3.0 or a later version.
    -   This server is used to temporarily store data during backup and recovery, and is not needed after the migration is complete.
    -   The capacity of the disk where the backup is stored must be larger than Azure Cosmos DB.
    This example installs MongoDB on a Linux server. You can also use other operating systems, such as Windows.


## Procedure {#section_gy4_pvk_5fb .section}

1.  Log on to the Azure portal.
2.  Click **Azure Cosmos DB** from the left-side navigation pane.
3.  On the Azure Cosmos DB page, click the account name of the Azure Cosmos DB that you want to migrate.
4.  On the account details page, click **Connection String**.
5.  Click the **Read-only Keys** tab to view the database connection information.

    ![](images/32319_en-US.png "Azure connection information")

    **Note:** To migrate data, you only need a database account that has read-only permissions.

6.  Run the following command on the MongoDB server to back up the Azure Cosmos DB to this server.

    ```
    mongodump --host <HOST>:10255 --authenticationDatabase admin -u <USERNAME> -p <PRIMARY PASSWORD> --ssl --sslAllowInvalidCertificates
    ```

    Note: Replace <HOST\>, <USERNAME\>, and <PRIMARY PASSWORD\> with the corresponding values shown in the [Azure connection information](#fig_qbq_fy5_vfb) figure.

    After the backup is complete, backups of the Azure Cosmos DB are stored in the dump folder.

7.  Obtain the endpoint of the primary node of the ApsaraDB for MongoDB instance. For more information, see [Retrieve the seven connection elements](https://www.alibabacloud.com/help/doc-detail/44623.htm).
8.  Run the following command on the MongoDB server to export the backups to the ApsaraDB for MongoDB instance.

    ```
     mongorestore --host <mongodb_host>:3717 --authenticationDatabase admin -u <username> -p <password> dump
    ```

    Description:

    -   <mongodb\_host\>: The endpoint of the primary node of the MongoDB instance.
    -   <username\>: The username for the MongoDB instance.
    -   <password\>: The password for the MongoDB instance.

After the recovery is complete, backups of the Azure Cosmos DB are migrated to the ApsaraDB for MongoDB instance.

