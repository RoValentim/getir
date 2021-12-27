# Simple RESTfull API Assignment
This is a RESTful API with two endpoints.
1. One of them that fetches the data in the provided MongoDB collection and returns the results in the requested format.
2. Second endpoint is to create(POST) and fetch(GET) data from an in-memory storage.


## Pre requsites
- Golang (tested on version 1.75.5) for the application and Unit Tests
https://go.dev/doc/install

- Newman for End To End tests
https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/


# Installation
Clone the repository and once inside the new directory, get inside src:
```
cd src
```
You can build or just run as any other Golang program, the main entrance of the project is the file restful.go, e.g.:
```
go run restful.go
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
