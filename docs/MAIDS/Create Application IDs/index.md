# Create Application IDs
Generate one or more new application IDs.  After a successful request, this ID is guaranteed to be unique across the entire SDL ecosystem.

## Request
Make a ```POST``` request to ```/maids/0/appids``` with any of the following body parameters.

| Body Parameters | Data Type | Required | Default Value| Description |
|-----------|------|----------|---------|-------------|
| numOfIds | Number | No | ```1``` | Number of application IDs to generate. Using ridiculous values such as ```{ numOfIds: 9999999 }``` may result in your API key getting revoked. |

## Response
For a successful request, an array of [application ID objects]() will be returned in the ```data``` field.

## Example
The following example shows how to create three new application IDs.

### Request
```json
"Headers": {
    "Authorization": "MyAccessToken",
    "Content-Type": "application/json"
}
```

```
POST https://shaid.smartdevicelink.com/maids/0/appids
```

```json
"Body": {
  "numOfIds": 3
}
```

### Response
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
