# loopback-component-storage-mongo2
[![Build Status](https://travis-ci.org/jdrouet/loopback-component-storage-mongo.svg)](https://travis-ci.org/jdrouet/loopback-component-storage-mongo)
[![codecov.io](https://codecov.io/github/jdrouet/loopback-component-storage-mongo/coverage.svg?branch=master)](https://codecov.io/github/jdrouet/loopback-component-storage-mongo?branch=master)
[![Dependency Status](https://david-dm.org/jdrouet/loopback-component-storage-mongo.svg)](https://david-dm.org/jdrouet/loopback-component-storage-mongo)

![codecov.io](https://codecov.io/github/jdrouet/loopback-component-storage-mongo/branch.svg?branch=master)

LoopBack storage mongo component provides Node.js and REST APIs to manage binary contents using Mongodb gridfs

## Installation

Install the storage component using npm:

```bash
  npm install --save git+https://git@github.com/nickgermaine/loopback-component-storage-mongo.git
```

## Using it

Edit you datasources.json and add the following part

```javascript
"gridfs": {
  "name": "gridfs",
  "connector": "loopback-component-storage-mongo",
  "host": "localhost",
  "port": 27017,
  "database": "test"
}
```

And the you can use it as a datasource of your model.

## API

Description                                                   | Container model method                    | REST URI
--------------------------------------------------------------|-------------------------------------------|--------------------------------------------
List all containers                                           | getContainers(callback)                   | GET /api/YOURMODEL
Get information about specified container                     | getContainer(container, callback)         | GET /api/YOURMODEL/:container
Create a new container                                        | createContainer(options, callback)        | PORT /api/YOURMODEL
Delete specified container                                    | destroyContainer(options, callback)       | DELETE /api/YOURMODEL/:container
List all files within specified container                     | getFiles(container, callback)             | GET /api/YOURMODEL/:container/files
Get information for specified file within specified container | getFile(container, file, callback)        | GET /api/YOURMODEL/:container/files/:file
Delete a file within a given container by name                | removeFile(container, file, callback)     | DELETE /api/YOURMODEL/:container/files/:file
Upload one or more files into the specified container         | upload(container, req, res, callback)     | POST /api/YOURMODEL/:container/upload
Download a file within specified container                    | download(container, file, res, callback)  | GET /api/YOURMODEL/:container/download/:file
View file                                                     | viewFile(container, file, res, callback)  | GET /api/YOURMODEL/:container/view/:file
