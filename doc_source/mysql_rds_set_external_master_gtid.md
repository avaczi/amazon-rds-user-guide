# mysql\.rds\_set\_external\_master\_gtid<a name="mysql_rds_set_external_master_gtid"></a>

Configures GTID\-based replication from a MariaDB instance running external to Amazon RDS to an Amazon RDS MariaDB DB instance\. This stored procedure is supported only where the external MariaDB instance is version 10\.0\.24 or greater\. When setting up replication where one or both instances do not support MariaDB global transaction identifiers \(GTIDs\), use [mysql\.rds\_set\_external\_master](mysql_rds_set_external_master.md)\.

Using GTIDs for replication provides crash\-safety features not offered by binary log replication, so we recommend it in cases where the replicating instances support it\. 

## Syntax<a name="mysql_rds_set_external_master_gtid-syntax"></a>

```
CALL mysql.rds_set_external_master_gtid(
  host_name
  , host_port
  , replication_user_name
  , replication_user_password
  , gtid
  , ssl_encryption
);
```

## Parameters<a name="mysql_rds_set_external_master_gtid-parameters"></a>

 *host\_name*   
String\. The host name or IP address of the MariaDB instance running external to Amazon RDS that will become the replication master\.

 *host\_port*   
Integer\. The port used by the MariaDB instance running external to Amazon RDS to be configured as the replication master\. If your network configuration includes SSH port replication that converts the port number, specify the port number that is exposed by SSH\.

 *replication\_user\_name*   
String\. The ID of a user with REPLICATION SLAVE permissions in the MariaDB DB instance to be configured as the Read Replica\.

 *replication\_user\_password*   
String\. The password of the user ID specified in `replication_user_name`\.

 *gtid*   
String\. The global transaction ID on the master that replication should start from\.  
You can use `@@gtid_current_pos` to get the current GTID if the replication master has been locked while you are configuring replication, so the binary log doesn't change between the points when you get the GTID and when replication starts\.  
Otherwise, if you are using `mysqldump` version 10\.0\.13 or greater to populate the slave instance prior to starting replication, you can get the GTID position in the output by using the `--master-data` or `--dump-slave` options\. If you are not using `mysqldump` version 10\.0\.13 or greater, you can run the `SHOW MASTER STATUS` or use those same `mysqldump` options to get the binary log file name and position, then convert them to a GTID by running `BINLOG_GTID_POS` on the external MariaDB instance:  

```
SELECT BINLOG_GTID_POS('<binary log file name>', <binary log file position>);
```
For more information about the MariaDB implementation of GTIDs, go to [Global Transaction ID](http://mariadb.com/kb/en/mariadb/global-transaction-id/) in the MariaDB documentation\.

 *ssl\_encryption*   
Integer\. This option is not currently implemented\.  The default is 0\.

## Usage Notes<a name="mysql_rds_set_external_master_gtid-usage-notes"></a>

The `mysql.rds_set_external_master_gtid` procedure must be run by the master user\. It must be run on the MariaDB DB instance that you are configuring as the replication slave of a MariaDB instance running external to Amazon RDS\. Before running `mysql.rds_set_external_master_gtid`, you must have configured the instance of MariaDB running external to Amazon RDS as a replication master\. For more information, see [Importing Data into a MariaDB DB Instance](MariaDB.Procedural.Importing.md)\.

**Warning**  
Do not use `mysql.rds_set_external_master_gtid` to manage replication between two Amazon RDS DB instances\. Use it only when replicating with a MariaDB instance running external to RDS\. For information about managing replication between Amazon RDS DB instances, see [Working with Read Replicas of MariaDB, MySQL, and PostgreSQL DB Instances](USER_ReadRepl.md)\.

After calling `mysql.rds_set_external_master_gtid` to configure an Amazon RDS DB instance as a Read Replica, you can call [mysql\.rds\_start\_replication](mysql_rds_start_replication.md) on the replica to start the replication process\. You can call [mysql\.rds\_reset\_external\_master](mysql_rds_reset_external_master.md) to remove the Read Replica configuration\.

When `mysql.rds_set_external_master_gtid` is called, Amazon RDS records the time, user, and an action of "set master" in the `mysql.rds_history` and `mysql.rds_replication_status` tables\.

## Examples<a name="mysql_rds_set_external_master_gtid-examples"></a>

When run on a MariaDB DB instance, the following example configures it as the replication slave of an instance of MariaDB running external to Amazon RDS\.

```
call mysql.rds_set_external_master_gtid ('Sourcedb.some.com',3306,'ReplicationUser','SomePassW0rd','0-123-456',0); 
```

## Related Topics<a name="mysql_rds_set_external_master_gtid.related"></a>

+ [mysql\.rds\_reset\_external\_master](mysql_rds_reset_external_master.md)

+ [mysql\.rds\_start\_replication](mysql_rds_start_replication.md)

+ [mysql\.rds\_stop\_replication](mysql_rds_stop_replication.md)