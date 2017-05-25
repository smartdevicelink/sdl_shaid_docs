# Vendors
Every developer who wants to allow their smartphone application to communicate with the vehicle and any OEM who wants to synchronize SDL applications with their system is required to register as a Vendor. All SDL Applications are required to be associated with a Vendor, and application developers select which "app consumer" Vendors have read access to their applications.

A Vendor may use SHAID APIs using their `public_key` and `secret_key` if they have been flagged as either `is_admin` or `is_app_consumer`.

## Vendor Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `id` | Integer | The ID of the Vendor. |
| `is_admin` | Boolean | Whether or not the Vendor is an admin. |
| `is_app_consumer` | Boolean | Whether or not the Vendor is allowed to read applications via the API and appear as an OEM for a developer to choose to grant access to. |
| `sdlc_member_level` | Integer | The SDLC membership level of the Vendor, 1 being the highest. |
| `name` | String | The Vendor's name (either a person or a company). |
| `email` | String | The Vendor's email address. |
| `icon_url` | String | A URL of the Vendor's logo. |
| `webhook_url` | String | A URL of where the Vendor would like to get webhook requests when an Application is modified. |
| `public_key` | String | The Vendor's API public_key. |
| `secret_key` | String | The Vendor's API secret_key. |
| `is_selected` | Boolean | Whether or not the Vendor is selected as an OEM allowed to see the Application, when queried in the context of a specific Application. |
