## Delete Applications *requires admin privileges*
Delete one or more applications.

## HTTP Request
`DELETE` https://shaid.smartdevicelink.com/api/v1/application

## JSON Body Parameters
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| applications | Application[] | Yes | | An array of application objects. |

## Application Object Model
| Parameter | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| uuid | String | Yes | | The UUID of the application to delete. |

## Response Codes
* `200`: Application(s) deleted!
* `400`: Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.
* `500`: Internal server error.

## Example
The following example shows how to delete an application.

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
            "uuid": "1ffc60c2-bed8-40d8-a6ca-5237ab025404"
        }
    ]
}
```

#### Example Response
```json
{
  "meta": {
    "request_id": "03727d6a-3ca8-468b-b4cd-1f956d5abe7d",
    "code": 200,
    "message": "Application(s) deleted!"
  },
  "data": {
  }
}
```
