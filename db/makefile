postgres:
    docker run --name postgres-16 -p 5432:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -d postgres:16-alpine

createdb:
    docker exec -it postgres-16 createdb --username=postgres --owner=postgres simple_bank

dropdb:
    docker exec -it postgres-16 dropdb simple_bank

migrateup:
   migrate -path db/migration -database "postgres://postgres:postgres@localhost:5432/simple_bank?sslmode=disable" -verbose up

migratedown:
   migrate -path db/migration -database "postgres://postgres:postgres@localhost:5432/simple_bank?sslmode=disable" -verbose down

sqlc:
   sqlc generate

test:
   go test -v -cover ./...

server:
    go run main.go

.PHONY: postgres createdb dropdb migrateup migratedown sqlc test server