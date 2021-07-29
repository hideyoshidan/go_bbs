## 参照サイト
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
  
## 使用パッケージ
  - GIN  
    github.com/gin-gonic/gin
  - PostgreSQL Driver  
    github.com/lib/pq
  - Gorm  
    github.com/jinzhu/gorm
  - godotenv  
    github.com/joho/godotenv

## 初期設定 & 初期パッケージinstall
```
$ go mod init github.com/hideyoshidan/go_bbs
$ go get github.com/gin-gonic/gin
$ go get github.com/lib/pq
$ go get github.com/jinzhu/gorm
$ go get github.com/joho/godotenv
$ go mod tidy
```
## メモ
  - GOPATH
```
GOPATH=$HOME/go
```
