# Well-known struct tags
## Background

Go offers [struct tags](https://go.dev/ref/spec#Tag) which are discoverable via reflection. These enjoy a wide range of use in the standard library in the JSON/XML and other encoding packages.

The community welcomed them and has built ORMs, further encodings, flag parsers and much more around them since, especially for these tasks, single-sourcing is beneficial for data structures.

## Problem description
Due to increased usage of Go and thus Go [struct tags](https://go.dev/ref/spec#Tag), clashes become inevitable.

## Solution
The list below is a best effort to document well-known struct tags used by packages which are available to the public.

## Format of the list
* Struct tag as extracted by calling https://pkg.go.dev/reflect#StructTag.Get with this tag as the `key` argument.
* Documentation link of this package using https://pkg.go.dev

### Example entry
Tag | Documentation
----|-----
xml | https://pkg.go.dev/encoding/xml

### Change Management
List entries can be added by anyone who creates a public package where a new tag is used.
List entries can be removed when the links to the package documentation stops working or the author(s) of that package requests it.

## List of well-known struct tags
Tag       | Documentation
----------|---------------
xml       | https://pkg.go.dev/encoding/xml
json      | https://pkg.go.dev/encoding/json
asn1      | https://pkg.go.dev/encoding/asn1
reform    | https://pkg.go.dev/gopkg.in/reform.v1
dynamodb  | https://docs.aws.amazon.com/sdk-for-go/api/service/dynamodb/dynamodbattribute/#Marshal
bigquery  | https://pkg.go.dev/cloud.google.com/go/bigquery
datastore | https://pkg.go.dev/cloud.google.com/go/datastore
spanner   | https://pkg.go.dev/cloud.google.com/go/spanner
bson      | https://pkg.go.dev/labix.org/v2/mgo/bson, https://pkg.go.dev/go.mongodb.org/mongo-driver/bson/bsoncodec
gorm      | https://pkg.go.dev/github.com/jinzhu/gorm
yaml      | https://pkg.go.dev/gopkg.in/yaml.v2
toml      | https://pkg.go.dev/github.com/pelletier/go-toml
validate  | https://github.com/go-playground/validator
mapstructure | https://pkg.go.dev/github.com/mitchellh/mapstructure
parser    | https://pkg.go.dev/github.com/alecthomas/participle
protobuf  | https://github.com/golang/protobuf
db        | https://github.com/jmoiron/sqlx
url       | https://github.com/google/go-querystring
feature   | https://github.com/nikolaydubina/go-featureprocessing
