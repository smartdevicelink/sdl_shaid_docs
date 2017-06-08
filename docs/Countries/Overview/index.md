# Countries
A SmartDeviceLink Application supports operating in one or more countries, chosen by the developer.

## Country Object Model
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| `id` | Integer | The unique numerical ID of the country. |
| `iso` | String | The 2-character ISO 3166-2 code of the country. |
| `name` | String | The user-friendly english name of the country. |
| `is_selected` | Boolean | Whether or not the country is in use by the optionally provided context of an Application UUID. |
