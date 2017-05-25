## Update Applications
#### Requires admin privileges
Update one or more applications. This operation performs a *full overwrite* of the application's metadata, therefore you must send all metadata about an application, even if a particular attribute hasn't changed. Partial updates are performed via PATCH, which is currently unsupported.

## HTTP Request
`PUT` https://shaid.smartdevicelink.com/api/v1/application

## JSON Body Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| `applications` | Application[] | Yes | | An array of application objects. |

## Application Object Model
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| `uuid` | String | Yes | | The UUID of the application to update. |
| `vendor_id` | Integer | Yes | | The ID of the Vendor who owns this application. |
| `name` | String | Yes |  | The internal name of this application. |
| `description` | String | No | | A brief description of what the application does. |
| `icon_url` | String | No | | A URL to an icon of the application's branding. |
| `display_names` | String[] | Yes | | An array of names which may be displayed as the application's name in the vehicle. |
| `status` | DEVELOPMENT<br/>REVIEW<br/>PRODUCTION | Yes | | The status of the application. |
| `platform` | ANDROID<br/>IOS | Yes | | The platform of the application. |
| `platform_id` | String | Yes | | The package name or bundle ID of the application. |
| `can_background_alert` | Boolean | No | `FALSE` | Whether or not the application needs to be able to create an alert when running in the background. |
| `can_steal_focus` | Boolean | No | `FALSE` | Whether or not the application needs to be able to request to enter the foreground. |
| `permissions` | Object[] | Yes | | An array of permission objects, each containing the `id` of the permission the application uses and the `hmi_level` needed. |
| `countries` | Object[] | Yes | | An array of country objects, each containing the `id` of the country the application is available in. |
| `vendors` | Object[] | Yes | | An array of vendor objects, each containing the `id` of the vendor the application is granting read access to. |

## Response Codes
* `200`: Application(s) updated! The applications provided were successfully updated and are returned in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to update an application.

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
        "uuid": "1ffc60c2-bed8-40d8-a6ca-5237ab025404",
        "name": "Edited App 1",
        "display_names": [
          "hello",
          "hello again",
          "hello good friend"
        ],
        "description": "A great app used by many.",
        "icon_url": null,
        "vendor_id": 1,
        "platform": "ANDROID",
        "platform_app_id": "a11",
        "category_id": 1,
        "status": "DEVELOPMENT",
        "can_background_alert": true,
        "can_steal_focus": true,
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
    "request_id": "75912800-2217-4794-a175-0456f48e00df",
    "code": 200,
    "message": "Application(s) updated!"
  },
  "data": {
    "applications": [
      {
        "uuid": "1ffc60c2-bed8-40d8-a6ca-5237ab025404",
        "vendor_id": 1,
        "name": "Edited App 1",
        "display_names": [
          "hello",
          "hello again",
          "hello good friend"
        ],
        "description": "A great app used by many.",
        "icon_url": null,
        "platform": "ANDROID",
        "platform_app_id": "a11",
        "category_id": 1,
        "can_background_alert": true,
        "can_steal_focus": true,
        "status": "DEVELOPMENT",
        "updated_ts": "2017-05-23T15:26:48.978Z",
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
