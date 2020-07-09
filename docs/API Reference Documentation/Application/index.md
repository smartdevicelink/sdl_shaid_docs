## GET /application

Retrieve one or more SDL applications and metadata about them: their UUID (a unique identifier which should be kept private), the countries the application supports, the application category, and the data permissions the application requires access to.

**Parameters**

| in    | name                        | type                                                                                                                                                                                                | required | description                                                                                                                                                                                                                                                                                                                 | default            |
|-------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| query | uuid                        | string                                                                                                                                                                                              | false    | A comma-separated list of Application UUIDs. Find applications by their UUID.                                                                                                                                                                                                                                               |                    |
| query | version_id                  | string                                                                                                                                                                                              | false    | A comma-separated list of Application Version IDs. Find applications by specific version IDs.                                                                                                                                                                                                                               |                    |
| query | vendor_id                   | string                                                                                                                                                                                              | false    | A comma-separated list of Vendor IDs. Find applications owned by specific Vendors.                                                                                                                                                                                                                                          |                    |
| query | champion_assigned_vendor_id | string                                                                                                                                                                                              | false    | A comma-separated list of Vendor IDs. Find applications with specific assigned champion Vendors. Alternatively, find applications without an assigned champion Vendor by sending `null`. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will be ignored. |                    |
| query | champion_approval_status    | string: APPROVED, PENDING, DENIED                                                                                                                                                                   | false    | A comma-separated list of Champion Approval Statuses. Only retrieve applications matching the provided champion approval status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will be ignored.                                                         |                    |
| query | status                      | string: DEVELOPMENT, REVIEW, PRODUCTION                                                                                                                                                             | false    | A comma-separated list of Statuses. Only retrieve applications matching the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`.                                                                                 |                    |
| query | approval_status             | string: DENIED, PENDING, APPROVED                                                                                                                                                                   | false    | Only retrieve applications matching the provided SDLC approval status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `APPROVED`.                                                                                                         |                    |
| query | granted_vendor_id           | string                                                                                                                                                                                              | false    | A comma-separated list of Vendor IDs. Find applications granted read access to the given Vendor IDs. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will be ignored.                                                                                     |                    |
| query | not_granted_vendor_id       | string                                                                                                                                                                                              | false    | A comma-separated list of Vendor IDs. Find applications NOT granted read access to the given Vendor IDs. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will be ignored.                                                                                 |                    |
| query | platform                    | string: ANDROID, IOS, CLOUD, EMBEDDED                                                                                                                                                               | false    | Only retrieve applications matching the provided platform. Supports filtering on multiple platforms as a comma-separated list.                                                                                                                                                                                              |                    |
| query | country_iso                 | string                                                                                                                                                                                              | false    | Only retrieve applications built to support the provided country.                                                                                                                                                                                                                                                           |                    |
| query | category_id                 | integer                                                                                                                                                                                             | false    | Only retrieve applications in the provided category. See `GET /category` for a list of available values. Supports filtering on multiple categories as a comma-separated list.                                                                                                                                               |                    |
| query | allow_marketing             | boolean                                                                                                                                                                                             | false    | Only retrieve applications that explicitly allow or deny marketing/promotion of their application.                                                                                                                                                                                                                          |                    |
| query | include_deleted             | boolean                                                                                                                                                                                             | false    | Include applications in the response which are deleted.                                                                                                                                                                                                                                                                     | `false`            |
| query | include_blacklisted         | boolean                                                                                                                                                                                             | false    | Include applications in the response which are blacklisted by the SDLC.                                                                                                                                                                                                                                                     | `false`            |
| query | name                        | string                                                                                                                                                                                              | false    | Search for Applications containing the provided string in their name.                                                                                                                                                                                                                                                       |                    |
| query | query_type                  | string: ALL, LATEST                                                                                                                                                                                 | false    | Modifies the scope of the endpoint to query ALL versions of each application, the LATEST version of each application, or only the latest production version of each application (default).                                                                                                                                  |                    |
| query | has_entered_review          | boolean                                                                                                                                                                                             | false    | Only retrieve applications that are either currently in or have been reviewed (true) or have not yet entered review (false). Default null.                                                                                                                                                                                  |                    |
| query | is_in_catalog               | boolean                                                                                                                                                                                             | false    | Whether the app should appear in the App Catalog on smartdevicelink.com.                                                                                                                                                                                                                                                    |                    |
| query | is_homepage_app             | boolean                                                                                                                                                                                             | false    | Whether the app is eligible appear on the homepage smartdevicelink.com.                                                                                                                                                                                                                                                     |                    |
| query | is_oem_specific             | boolean                                                                                                                                                                                             | false    | Whether the app should appear in the OEM-specific section of the App Catalog.                                                                                                                                                                                                                                               |                    |
| query | limit                       | integer                                                                                                                                                                                             | false    | The maximum number of results to return. Default 50.                                                                                                                                                                                                                                                                        | `50`               |
| query | offset                      | integer                                                                                                                                                                                             | false    | The number of results to offset, for basic pagination.                                                                                                                                                                                                                                                                      | `0`                |
| query | sort_by                     | string: application.id, application.name, application.platform, application.status, application.approval_status, vendor.name, application.champion_approval_status, application.champion_updated_ts | false    | Which property to sort the results by.                                                                                                                                                                                                                                                                                      | `"application.id"` |
| query | sort_order                  | string: ASC, DESC                                                                                                                                                                                   | false    | How to order the results (in combination with `sort_by`).                                                                                                                                                                                                                                                                   | `"ASC"`            |

#### Response: 200

Application(s) retrieved! The request was successful and any matching applications are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - applications (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A
## PUT /application/approval/vendor

This operation changes the requesting OEM's `approval_status` property of an application version.

**Parameters**

| in   | name         | required | description                                   |
|------|--------------|----------|-----------------------------------------------|
| body | applications | true     | An array of Application OEM Approval objects. |

**Request Body**

- (object)
  - applications (array) (optional)
    - (object)
      - version_id (int64) A unique integer to identify the application version
      - approval_status (string: LIMITED, ACCEPTED) The OEM's selected status of the application version
      - notes (string) (optional) Notes by the OEM to be shared with the application developer

#### Response: 200

Application OEM approval status(es) updated! The application version(s) provided were successfully updated.

**Schema**

N/A

#### Response: 400

Invalid request. You probably tried to update an application version ID which you don't have access to.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A