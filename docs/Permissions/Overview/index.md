# Permissions
A SmartDeviceLink Application requires certain data permissions about the mobility experience. These permissions are chosen by the developer and should be synchronized with OEM systems or SDL Policy Server implementations.

## Permission Category Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `id` | Integer | The unique numerical ID of the permission category. |
| `name` | String | The user-friendly english name of the permission category. |
| `description` | String | The user-friendly description of the permission category. |
| `permissions` | Permission[] | An array of Permission objects associated with the permission category. |

## Permission Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `id` | Integer | The unique numerical ID of the country. |
| `key` | String | SDL Core's unique text string to identify the permission. |
| `name` | String | The user-friendly english name of the permission. |
| `selected_hmi_level` | HMI_NONE<br/>HMI_BACKGROUND<br/>HMI_LIMITED<br/>HMI_FULL | The HMI access level requested by the Application in context. |
