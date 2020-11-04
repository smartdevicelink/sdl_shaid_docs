## GET /permission

Retrieve a list of supported permissions an Application can request access to. An Application can use many permissions. A SmartDeviceLink Application requires certain data permissions about the mobility experience. These permissions are chosen by the developer and should be synchronized with OEM systems or SDL Server implementations.

**Parameters**

| in    | name             | type                                    | required | description                                                                                                                                                                                                            | default |
|-------|------------------|-----------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| query | application_uuid | string                                  | false    | Check each permission against the given Application to see if it is currently in use by the Application, returned by the hmi_level attribute.                                                                          |         |
| query | status           | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only match against the given `application_uuid` in the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`. |         |
| query | include_hidden   | boolean                                 | false    | Set to `true` to return permissions which are not presented to app developers as selectable permission options. Default `false`.                                                                                       | `false` |
| query | include_parents  | boolean                                 | false    | Set to `true` to return a `parent_permissions` array of permission objects in each first-level permission object. Default `false`.                                                                                     | `false` |

#### Response: 200

Permission(s) retrieved! The request was successful and the permissions are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - permission_categories (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A