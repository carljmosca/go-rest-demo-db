# go-rest-demo-db
go language REST demo with MySQL db  
The instructions assume a configured go development environment.  If needed see the go install docs https://golang.org/doc/install

######database connection explanation
The database connection expected 3 values to be available as environment variables.  
From the code excerpt below, we see the three values: **MYSQL_ENV_MYSQL_ROOT_PASSWORD,
  MYSQL_PORT_3306_TCP_ADDR, and MYSQL_PORT_3306_TCP_PORT**  
Also note, in this example the username and database name are both hard-coded and
may also be substituted with environment variables in a real-world use case.
```
db, err := sql.Open("mysql", "root:" +
  os.Getenv("MYSQL_ENV_MYSQL_ROOT_PASSWORD") +
  "@tcp(" + os.Getenv("MYSQL_PORT_3306_TCP_ADDR") + ":" +
  os.Getenv("MYSQL_PORT_3306_TCP_PORT") + ")/godemo")
```
Each of these should be configured according (see below).


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
./buildsh  
./run.sh  
if you don't have it, get the ip address of your docker machine  (depending on your environment)
docker-machine ip default  
curl -H "Content-Type: application/json" -X POST -d '{"firstname":"John","lastname":"Smith"}' http://192.168.99.100:3000/api/v1/users  
curl -H "Content-Type: application/json" http://192.168.99.100:3000/api/v1/users  
