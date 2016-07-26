# API Responses
Each API response follows typical RESTful patterns and return JSON response bodies, unless otherwise specified.  By default a response's information is packaged in an object, called an envelope, along side additional meta data.  This meta data could include errors, paging information, etc.  

## Headers
The following is a list of possible response headers.

| Header Parameter | Type | Required | Default | Description |
|------------------|------|----------|---------|-------------|
| Content-Type | String | Yes | ```application/json; charset=utf-8``` | Unless otherwise specified, the default value will be returned. |


## Response Envelope
A response from the server will contain the expected data as well as some meta data.  The meta data can be used to help make future requests to the server, such as paging, or diagnose errors.  The following top level attributes are possible, but none of them are guaranteed to be in each response.

| Attribute | Data Type | Description |
|------------------|------|----------|---------|-------------|
| ```errors``` | Array of Objects | Stores one or more errors that occurred during the request. |
| ```response``` | Varies | Stores the response data for a successful, or partially successful, request. |

### Response Data
The ```response``` attribute stores data related to each successful request.  Some requests, such as creating multiple application IDs, may allow you to perform several requests in batch.  In these cases the ```response``` attribute may only store the successful requests, while other's in the batch failed.  The data type of the ```response``` attribute varies and you should reference each API's endpoint documentation for more details.

#### Example Response Data
The following shows a successful response to a request to create three new application IDs.
```json
{
  "response": [{
    "id": "735035aa-c279-406d-a33e-e1871ebf6629",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }, {
    "id": "301a82b4-a2da-4763-9c54-1ddf54ef6c27",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }, {
    "id": "d228298e-1ed6-4c99-9577-7b48b908872c",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }]
}
```

#### Example Failed Batch Response Data
The following shows a response to a partially successful batch request to register three new application IDs.  In this example, the id ```1``` already exists.
```json
{
  "response": [{
    "id": "2",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }, {
    "id": "3",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }],
  "errors": [{
    "message": "An application ID with a value of '1' has already been registered.",
    "code": "server.400.duplicateappid",
    "referenceData": {
      "createdBy":"1",
      "createdOn":"2016-07-15T20:49:59.130Z",
      "id":"1",
      "isGenerated":false
    },
    "messageData": {
      "id": "1"
    }
  }]
}
```

### Errors
The ```errors``` attribute stores errors that occurred during a request.  When present the data type is always an array of error objects.

#### Error Objects
An error object can include any of the following attributes.

| Attribute | Data Type | Required | Description |
|------------------|------|----------|---------|-------------|
| ```message``` | String | Yes | A human readable error message.  |
| ```messageData``` | Object | No | Dynamic data values used by the error message.  The ```code``` and ```messageData``` is used by the server to create the human human readable error ```message```. |
| ```code``` | String | No | A machine readable string, aka locale, for the error message.  |
| ```referenceData``` | Varies | No | Data that caused or is related to the error. |
| ```stack``` | String | No | A stack trace of for the error. |

#### Example Error Object
The following is an example error for a request to register a duplicate application ID value of ```1```.  Notice how the ```code``` and ```messageData``` are combined to create the human readable error.   

```json
{
  "errors": [{
    "message": "An application ID with a value of '1' has already been registered.",
    "code": "server.400.duplicateappid",
    "referenceData": {
      "createdBy":"1",
      "createdOn":"2016-07-25T20:12:22.818Z",
      "id":"1",
      "isGenerated":false
    },
    "messageData": {
      "id": "1"
    }
  }]
}
```
