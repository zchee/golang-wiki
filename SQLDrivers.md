# SQL database drivers

The database/sql and database/sql/driver packages are designed for using databases from Go and implementing database drivers, respectively.

See the design goals doc:

> http://golang.org/src/pkg/database/sql/doc.txt

# Drivers

Drivers for Go's sql package include:

  * **Apache Phoenix/Avatica**: https://github.com/Boostport/avatica
  * **ClickHouse**: https://github.com/kshvakov/clickhouse
  * **Couchbase N1QL**: https://github.com/couchbase/go_n1ql
  * **DB2**: https://bitbucket.org/phiggins/db2cli
  * **Firebird SQL**: https://github.com/nakagami/firebirdsql
  * **MS ADODB**: https://github.com/mattn/go-adodb
  * **MS SQL Server** (pure go): https://github.com/denisenkom/go-mssqldb
  * **MS SQL Server** (uses cgo): https://github.com/minus5/gofreetds
  * **MySQL**: https://github.com/ziutek/mymysql ` [*] `
  * **MySQL**: https://github.com/go-sql-driver/mysql/ ` [*] `
  * **ODBC**: https://bitbucket.org/miquella/mgodbc
  * **ODBC**: https://github.com/alexbrainman/odbc
  * **Oracle**: https://github.com/mattn/go-oci8
  * **Oracle**: https://github.com/rana/ora
  * **QL**: http://godoc.org/github.com/cznic/ql/driver
  * **Postgres** (pure Go): https://github.com/lib/pq ` [*] `
  * **Postgres** (uses cgo): https://github.com/jbarham/gopgsqldriver
  * **Postgres** (pure Go): https://github.com/jackc/pgx
  * **SAP HANA** (pure go): https://github.com/SAP/go-hdb
  * **SQLite**: https://github.com/mattn/go-sqlite3 ` [*] `
  * **SQLite**: https://github.com/gwenn/gosqlite - Supports SQLite dynamic data typing
  * **SQLite**:  https://github.com/mxk/go-sqlite
  * **Sybase SQL Anywhere**: https://github.com/a-palchikov/sqlago
  * **Vitess**: https://godoc.org/github.com/youtube/vitess/go/vt/vitessdriver
  * **YQL (Yahoo! Query Language)**: https://github.com/mattn/go-yql

Drivers marked with a ` [*] ` are both included in and pass the compatibility test suite at https://github.com/bradfitz/go-sql-test