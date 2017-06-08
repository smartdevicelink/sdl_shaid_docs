# Categories
A SmartDeviceLink Application always has a category associated to it, chosen by the developer. The category may be used to group or filter applications on a vehicle's HMI, on a web-based directory of SmartDeviceLink Applications, and other user-accessible locations.

## Category Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `id` | Integer | The unique numerical ID of the category. |
| `display_name` | String | The user-friendly name of the category. |
| `is_selected` | Boolean | Whether or not the category is in use by the optionally provided context of an Application UUID. |
