# Applications
Every developer who wants to allow their smartphone application to communicate with the vehicle is required to register as a SmartDeviceLink Application. The SHAID service acts as the centralized datastore and synchronizer to ensure uniqueness across all SDL-enabled Applications and keep Vehicle OEMs up-to-date when a developer's application requirements or metadata change.

## Application Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `uuid` | String | The UUID of the application. Do not share this value with others! |
| `vendor_id` | Integer | The ID of the Vendor who owns this application. |
| `name` | String | The internal name of this application. |
| `description` | String | A brief description of what the application does. |
| `icon_url` | String | A URL to an icon of the application's branding. |
| `display_names` | String[] | An array of names which may be displayed as the application's name in the vehicle. |
| `status` | DEVELOPMENT<br/>REVIEW<br/>PRODUCTION | The status of the application. |
| `platform` | ANDROID<br/>IOS || The platform of the application. |
| `platform_id` | String | The package name or bundle ID of the application. |
| `can_background_alert` | Boolean | Whether or not the application needs to be able to create an alert when running in the background. |
| `can_steal_focus` | Boolean | Whether or not the application needs to be able to request to enter the foreground. |
| `category` | [Category](../../categories/overview) | A [category object](../../categories/overview) representing the category the application should be listed in. |
| `permissions` | [Permission[]](../../permissions/overview) | An array of [permission objects](../../permissions/overview), each containing the `id` of the permission the application uses and the `hmi_level` needed. |
| `countries` | [Country[]](../../countries/overview) | An array of [country objects](../../countries/overview), each containing the `id` of the country the application is available in. |
| `vendors` | [Vendor[]](../../vendors/overview) | An array of [vendor objects](../../vendors/overview), each containing the `id` of the vendor the application is granting read access to. |
