## 1. 参照サイト
### Go関連
  - godotenvについて  
    https://www.st-hakky-blog.com/entry/2020/06/11/100000

### PostgresSQL関連
  - PostgresSQLコマンドの使い方  
    https://qiita.com/Shitimi_613/items/bcd6a7f4134e6a8f0621

  - POSTGRES_INITDB_ARGS:encodingとlocaleの設定  
    https://oki2a24.com/2020/02/23/set-no-locale-to-docker-compose-postgresql/

### migrate
  - golang-migrate  
    https://dev.classmethod.jp/articles/db-migrate-with-golang-migrate/
  
## 2. 初期使用パッケージ
  - GIN  
    github.com/gin-gonic/gin
  - PostgreSQL Driver  
    github.com/lib/pq
  - Gorm  
    github.com/jinzhu/gorm
  - godotenv  
    github.com/joho/godotenv

## 3. 初期設定 & 初期パッケージinstall
```
$ go mod init github.com/hideyoshidan/go_bbs
$ go get github.com/gin-gonic/gin
$ go get github.com/lib/pq
$ go get github.com/jinzhu/gorm
$ go get github.com/joho/godotenv
$ go mod tidy
```

## 4. 初期構築手順
#### ① docker build & make container
```
$ docker compose build --no-cache
$ docker compose up -d
```

#### ② containerに入る
```
$ docker compose exec go_app bash 
root@0b27509921ce:/var/www/go_bbs#
```

#### ③ migrateコマンドが使えるか確認
```
# migrate --help
Usage: migrate OPTIONS COMMAND [arg...]
       migrate [ -version | -help ]

Options:
  -source          Location of the migrations (driver://url)
  -path            Shorthand for -source=file://path
  -database        Run migrations against this database (driver://url)
  -prefetch N      Number of migrations to load in advance before executing (default 10)
  -lock-timeout N  Allow N seconds to acquire database lock (default 15)
  -verbose         Print verbose logging
  -version         Print version
  -help            Print usage

Commands:
  create [-ext E] [-dir D] [-seq] [-digits N] [-format] NAME
			   Create a set of timestamped up/down migrations titled NAME, in directory D with extension E.
			   Use -seq option to generate sequential up/down migrations with N digits.
			   Use -format option to specify a Go time format string. Note: migrations with the same time cause "duplicate migration version" error. 
  goto V       Migrate to version V
  up [N]       Apply all or N up migrations
  down [N]     Apply all or N down migrations
  drop         Drop everything inside database
  force V      Set version V but don't run migration (ignores dirty state)
  version      Print current migration version

Source drivers: github-ee, gitlab, go-bindata, godoc-vfs, gcs, file, s3, github
Database drivers: sqlserver, cockroachdb, firebirdsql, mysql, postgres, spanner, crdb-postgres, mongodb, redshift, stub, cassandra, clickhouse, cockroach, firebird, postgresql
```

#### ④ goが動くか確認
```
# make run
go run main.go
This is test
```

#### ⑤ go.mod作成
```
# go mod init github.com/hideyoshidan/go_bbs
go: creating new go.mod: module github.com/hideyoshidan/go_bbs
go: to add module requirements and sums:
	go mod tidy
```

#### ⑥ 必要なパッケージinstall
```
# go get github.com/gin-gonic/gin \
> github.com/lib/pq \
> github.com/jinzhu/gorm \
> github.com/joho/godotenv
# go mod tidy
```

## 5. メモ
  - GOPATH
```
GOPATH=$HOME/go
```
