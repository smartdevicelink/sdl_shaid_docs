## Update Vendors
#### Requires admin privileges
Update one or more Vendors.

## HTTP Request
`PUT` https://shaid.smartdevicelink.com/api/v1/vendor

## JSON Body Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| vendors | Vendor[] | Yes | | An array of vendor objects. |

## Vendor Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| is_admin | Boolean | Whether or not the Vendor is an admin. |
| is_app_consumer | Boolean | Whether or not the Vendor is allowed to read applications via the API and appear as an OEM for a developer to choose to grant access to. |
| sdlc_member_level | Integer | The SDLC membership level of the Vendor, 1 being the highest. |
| name | String | The Vendor's name (either a person or a company). |
| email | String | The Vendor's email address. |
| icon_url | String | A URL of the Vendor's logo. |
| webhook_url | String | A URL of where the Vendor would like to get webhook requests when an Application is modified. |

## Response Codes
* `200`: Vendor(s) updated! The vendors provided were successfully updated and are returned in the response body.
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to create a vendor.

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
    "vendors": [
      {
        "id": 34,
        "name": "Nick Schwab",
        "email": "test@example.com",
        "is_admin": false,
        "is_app_consumer": false,
        "sdlc_member_level": 3,
        "webhook_url": "https://livio.io",
        "icon_url": null
      },
      {
        "id": 35,
        "name": "Edited Example OEM",
        "email": "example@oem.com",
        "is_admin": false,
        "is_app_consumer": true,
        "sdlc_member_level": 2,
        "webhook_url": "https://example.com/webhook",
        "icon_url": null
      }
    ]
}
```

#### Example Response
```json
{
  "meta": {
    "request_id": "0f12b0a6-5151-4c9f-8b8e-71b4becd4b08",
    "code": 201,
    "message": "Vendor(s) updated!"
  },
  "data": {
    "vendors": [
      {
        "id": 34,
        "name": "Nick Schwab",
        "email": "test@example.com",
        "is_admin": false,
        "is_app_consumer": false,
        "sdlc_member_level": 3,
        "webhook_url": "https://livio.io",
        "icon_url": null,
        "public_key": "c355858d-e0c1-4f66-8fab-61eb29c2d8e5",
        "secret_key": "c456d046-4185-4579-bf9c-93b36a24fa9b",
        "created_ts": "2017-05-24T15:42:21.631Z",
        "updated_ts": "2017-05-24T18:04:08.658Z"
      },
      {
        "id": 35,
        "name": "Edited Example OEM",
        "email": "example@oem.com",
        "is_admin": false,
        "is_app_consumer": true,
        "sdlc_member_level": 2,
        "webhook_url": "https://example.com/webhook",
        "icon_url": null,
        "public_key": "d36036c5-73c8-47b6-a3ae-bba4eaad7822",
        "secret_key": "5f30440b-badb-47ad-b79b-8dc6ef5b09c3",
        "created_ts": "2017-05-24T15:42:21.631Z",
        "updated_ts": "2017-05-24T18:04:08.660Z"
      }
    ]
  }
}
```
