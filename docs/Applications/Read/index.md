## Read Applications
Retrieve one or more SDL applications and metadata about them: their UUID (a unique identifier which should be kept private), the countries the application supports, the application category, and the data permissions the application requires access to.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v2/application

## Query Parameters
| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `uuid` | No | | Find a specific application by its UUID. |
| `limit` | No | 50 | The maximum number of results to return. Max 50. |
| `offset` | No | 0 | The number of results to offset, for basic pagination. |

## Behavioral Notes
* If no results are found, the request will succeed with an empty array of applications in the response.

## Response Codes
* `200`: Application(s) retrieved! The request was successful and any matching applications are returned in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example Response
```json
{
  "meta": {
    "request_id": "10ae97d7-c017-449a-bbc1-43d060010419",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "applications": [
      {
        "uuid": "fa317820-60d2-4149-a7be-53239430270b",
        "name": "App 1",
        "display_names": [
          "App One",
          "App 1"
        ],
        "platform": "ANDROID",
        "platform_app_id": "com.company.android.one",
        "status": "PRODUCTION",
        "can_background_alert": true,
        "can_steal_focus": true,
        "tech_email": "tech@company.com",
        "tech_phone": "2345678901",
        "default_hmi_level": "HMI_NONE",
        "created_ts": "2017-06-16T14:44:14.519Z",
        "updated_ts": "2017-06-16T14:44:14.519Z",
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
            "name": "Accelerator Pedal Position",
            "hmi_level": "HMI_FULL"
          },
          {
            "id": 20,
            "key": "driverBraking",
            "name": "Braking",
            "hmi_level": "HMI_BACKGROUND"
          }
        ],
        "category": {
          "id": 1,
          "name": "DEFAULT",
          "display_name": "Default"
        },
        "vendor": {
          "id": 1,
          "name": "SmartDeviceLink",
          "email": "person@example.com"
        }
      }
    ]
  }
}
```
