# API Responses
Each API response follows typical RESTful patterns and returns a JSON response body, unless otherwise specified.  By default the API response data is packaged in an object, called an envelope, along side additional meta data.  This meta data could include errors, paging information, etc.  

## Headers
The following is a list of possible response headers.

| Header Parameter | Type | Required | Default | Description |
|------------------|------|----------|---------|-------------|
| Content-Type | String | Yes | ```application/json; charset=utf-8``` | Unless otherwise specified, the default value will be returned. |


## Response Envelope
A response from the server will contain the response data as well as some meta data.  The meta data can be used to help make future requests to the server (e.g. paging) or diagnose an error.  The following top level attributes are possible, but none of them are guaranteed to be in each response.

| Attribute | Data Type | Description |
|-----------|------|----------|---------|-------------|
| ```errors``` | Array of Objects | Stores one or more errors that occurred during the request. |
| ```data``` | Varies | Stores the response data for a successful, or partially successful, request. |
| ```id``` | String | A unique identifier for the request and response throughout the SHAID micro-services |

### Response Data
The ```data``` attribute stores response data related to each successful request.  Some requests, such as creating multiple application IDs, may allow you to perform several operations in batch.  In these cases the ```data``` attribute may contain a few successful responses even though some operations failed.  The failed batched operations will instead have error messages in the ```errors``` field.  

The data type of the ```data``` attribute varies and you should reference each API's endpoint documentation for more details.

#### Example Response Data
The following shows a successful response to a request to create three new application IDs.
```json
{
  "data": [{
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
  }],
  "id": "35742a42-6abf-47c2-891d-ad3399e83399"
}
```

#### Example Failed Batch Response Data
The following shows a response to a partially successful batch request to register three new application IDs.  In this example, the id ```1``` already exists.
```json
{
  "data": [{
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
  }],
  "id": "35742a42-6abf-47c2-891d-ad3399e83399"
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

# Date-Time
Date-Time values can seem confusing or complicated, so let's keep it [simple](https://xkcd.com/1179/).  All date-time values sent to or from SHAID are in the string format described below.

!!! IMPORTANT
All date-time values are stored as ```Strings```.
!!!

## ISO 8601
SHAID uses [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) to display date-time values.

All date-time values are formatted as ```date``` + ```T``` + ```time```.
```
2016-07-15T20:49:59.130Z
```

### Dates
Dates are written as ```Year-Month-Day``` in the format ```YYYY-MM-DD```, with the month and day values zero padded.
```
2016-07-15
```

### Time
Times are written using the [24-hour clock system](https://en.wikipedia.org/wiki/24-hour_clock).  They include ```Hours:Minutes:Seconds.Milliseconds``` in the format ```hh:mm:ss.sss```. The hours, minutes, and seconds are single zero padded, while the milliseconds have a double zero padding.  As indicated above a ```T``` prefixes the time value separating the date from the time.  A ```Z``` at the end of the time value indicates the [+0 GMT](http://wwp.greenwichmeantime.com/info/iso.htm) timezone.

!!! IMPORTANT
All times are in the [+0 GMT](http://wwp.greenwichmeantime.com/info/iso.htm) timezone.
!!!

```
T20:49:59.130Z
```

### Date-Time Example
The time for July 15th 2016 at 8:49:59 pm, and 130 milliseconds, in the timezone of +0 GMT would look like:
```
2016-07-15T20:49:59.130Z
```
