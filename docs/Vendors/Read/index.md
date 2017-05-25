## Read Vendors
#### Requires admin privileges
Retrieve information about one or more vendors.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/vendor

## Query Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| `id` | Integer | No | | The specific ID of a Vendor to retrieve. |
| `application_uuid` | String | No | | The application UUID to query in the context of to see if the Vendor has been granted read permissions by the application developer. |
| `sdlc_member_level` | Integer | No | | Limit the results to Vendors with this SDLC membership level. |
| `is_admin` | Boolean | No | | Limit the results to Vendors that either are or are not explicitly administrators. |
| `is_app_consumer` | Boolean | No | | Limit the results to Vendors that either are or are not explicitly app consumers. |
| `public_key` | String | No | | Find the Vendor associated with this public_key. The secret_key parameter must also be provided for this to work. |
| `secret_key` | String | No | | Find the Vendor associated with this secret_key. The public_key parameter must also be provided for this to work. |
| `limit` | No | No | 50 | The maximum number of results to return. Max 50. |
| `offset` | No | No | 0 | The number of results to offset, for basic pagination. |

## Vendor Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `is_admin` | Boolean | Whether or not the Vendor is an admin. |
| `is_app_consumer` | Boolean | Whether or not the Vendor is allowed to read applications via the API and appear as an OEM for a developer to choose to grant access to. |
| `sdlc_member_level` | Integer | The SDLC membership level of the Vendor, 1 being the highest. |
| `name` | String | The Vendor's name (either a person or a company). |
| `email` | String | The Vendor's email address. |
| `icon_url` | String | A URL of the Vendor's logo. |
| `webhook_url` | String | A URL of where the Vendor would like to get webhook requests when an Application is modified. |
| `is_selected` | Boolean | Whether or not the Vendor is selected as an OEM allowed to see the Application, when queried in the context of a specific Application. |

## Response Codes
* `200`: Vendor(s) queried! The vendors matching the request are in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to read all vendors that are app consumers.

#### Request Headers
```json
{
    "Content-Type": "application/json",
    "public_key": "abc123",
    "secret_key": "s3cr3t"
}
```

#### HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/vendor?is_app_consumer=true

#### Example Response
```json
{
  "meta": {
    "request_id": "f3d6d4c2-f467-4d61-8e66-afcfe2d2d553",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "vendors": [
      {
        "id": 35,
        "name": "Example OEM",
        "email": "example@oem.com",
        "is_admin": false,
        "is_app_consumer": true,
        "sdlc_member_level": 2,
        "webhook_url": "https://example.com/webhook",
        "icon_url": null,
        "public_key": "d36036c5-73c8-47b6-a3ae-bba4eaad7822",
        "secret_key": "5f30440b-badb-47ad-b79b-8dc6ef5b09c3",
        "created_ts": "2017-05-24T15:42:21.638Z",
        "updated_ts": "2017-05-24T15:42:21.638Z"
      }
    ]
  }
}
```
