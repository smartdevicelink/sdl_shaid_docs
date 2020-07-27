## GET /service

Retrieve a list of app service types an Application can choose to support. An Application may support many service types.

**Parameters**

| in    | name                | type                                    | required | description                                                                                                                                                                                                            | default |
|-------|---------------------|-----------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| query | include_permissions | boolean                                 | false    | Set to `true` to return a `permissions` array of permission objects associated with each app service type. Default `false`.                                                                                            | `false` |
| query | application_uuid    | string                                  | false    | Check each service against the given Application to see if it is currently supported by the Application, returned by the is_selected attribute.                                                                        |         |
| query | status              | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only match against the given `application_uuid` in the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`. |         |

#### Response: 200

Services retrieved! The request was successful and the services are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - services (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A