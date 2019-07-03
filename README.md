[![Coverage Status](https://coveralls.io/repos/github/mrdefenestrator/jsonapi-store-cosmos-table/badge.svg?branch=master)](https://coveralls.io/github/mrdefenestrator/jsonapi-store-cosmos-table?branch=master)
[![Build Status](https://travis-ci.org/mrdefenestrator/jsonapi-store-cosmos-table.svg?branch=master)](https://travis-ci.org/mrdefenestrator/jsonapi-store-cosmos-table)
[![npm version](https://badge.fury.io/js/jsonapi-store-mongodb.svg)](http://badge.fury.io/js/jsonapi-store-mongodb)
[![Code Climate](https://codeclimate.com/github/mrdefenestrator/jsonapi-store-cosmos-table/badges/gpa.svg)](https://codeclimate.com/github/mrdefenestrator/jsonapi-store-cosmos-table)
[![Dependencies Status](https://david-dm.org/mrdefenestrator/jsonapi-store-cosmos-table.svg)](https://david-dm.org/mrdefenestrator/jsonapi-store-cosmos-table)

# jsonapi-store-mongodb

`jsonapi-store-mongodb` is a MongoDB backed data store for [`jsonapi-server`](https://github.com/holidayextras/jsonapi-server).

This project conforms to the specification laid out in the [jsonapi-server handler documentation](https://github.com/holidayextras/jsonapi-server/blob/master/documentation/handlers.md).

## Usage

```javascript
var MongoStore = require("jsonapi-store-mongodb");

jsonApi.define({
  resource: "comments",
  handlers: new MongoStore({
    url: "mongodb://localhost:27017/jsonapi",
  })
});
```

## Features

* Search, Find, Create, Delete, Update
* Efficient lookups via appropriate indexes
* Database layer filtering, pagination and sorting

## Getting to Production

Getting this data store to production is really simple:

1. Bring up your MongoDB stack.
2. Create any indexes you may need (this is optional, this module will automatically ensure indexes exist on relationships, however you might want to add an index to an attribute you intend on querying aggressively).
3. Deploy your code.
4. Celebrate.

When making schema changes, deploy away and carry on. If the changes aren't backwards compatible, you may want to run a job to ensure all old (existing) records conform to the new schema. If they don't conform to the new schema, they will be dropped by jsonapi-server's validation layer.
