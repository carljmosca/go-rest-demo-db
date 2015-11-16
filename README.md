# go-rest-demo-db
go language REST demo with MySQL db  
The instructions assume a configured go development environment.  If needed see the go install docs https://golang.org/doc/install

#####build
go build main.go

#####create database
mysqladmin create database -u root -p godemo

mysql godemo -u root -p <db/godemo.sql

#####set environment variables (adjust for your platform)
export MYSQL_ENV_MYSQL_ROOT_PASSWORD=password  
export MYSQL_PORT_3306_TCP_ADDR=localhost  
export MYSQL_PORT_3306_TCP_PORT=3306

#####running
######run
./main
######test from browser
http://localhost:3000/api/v1/users
######populate with some data
curl -H "Content-Type: application/json" -X POST -d '{"firstname":"John","lastname":"Smith"}' http://localhost:3000/api/v1/users {"id":3,"firstname":"John","lastname":"Smith"}
######test again from browser or GET with curl
curl -H "Content-Type: application/json" http://localhost:3000/api/v1/users

#####Docker instructions
######build
change to the db directory  
./build.sh
./run.sh
change back to top level directory
./run.sh
