# go-rest-demo-db
go language REST demo with MySQL db

####go build main.go

####create database
mysqladmin create database -u root -p godemo
mysql godemo -u root -p <godemo.sql

####set environment variables (adjust for your platform)
export MYSQL_ENV_MYSQL_ROOT_PASSWORD=password
export MYSQL_PORT_3306_TCP_ADDR=localhost
export MYSQL_PORT_3306_TCP_PORT=3306
