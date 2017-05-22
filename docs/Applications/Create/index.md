## Create Applications
Create an application with a custom UUID, or automatically generate a new UUID.

## HTTP Request
`POST` https://shaid.smartdevicelink.com/api/v1/application

## JSON Body Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|----------------|----------|---------|-------------|
| uuid | String | No | `auto-generate` | The UUID of the new application. Leave blank/null to auto-generate a UUID. |
| vendor_id | Integer | Yes | | The ID of the Vendor who owns this application. |
| name | String | Yes |  | The internal name of this application. |
| display_names | String[] | Yes | `[]` | An array of names which may be displayed as the application's name in the vehicle. |
| status | ENUM(DEVELOPMENT,REVIEW,PRODUCTION) | Yes | | The status of the application. |
| platform | ENUM(ANDROID,IOS) | Yes | | The platform of the application. |
| platform_id | String | Yes | | The package name or bundle ID of the application. |
| can_background_alert | Boolean | No | FALSE | Whether or not the application needs to be able to create an alert when running in the background. |
| can_steal_focus | Boolean | No | FALSE | Whether or not the application needs to be able to request to enter the foreground. |
| permissions | Object[] | Yes | | An array of permission objects, each containing the `id` of the permission the application uses and the `hmi_level` needed. |
| countries | Object[] | Yes | | An array of country objects, each containing the `id` of the country the application is available in. |
| vendors | Object[] | Yes | | An array of vendor objects, each containing the `id` of the vendor the application is granting read access to. |

## Response Codes
* `201`: Application(s) created! The applications provided were successfully created and are returned in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to create an application with an auto-generated UUID.
`POST` https://shaid.smartdevicelink.com/api/v1/application

#### Request Headers
```json
{
    "Content-Type": "application/json",
    "public_key": "abc123",
    "secret_key": "s3cr3t"
}
```

#### Request Body
```json
{
    "applications": [
        {
            "uuid": null,
            "vendor_id": 1,
            "name": "App 1",
            "display_names": ["App 1", "App One", "Application 1", "Application One"],
            "platform_app_id": "com.demo.app.one",
            "platform": "ANDROID",
            "category_id": 1,
            "can_background_alert": true,
            "can_steal_focus": true,
            "status": "DEVELOPMENT",
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
            ]
        }
    ]
}
```

### Example Response
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
            "App 1",
            "App One",
            "Application 1",
            "Application One"
        ],
        "vendor_id": 1,
        "platform": "ANDROID",
        "platform_app_id": "com.demo.app.one",
        "status": "DEVELOPMENT",
        "can_background_alert": true,
        "can_steal_focus": true,
        "created_ts": "2017-05-22T19:35:36.308Z",
        "updated_ts": "2017-05-22T19:35:36.308Z",
        "countries": [
          {
            "id": 1
          },
          {
            "id": 2
          }
        ],
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
