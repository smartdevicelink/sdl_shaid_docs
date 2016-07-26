# Register Application IDs
Add one or more existing application IDs to the registry.  After a successful request, these IDs are guaranteed to be unique across the entire SDL ecosystem.

## Request
Make a ```POST``` request to ```/maids/0/appids/register``` with any of the following body parameters.

| Body Parameters | Data Type | Required | Default Value | Description |
|-----------|------|----------|---------|-------------|
| ids | Array of Strings | Yes | ```[]``` | A list of application IDs to be registered. |

## Response
For a successful request, an array of [application ID objects]() will be returned in the response field.

## Example
The following example shows how to register three application IDs.

### Request
```json
"Headers": {
    "Authorization": "MyAccessToken",
    "Content-Type": "application/json"
}
```

```
POST https://shaid.smartdevicelink.com/maids/0/appids/register
```

```json
"Body": {
  "ids": [
    "AF12ADK2L2BSDL",
    "FEWLB1101IAJESD",
    "HHWOEK7SNBL1912G"
  ]
}
```

### Response
```json
{
  "response": [{
    "id": "AF12ADK2L2BSDL",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }, {
    "id": "FEWLB1101IAJESD",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }, {
    "id": "HHWOEK7SNBL1912G",
    "createdBy": "321516981351381613215",
    "createdOn": "2016-07-15T20:49:59.130Z"
  }]
}
```
