# Applications
Every developer who wants to allow their smartphone application to communicate with the vehicle is required to register as a SmartDeviceLink Application. The SHAID service acts as the centralized datastore and synchronizer to ensure uniqueness across all SDL-enabled Applications and keep Vehicle OEMs up-to-date when a developer's application requirements or metadata change.

## Application Object Model
| Attribute | Data Type | Required | Default | Description |
|-----------|-----------|----------|---------|-------------|
| `uuid` | String | No | `auto-generated` | The UUID of the application. Do not share this value with others! |
| `vendor` | [Vendor](../../vendors/overview) | Yes | | A Vendor object containing the `id` of the Vendor who owns this application. |
| `tech_email` | String | No | | An email address of the Vendor's (optional) technical contact for this application. |
| `tech_phone` | String | No | A phone number of the Vendor's (optional) technical contact for this application. |
| `name` | String | Yes | | The internal name of this application. |
| `description` | String | No | | A brief description of what the application does. |
| `icon_url` | String | No | | A URL to an icon of the application's branding. |
| `display_names` | String[] | Yes | | An array of names which may be displayed as the application's name in the vehicle. |
| `default_hmi_level` | HMI_NONE<br/>HMI_BACKGROUND<br/>HMI_LIMITED<br/>HMI_FULL | No | HMI_NONE | The HMI Level the application expects to open with. |
| `status` | DEVELOPMENT<br/>REVIEW<br/>PRODUCTION | Yes | | The status of the application. |
| `platform` | ANDROID<br/>IOS | Yes | | The platform of the application. |
| `platform_id` | String | Yes | | The package name or bundle ID of the application. |
| `can_background_alert` | Boolean | No | `false` | Whether or not the application needs to be able to create an alert when running in the background. |
| `can_steal_focus` | Boolean | No | `false` | Whether or not the application needs to be able to request to enter the foreground. |
| `category` | [Category](../../categories/overview) | Yes | | A [category object](../../categories/overview) containing an `id` of the category the application should be listed in. |
| `permissions` | [Permission[]](../../permissions/overview) | No | `[]` | An array of [permission objects](../../permissions/overview), each containing the `id` of the permission the application uses and the `hmi_level` needed. |
| `countries` | [Country[]](../../countries/overview) | No | `[]` | An array of [country objects](../../countries/overview), each containing the `id` of the country the application is available in. |
| `vendors` | [Vendor[]](../../vendors/overview) | No | `[]` | An array of [vendor objects](../../vendors/overview), each containing the `id` of the vendor the application is granting read access to. |
