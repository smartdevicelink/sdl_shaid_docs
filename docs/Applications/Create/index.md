## Create Applications
Create an application with a custom UUID, or automatically generate a new UUID.

## HTTP Request
`POST` https://shaid.smartdevicelink.com/api/v1/application

## JSON Body Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| uuid | String | No | `auto-generate` | The UUID of the new application. Leave blank/null to auto-generate a UUID. |
| vendor_id | Integer | Yes | | The ID of the Vendor who owns this application. |
| name | String | Yes |  | The internal name of this application. |
| description | String | No | | A brief description of what the application does. |
| icon_url | String | No | | A URL to an icon of the application's branding. |
| display_names | String[] | Yes | | An array of names which may be displayed as the application's name in the vehicle. |
| status | ENUM(DEVELOPMENT, REVIEW, PRODUCTION) | Yes | | The status of the application. |
| platform | ENUM(ANDROID,IOS) | Yes | | The platform of the application. |
| platform_id | String | Yes | | The package name or bundle ID of the application. |
| can_background_alert | Boolean | No | `FALSE` | Whether or not the application needs to be able to create an alert when running in the background. |
| can_steal_focus | Boolean | No | `FALSE` | Whether or not the application needs to be able to request to enter the foreground. |
| permissions | Object[] | Yes | | An array of permission objects, each containing the `id` of the permission the application uses and the `hmi_level` needed. |
| countries | Object[] | Yes | | An array of country objects, each containing the `id` of the country the application is available in. |
| vendors | Object[] | Yes | | An array of vendor objects, each containing the `id` of the vendor the application is granting read access to. |

## Response Codes
* `201`: Application(s) created! The applications provided were successfully created and are returned in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to create an application with an auto-generated UUID.

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
            "name": "Two App",
            "description": null,
            "icon_url": null,
            "display_names": ["App Two", "Application Two"],
            "platform_app_id": "com.demo.app.two",
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

#### Example Response
```json
{
  "meta": {
    "request_id": "c33c3846-c898-4820-ae50-191b83bed5f3",
    "code": 201,
    "message": "Application(s) created!"
  },
  "data": {
    "applications": [
      {
        "uuid": "82e17947-c83b-42ed-aef4-48ea2702e597",
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
        "updated_ts": "2017-05-22T21:28:33.329Z",
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
}
```
