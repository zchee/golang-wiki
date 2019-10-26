# SQL database drivers

The database/sql and database/sql/driver packages are designed for using databases from Go and implementing database drivers, respectively.

See the design goals doc:

> http://golang.org/src/pkg/database/sql/doc.txt

# Drivers

Drivers for Go's sql package include:

  * **Apache Ignite/GridGain**: https://github.com/amsokol/ignite-go-client
  * **Apache Impala**: https://github.com/bippio/go-impala
  * **Apache Avatica/Phoenix**: https://github.com/apache/calcite-avatica-go
  * **AWS Athena**: https://github.com/segmentio/go-athena
  * **ClickHouse** (uses [native TCP interface](https://clickhouse.yandex/docs/en/interfaces/tcp.html)): https://github.com/kshvakov/clickhouse
  * **ClickHouse** (uses [HTTP API](https://clickhouse.yandex/docs/en/interfaces/http_interface.html)): https://github.com/mailru/go-clickhouse
  * **CockroachDB**: Use any PostgreSQL driver
  * **Couchbase N1QL**: https://github.com/couchbase/go_n1ql
  * **DB2 LUW** and **DB2/Z with DB2-Connect**: https://bitbucket.org/phiggins/db2cli (Last updated 2015-08)
  * **DB2 LUW** (uses cgo): https://github.com/asifjalil/cli
  * **DB2 LUW, z/OS, iSeries and Informix**: https://github.com/ibmdb/go_ibm_db
  * **Firebird SQL**: https://github.com/nakagami/firebirdsql
  * **Google Cloud BigQuery**: https://github.com/solcates/go-sql-bigquery
  * **MS ADODB**: https://github.com/mattn/go-adodb
  * **MS SQL Server** (pure go): https://github.com/denisenkom/go-mssqldb
  * **MS SQL Server** (uses cgo): https://github.com/minus5/gofreetds
  * **MySQL**: https://github.com/go-sql-driver/mysql/ ` [*] `
  * **MySQL**: https://github.com/siddontang/go-mysql/ ` [**] ` (also handles replication)
  * **MySQL**: https://github.com/ziutek/mymysql ` [*] `
  * **ODBC**: https://bitbucket.org/miquella/mgodbc (Last updated 2016-02)
  * **ODBC**: https://github.com/alexbrainman/odbc
  * **Oracle**: https://github.com/mattn/go-oci8
  * **Oracle**: https://gopkg.in/rana/ora.v4
  * **Oracle**: https://gopkg.in/goracle.v2
  * **QL**: http://godoc.org/github.com/cznic/ql/driver
  * **Postgres** (pure Go): https://github.com/lib/pq ` [*] `
  * **Postgres** (uses cgo): https://github.com/jbarham/gopgsqldriver
  * **Postgres** (pure Go): https://github.com/jackc/pgx ` [**] `
  * **Presto**: https://github.com/prestodb/presto-go-client
  * **SAP HANA** (uses cgo): https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.03/en-US/0ffbe86c9d9f44338441829c6bee15e6.html
  * **SAP HANA** (pure go): https://github.com/SAP/go-hdb
  * **SAP ASE** (uses cgo): https://github.com/SAP/go-ase - package cgo (pure go package planned)
  * **Snowflake** (pure Go): https://github.com/snowflakedb/gosnowflake
  * **SQLite** (uses cgo): https://github.com/mattn/go-sqlite3 ` [*] `
  * **SQLite** (uses cgo): https://github.com/gwenn/gosqlite - Supports SQLite dynamic data typing
  * **SQLite** (uses cgo): https://github.com/mxk/go-sqlite
  * **SQLite**: (uses cgo): https://github.com/rsc/sqlite
  * **SQL over REST**: https://github.com/adaptant-labs/go-sql-rest-driver
  * **Sybase SQL Anywhere**: https://github.com/a-palchikov/sqlago
  * **Sybase ASE** (pure go): https://github.com/thda/tds
  * **TiDB**: Use any MySQL driver
  * **Vertica**: https://github.com/vertica/vertica-sql-go
  * **Vitess**: https://godoc.org/vitess.io/vitess/go/vt/vitessdriver
  * **YQL (Yahoo! Query Language)**: https://github.com/mattn/go-yql
  * **Apache Hive**: https://github.com/sql-machine-learning/gohive
  * **MaxCompute**: https://github.com/sql-machine-learning/gomaxcompute

Drivers marked with ` [*] ` are both included in and pass the compatibility test suite at https://github.com/bradfitz/go-sql-test.  
Drivers marked with ` [**] ` pass the compatibility test suite but are not currently included in it.