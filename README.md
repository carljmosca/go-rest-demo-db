# go-rest-demo-db
go language REST demo with MySQL db

####build
go build main.go

####create database
mysqladmin create database -u root -p godemo

mysql godemo -u root -p <db/godemo.sql

####set environment variables (adjust for your platform)
export MYSQL_ENV_MYSQL_ROOT_PASSWORD=password  
export MYSQL_PORT_3306_TCP_ADDR=localhost  
export MYSQL_PORT_3306_TCP_PORT=3306

####running
#####run
./main
#####test from browser
http://localhost:3000/api/v1/users
