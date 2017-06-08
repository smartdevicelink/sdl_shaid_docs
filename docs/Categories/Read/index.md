# Read Categories
Retrieve a list of supported categories an Application can choose to be associated with. An Application may only be associated to one category.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/category

## Query Parameters
| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `application_uuid` | No | | Check each Category against the given Application to see if it is currently chosen by the Application, returned by the `is_selected` attribute. |

## Example Response

```json
{
  "meta": {
    "request_id": "1ee12acd-257f-4ed8-85d7-b20cd96e67a5",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "categories": [
      {
        "id": 8,
        "display_name": "Background Process",
        "is_selected": false
      },
      {
        "id": 2,
        "display_name": "Communication",
        "is_selected": false
      },
      {
        "id": 1,
        "display_name": "Default",
        "is_selected": false
      },
      {
        "id": 6,
        "display_name": "Information",
        "is_selected": false
      },
      {
        "id": 3,
        "display_name": "Media",
        "is_selected": true
      },
      {
        "id": 4,
        "display_name": "Messaging",
        "is_selected": false
      },
      {
        "id": 5,
        "display_name": "Navigation",
        "is_selected": false
      },
      {
        "id": 7,
        "display_name": "Social",
        "is_selected": false
      },
      {
        "id": 10,
        "display_name": "System",
        "is_selected": false
      },
      {
        "id": 9,
        "display_name": "Testing",
        "is_selected": false
      }
    ]
  }
}
```
