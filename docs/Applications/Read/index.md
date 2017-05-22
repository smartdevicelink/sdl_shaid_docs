## Read Applications
Retrieve one or more SDL applications and metadata about them: their UUID (a unique identifier which should be kept private), the countries the application supports, the application category, and the data permissions the application requires access to.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/application

## Query Parameters
| Parameter | Requires Admin | Required | Default | Description |
|-----------|----------------|----------|---------|-------------|
| uuid | No | No | | Find a specific application by its UUID. |
| status | Yes | No | | Only retrieve applications matching the provided status (DEVELOPMENT, REVIEW, PRODUCTION). |
| limit | No | No | 50 | The maximum number of results to return. Max 50. |
| offset | No | No | 0 | The number of results to offset, for basic pagination. |

## Behavioral Notes
* Non-administrative vendors always query applications with `PRODUCTION` status, regardless of the provided parameter.
* Non-administrative vendors always query applications that they have been given explicit permission to view by application developers. All other applications will not appear in results.
* If no results are found, the request will succeed with an empty array of applications in the response.

## Example Response
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
