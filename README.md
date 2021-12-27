# Simple RESTfull API Assignment
This is a RESTful API with two endpoints, where:
- One of them that fetches the data in the provided MongoDB collection and returns the results in the requested format.
- Second endpoint is a create(POST) and fetch(GET) data from an in-memory storage.


## Prerequisites
- Golang (tested on version 1.75.5) for the application and Unit Tests

https://go.dev/doc/install

- Newman for End To End tests

https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/


# Installation and running
Clone the repository and once inside the new directory, get inside src:
```
cd src
```
You can build or just run as any other Golang program, the main entrance of the project is the file restful.go, e.g.:
```
go build; ./restful
```
or
```
go run restful.go
```

## About runnig
The file named *restful.go* have the line:
```
http.ListenAndServe(":8080", r)
```
That line is responsible to for the connection, it's good to know in case if you need to change any information about it.
For instance, there's a working application running at Heroku and for that this line needed to be changed for their local port as following:
```
http.ListenAndServe(":"+os.Getenv("PORT"), r)
```


## External resource
You may need to install mongo driver to your environment:
```
go get go.mongodb.org/mongo-driver
```
Or just the ones needed by the project:
```
go get go.mongodb.org/mongo-driver/mongo/options
go get go.mongodb.org/mongo-driver/mongo
go get go.mongodb.org/mongo-driver/bson
```


# Tests
## End To End (E2E)
To run E2E tests first you need to go inside the tests directory
```
cd tests
```
After that you need to run newman for the json file located at this folder:
```
newman run Assessment.postman_collection.json
```
Remember to always to restart the server before and after run this tests, due the memory storage

## Unit Tests
To run unit tests first you need to go inside the src directory
```
cd src
```
After that you need to run go tests for directories:
```
go test ./...
```


# Production
If you just want to test without any installation, feel free to try at this server:
```
https://agile-headland-80738.herokuapp.com
```


# Development
## Directories
The main code is at the file *restful.go*

The docs directory contain a [Swagger Contract](https://swagger.io/docs/specification/paths-and-operations/) with API documentation and validates using [Swagger Validator](https://editor.swagger.io/)

The src directory contains the source code

The tests directory contains the E2E tests made with Postman, so you can use the file to import it, or use it with Newman in console

## Source directory
The configs directory is responsible for main configurations
- database.go for database connections and messages related
- messages.go for all other standard messages, as error messages for the API for instance

The database directory is responsible for the database endpoints
- data.go is responsible for content to be used in any Database
- mongo.go is responsible for the MongoDB management for the project

The internal directory contains functions that can be used in several parts of the code to keep the DRY principle

The memory directory contains the code for in-memory storage

The router directory have 2 files:
- entry.go which is responsible to manager the entries (match the endpoints)
- router.go which is responsible to manager the routes (connections)
