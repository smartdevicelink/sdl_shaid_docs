# API Responses
Each API response follows typical RESTful patterns and returns a JSON response body, unless otherwise specified.

## API Behavior
API endpoints which support multi-entity operations (e.g. creating multiple Applications in a single request) are *"all-or-nothing"*, meaning that if a single entity fails the operation or is malformed, the whole request will fail and no changes will be made.

In the event of an HTTP 400 error, the response `data` object will contain information about the failing entities.

In the event of an HTTP 2XX response, the response `data` object will contain information about the successful entities.

## Headers
The following is a list of possible response headers.

| Header Parameter | Type | Required | Default | Description |
|------------------|------|----------|---------|-------------|
| `Content-Type` | String | Yes | ```application/json; charset=utf-8``` | Unless otherwise specified, the default value will be returned. |


## Meta Object Model
Each JSON response includes a `meta` object, containing basic information about the result of the request.

| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `request_id` | String | A unique identifier representing the specific request. |
| `code` | Integer | The HTTP response code of the result. |
| `message` | String | A short textual summary of the result. |

## Data Object Model
Each JSON response includes a `data` object, containing the full outcome of the result. The attributes within the `data` object vary upon the entity you're operating on.

## Errors
The ```errors``` attribute stores errors that occurred during a request.  When present the data type is always an array of error objects.

#### Error Object Model
| Attribute | Data Type | Description |
|------------------|------|----------|---------|-------------|
| `property` | String | The attribute key of the erroneous data. |
| `message` | String | A human-readable error message describing why the associated attribute was erroneous. |

## Example Success Response Structure
The following shows an example success response on an operation against Applications. Please see the example response in each documented REST endpoint for a more detailed view of how each entity operation behaves.
```json
{
  "meta": {
    "request_id": "2d535fcc-a92a-4036-8678-9541f9bffcfb",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "applications": [
      {
        "uuid": "269e4b37-8cf4-4e5d-87c0-d8ebc84449a1",
        "name": "App 1",
        "display_names": [
          "hello"
        ],
        "vendor_id": 1,
        "platform": "ANDROID",
        "platform_app_id": "a11",
        "status": "DEVELOPMENT",
        "can_background_alert": true,
        "can_steal_focus": true,
        "created_ts": "2017-05-22T19:35:36.308Z",
        "updated_ts": "2017-05-22T19:35:36.308Z",
        "countries": [
          {
            "id": 1,
            "iso": "AD",
            "name": "Andorra"
          },
          {
            "id": 2,
            "iso": "AE",
            "name": "United Arab Emirates"
          }
        ],
        "permissions": [
          {
            "id": 18,
            "key": "accPedalPosition",
            "name": "Accelerator Pedal Position"
          },
          {
            "id": 20,
            "key": "driverBraking",
            "name": "Braking"
          }
        ],
        "category": {
          "id": 1,
          "name": "DEFAULT",
          "display_name": "Default"
        }
      }
    ]
  }
}
```

## Example Failure Response Structure
The following shows an example failed response on an operation against Applications. Please see the example response in each documented REST endpoint for a more detailed view of how each entity operation behaves.
```json
{
  "meta": {
    "request_id": "c7650cd1-7e54-422b-9d17-e248d14f3049",
    "code": 400,
    "message": "Applications NOT created. The returned applications encountered an error."
  },
  "data": {
    "applications": [
      {
        "uuid": "66f2f14b-aff2-492e-96b1-215fe961d78b",
        "vendor_id": 1,
        "name": "Two App",
        "display_names": [
          "App Two",
          "Application Two"
        ],
        "description": null,
        "icon_url": null,
        "platform": "ANDROID",
        "platform_app_id": "com.demo.app.two",
        "category_id": 1,
        "can_background_alert": true,
        "can_steal_focus": true,
        "status": "DEVELOPMENT",
        "updated_ts": "2017-05-24T19:48:00.672Z",
        "permissions": [
          {
            "id": 18,
            "hmi_level": "HMI_FULL"
          },
          {
            "id": 20,
            "hmi_level": "HMI_BACKGROUND"
          }
        ],
        "countries": [
          {
            "id": 1
          },
          {
            "id": 2
          }
        ],
        "vendors": [
          {
            "id": 1
          },
          {
            "id": 2
          }
        ],
        "errors": [
          {
            "property": "platform_app_id",
            "message": "This package name/bundle ID is already in use by another application"
          }
        ]
      }
    ]
  }
}
```

## Timestamps
SHAID uses [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) to store and return timestamp values.

#### Example Timestamp
```
2016-07-15T20:49:59.130Z
```
