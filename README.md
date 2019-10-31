# casbin-gosql-adapter
sqlx adapter for Casbin https://github.com/casbin/casbin

Based on [sqlx](https://github.com/jmoiron/sqlx), and tested in [MySQL](https://github.com/go-sql-driver/mysql).

## Installation

    go get github.com/ilibs/casbin-gosql-adapter

## Usage example

```go
package main

import (
	"github.com/casbin/casbin/v2"
	"github.com/ilibs/casbin-gosql-adapter"
	_ "github.com/go-sql-driver/mysql"
)

opts := &sqlxadapter.AdapterOptions{
    DriverName: "mysql",
    DataSourceName: "root:1234@tcp(127.0.0.1:3306)/yourdb",
    TableName: "casbin_rule",
    // or reuse an existing connection:
    // DB: myDBConn,
}

a := sqlxadapter.NewAdapterFromOptions(opts)
// Casbin v2 may return an error
e, err := casbin.NewEnforcer("examples/rbac_model.conf", a)
if err != nil {
    panic(err)
}
```

## Thank

This code fock from https://github.com/memwey/casbin-sqlx-adapter 

Currently for testing, gosql will be consolidated next
