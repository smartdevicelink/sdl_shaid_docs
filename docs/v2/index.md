### [Click here for the full API documentation](https://shaid.smartdevicelink.com/docs)
# SHAID, version 2.0.0

Base URL: https|http://shaid.smartdevicelink.com/api/v2

- [Endpoints](#endpoints)
  - [POST /application](#post-application)
  - [PUT /application](#put-application)
  - [GET /application](#get-application)
  - [DELETE /application](#delete-application)
  - [PUT /application/approval/sdlc](#put-applicationapprovalsdlc)
  - [GET /category](#get-category)
  - [GET /country](#get-country)
  - [GET /permission](#get-permission)
  - [POST /vendor](#post-vendor)
  - [PUT /vendor](#put-vendor)
  - [GET /vendor](#get-vendor)
  - [POST /webhooks](#post-webhooks)

## Endpoints

### POST /application

# Requires Admin Access
 Create one or more applications with custom UUIDs, or automatically generate new UUIDs. For nested properties `category`, `vendor`, and `permissions`, only the `id` value of each object should be provided. For `countries`, only each country's ISO code is required.

**Parameters**

| in   | name | required | description                                        |
|------|------|----------|----------------------------------------------------|
| body | body | true     | An array of Application objects to create/register |

**Request Body**

- (object)
  - applications (array) (optional)
    - (object)
      - uuid (string) (optional) A unique value representing the application.
      - name (string) The name of the application. This name will NOT be displayed on the vehicle's HMI unless it is also in `display_names`.
      - description (string) (optional) The description of the application. This should be a brief consumer-friendly explanation of what the application offers to SDL users.
      - display_names (array) An array of application names which the application may use to display on the vehicle's HMI.
        - (string)
      - platform (string: ANDROID, IOS) The device platform the app is designed for.
      - platform_app_id (string) The unique Android Package Name or iOS Bundle ID of the application.
      - status (string: DEVELOPMENT, REVIEW, PRODUCTION) (optional) The publishing status of the application. The status lifecycle of an application should be DEVELOPMENT -> REVIEW -> PRODUCTION. Once an application is in PRODUCTION status, it will not require SDLC approval for future changes. Only applications with PRODUCTION status can be viewed by authorized vendors.
      - approval_status (string: DENIED, PENDING, APPROVED) (optional) Whether or not the SDLC has approved the application. Non-admins may disregard this field. This property may only be modified using the PUT `/application/approval` endpoint.
      - tech_email (string) (optional) An optional email address of a technical contact for the application.
      - tech_phone (string) (optional) An optional 10-digit US phone number of the technical contact for the application.
      - default_hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional)
      - can_steal_focus (boolean) (optional) Whether or not the application needs to be able to request to enter the foreground.
      - can_background_alert (boolean) (optional) Whether or not the application needs to be able to create an alert when running in the background.
      - allow_marketing (boolean) (optional) Whether or not the application has been allowed by the developer to appear in SDL-related marketing material.
      - created_ts (string, date-time) (optional) The DateTime the application was created.
      - updated_ts (string, date-time) (optional) The DateTime the application was last updated.
      - countries (array) (optional)
        - (object)
          - iso (string) A unique 2-character ISO code to identify the country.
          - name (string) (optional) The readable name of the country.
          - is_selected (boolean) (optional) GET /country requests only. Designates whether or not the provided application intends to make itself available in the country.
      - category (object)
        - id (int64) A unique integer to identify the category
        - display_name (string) (optional) The readable name of the category
        - is_selected (boolean) (optional) GET /category requests only. Designates whether or not the provided application has selected the category
      - vendor (object)
        - id (int64) (optional) A unique integer assigned to the vendor.
        - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
        - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
        - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
        - name (string) The vendor's name.
        - email (string) The vendor's email address.
        - icon_url (string) (optional) A URL to an image representing the vendor's logo.
        - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
        - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
        - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
        - created_ts (string, date-time) (optional) The DateTime the vendor was created.
        - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
        - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
        - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
          - (object)
            - property (string) (optional) The name of the property that is erroneous.
            - message (string) (optional) An explanation about why the given property is erroneous.
      - permissions (array) (optional)
        - (object)
          - id (int64) A unique integer assigned to the permission.
          - key (string) (optional) A unique string assigned to the permission.
          - name (string) (optional) A readable name of the permission.
          - is_parameter (boolean) (optional) Indicates whether or not the permission is a parameter of an RPC, rather than an RPC itself.
          - hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional) GET /permission requests only. Designates the HMI access level the provided application has selected for the permission.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 201

Application(s) created! The applications provided were successfully created and are returned in the response body.

**Schema**

N/A

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### PUT /application

# Requires Admin Access
 This operation performs a full overwrite of the application's metadata (except for `approval_status`), therefore you must send all metadata about an application, even if a particular attribute hasn't changed. Partial updates are performed via PATCH, which is currently unsupported. For nested properties `category`, `vendor`, and `permissions`, only the `id` value of each object should be provided. For `countries`, only each country's ISO code is required.

**Parameters**

| in   | name         | required | description                               |
|------|--------------|----------|-------------------------------------------|
| body | applications | true     | An array of Application objects to update |

**Request Body**

- (object)
  - applications (array) (optional)
    - (object)
      - uuid (string) (optional) A unique value representing the application.
      - name (string) The name of the application. This name will NOT be displayed on the vehicle's HMI unless it is also in `display_names`.
      - description (string) (optional) The description of the application. This should be a brief consumer-friendly explanation of what the application offers to SDL users.
      - display_names (array) An array of application names which the application may use to display on the vehicle's HMI.
        - (string)
      - platform (string: ANDROID, IOS) The device platform the app is designed for.
      - platform_app_id (string) The unique Android Package Name or iOS Bundle ID of the application.
      - status (string: DEVELOPMENT, REVIEW, PRODUCTION) (optional) The publishing status of the application. The status lifecycle of an application should be DEVELOPMENT -> REVIEW -> PRODUCTION. Once an application is in PRODUCTION status, it will not require SDLC approval for future changes. Only applications with PRODUCTION status can be viewed by authorized vendors.
      - approval_status (string: DENIED, PENDING, APPROVED) (optional) Whether or not the SDLC has approved the application. Non-admins may disregard this field. This property may only be modified using the PUT `/application/approval` endpoint.
      - tech_email (string) (optional) An optional email address of a technical contact for the application.
      - tech_phone (string) (optional) An optional 10-digit US phone number of the technical contact for the application.
      - default_hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional)
      - can_steal_focus (boolean) (optional) Whether or not the application needs to be able to request to enter the foreground.
      - can_background_alert (boolean) (optional) Whether or not the application needs to be able to create an alert when running in the background.
      - allow_marketing (boolean) (optional) Whether or not the application has been allowed by the developer to appear in SDL-related marketing material.
      - created_ts (string, date-time) (optional) The DateTime the application was created.
      - updated_ts (string, date-time) (optional) The DateTime the application was last updated.
      - countries (array) (optional)
        - (object)
          - iso (string) A unique 2-character ISO code to identify the country.
          - name (string) (optional) The readable name of the country.
          - is_selected (boolean) (optional) GET /country requests only. Designates whether or not the provided application intends to make itself available in the country.
      - category (object)
        - id (int64) A unique integer to identify the category
        - display_name (string) (optional) The readable name of the category
        - is_selected (boolean) (optional) GET /category requests only. Designates whether or not the provided application has selected the category
      - vendor (object)
        - id (int64) (optional) A unique integer assigned to the vendor.
        - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
        - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
        - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
        - name (string) The vendor's name.
        - email (string) The vendor's email address.
        - icon_url (string) (optional) A URL to an image representing the vendor's logo.
        - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
        - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
        - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
        - created_ts (string, date-time) (optional) The DateTime the vendor was created.
        - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
        - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
        - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
          - (object)
            - property (string) (optional) The name of the property that is erroneous.
            - message (string) (optional) An explanation about why the given property is erroneous.
      - permissions (array) (optional)
        - (object)
          - id (int64) A unique integer assigned to the permission.
          - key (string) (optional) A unique string assigned to the permission.
          - name (string) (optional) A readable name of the permission.
          - is_parameter (boolean) (optional) Indicates whether or not the permission is a parameter of an RPC, rather than an RPC itself.
          - hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional) GET /permission requests only. Designates the HMI access level the provided application has selected for the permission.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 200

Application(s) updated! The applications provided were successfully updated and are returned in the response body.

**Schema**

N/A

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### GET /application

Retrieve one or more SDL applications and metadata about them: their UUID (a unique identifier which should be kept private), the countries the application supports, the application category, and the data permissions the application requires access to.

**Parameters**

| in    | name            | type                                    | required | description                                                                                                                                                                                                         | default |
|-------|-----------------|-----------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| query | uuid            | string                                  | false    | Find a specific application by its UUID.                                                                                                                                                                            |         |
| query | vendor_id       | integer                                 | false    | Find applications owned by a specific Vendor                                                                                                                                                                        | `null`  |
| query | status          | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only retrieve applications matching the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`.             |         |
| query | approval_status | string: DENIED, PENDING, APPROVED       | false    | Only retrieve applications matching the provided SDLC approval status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `APPROVED`. |         |
| query | limit           | integer                                 | false    | The maximum number of results to return. Max 50.                                                                                                                                                                    | `50`    |
| query | offset          | integer                                 | false    | The number of results to offset, for basic pagination.                                                                                                                                                              | `0`     |

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

### DELETE /application

# Requires Admin Access
 Deletes one or more applications. Only the `uuid` of each appliation object is required for this call.

**Parameters**

| in   | name         | required | description                                                                                            |
|------|--------------|----------|--------------------------------------------------------------------------------------------------------|
| body | applications | true     | An array of Application objects to delete. **Only the `uuid` is required in each Application object.** |

**Request Body**

- (object)
  - applications (array) (optional)
    - (object)
      - uuid (string) (optional) A unique value representing the application.
      - name (string) The name of the application. This name will NOT be displayed on the vehicle's HMI unless it is also in `display_names`.
      - description (string) (optional) The description of the application. This should be a brief consumer-friendly explanation of what the application offers to SDL users.
      - display_names (array) An array of application names which the application may use to display on the vehicle's HMI.
        - (string)
      - platform (string: ANDROID, IOS) The device platform the app is designed for.
      - platform_app_id (string) The unique Android Package Name or iOS Bundle ID of the application.
      - status (string: DEVELOPMENT, REVIEW, PRODUCTION) (optional) The publishing status of the application. The status lifecycle of an application should be DEVELOPMENT -> REVIEW -> PRODUCTION. Once an application is in PRODUCTION status, it will not require SDLC approval for future changes. Only applications with PRODUCTION status can be viewed by authorized vendors.
      - approval_status (string: DENIED, PENDING, APPROVED) (optional) Whether or not the SDLC has approved the application. Non-admins may disregard this field. This property may only be modified using the PUT `/application/approval` endpoint.
      - tech_email (string) (optional) An optional email address of a technical contact for the application.
      - tech_phone (string) (optional) An optional 10-digit US phone number of the technical contact for the application.
      - default_hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional)
      - can_steal_focus (boolean) (optional) Whether or not the application needs to be able to request to enter the foreground.
      - can_background_alert (boolean) (optional) Whether or not the application needs to be able to create an alert when running in the background.
      - allow_marketing (boolean) (optional) Whether or not the application has been allowed by the developer to appear in SDL-related marketing material.
      - created_ts (string, date-time) (optional) The DateTime the application was created.
      - updated_ts (string, date-time) (optional) The DateTime the application was last updated.
      - countries (array) (optional)
        - (object)
          - iso (string) A unique 2-character ISO code to identify the country.
          - name (string) (optional) The readable name of the country.
          - is_selected (boolean) (optional) GET /country requests only. Designates whether or not the provided application intends to make itself available in the country.
      - category (object)
        - id (int64) A unique integer to identify the category
        - display_name (string) (optional) The readable name of the category
        - is_selected (boolean) (optional) GET /category requests only. Designates whether or not the provided application has selected the category
      - vendor (object)
        - id (int64) (optional) A unique integer assigned to the vendor.
        - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
        - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
        - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
        - name (string) The vendor's name.
        - email (string) The vendor's email address.
        - icon_url (string) (optional) A URL to an image representing the vendor's logo.
        - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
        - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
        - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
        - created_ts (string, date-time) (optional) The DateTime the vendor was created.
        - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
        - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
        - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
          - (object)
            - property (string) (optional) The name of the property that is erroneous.
            - message (string) (optional) An explanation about why the given property is erroneous.
      - permissions (array) (optional)
        - (object)
          - id (int64) A unique integer assigned to the permission.
          - key (string) (optional) A unique string assigned to the permission.
          - name (string) (optional) A readable name of the permission.
          - is_parameter (boolean) (optional) Indicates whether or not the permission is a parameter of an RPC, rather than an RPC itself.
          - hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional) GET /permission requests only. Designates the HMI access level the provided application has selected for the permission.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 200

Application(s) deleted!

**Schema**

N/A

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### PUT /application/approval/sdlc

# Requires Admin Access
 This operation changes the `approval_status` property of an application. If the `approval_status` is changed to `APPROVED`, the application's `status` will be automatically set to `PRODUCTION` as well, making the application immediately available to its designated allowed Vendors.

**Parameters**

| in   | name         | required | description                                                                                                                          |
|------|--------------|----------|--------------------------------------------------------------------------------------------------------------------------------------|
| body | applications | true     | An array of Application objects to update. **Each application object only needs a `uuid` and `approval_status` for this operation.** |

**Request Body**

- (object)
  - applications (array) (optional)
    - (object)
      - uuid (string) (optional) A unique value representing the application.
      - name (string) The name of the application. This name will NOT be displayed on the vehicle's HMI unless it is also in `display_names`.
      - description (string) (optional) The description of the application. This should be a brief consumer-friendly explanation of what the application offers to SDL users.
      - display_names (array) An array of application names which the application may use to display on the vehicle's HMI.
        - (string)
      - platform (string: ANDROID, IOS) The device platform the app is designed for.
      - platform_app_id (string) The unique Android Package Name or iOS Bundle ID of the application.
      - status (string: DEVELOPMENT, REVIEW, PRODUCTION) (optional) The publishing status of the application. The status lifecycle of an application should be DEVELOPMENT -> REVIEW -> PRODUCTION. Once an application is in PRODUCTION status, it will not require SDLC approval for future changes. Only applications with PRODUCTION status can be viewed by authorized vendors.
      - approval_status (string: DENIED, PENDING, APPROVED) (optional) Whether or not the SDLC has approved the application. Non-admins may disregard this field. This property may only be modified using the PUT `/application/approval` endpoint.
      - tech_email (string) (optional) An optional email address of a technical contact for the application.
      - tech_phone (string) (optional) An optional 10-digit US phone number of the technical contact for the application.
      - default_hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional)
      - can_steal_focus (boolean) (optional) Whether or not the application needs to be able to request to enter the foreground.
      - can_background_alert (boolean) (optional) Whether or not the application needs to be able to create an alert when running in the background.
      - allow_marketing (boolean) (optional) Whether or not the application has been allowed by the developer to appear in SDL-related marketing material.
      - created_ts (string, date-time) (optional) The DateTime the application was created.
      - updated_ts (string, date-time) (optional) The DateTime the application was last updated.
      - countries (array) (optional)
        - (object)
          - iso (string) A unique 2-character ISO code to identify the country.
          - name (string) (optional) The readable name of the country.
          - is_selected (boolean) (optional) GET /country requests only. Designates whether or not the provided application intends to make itself available in the country.
      - category (object)
        - id (int64) A unique integer to identify the category
        - display_name (string) (optional) The readable name of the category
        - is_selected (boolean) (optional) GET /category requests only. Designates whether or not the provided application has selected the category
      - vendor (object)
        - id (int64) (optional) A unique integer assigned to the vendor.
        - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
        - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
        - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
        - name (string) The vendor's name.
        - email (string) The vendor's email address.
        - icon_url (string) (optional) A URL to an image representing the vendor's logo.
        - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
        - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
        - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
        - created_ts (string, date-time) (optional) The DateTime the vendor was created.
        - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
        - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
        - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
          - (object)
            - property (string) (optional) The name of the property that is erroneous.
            - message (string) (optional) An explanation about why the given property is erroneous.
      - permissions (array) (optional)
        - (object)
          - id (int64) A unique integer assigned to the permission.
          - key (string) (optional) A unique string assigned to the permission.
          - name (string) (optional) A readable name of the permission.
          - is_parameter (boolean) (optional) Indicates whether or not the permission is a parameter of an RPC, rather than an RPC itself.
          - hmi_level (string: HMI_NONE, HMI_BACKGROUND, HMI_LIMITED, HMI_FULL) (optional) GET /permission requests only. Designates the HMI access level the provided application has selected for the permission.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 200

Application approval status(es) updated! The application(s) provided were successfully updated.

**Schema**

N/A

#### Response: 400

Invalid request.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### GET /category

Retrieve a list of supported categories an Application can choose to be listed under. An Application may only be associated with one category.

**Parameters**

| in    | name             | type   | required | description                                                                                                                                   |
|-------|------------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string | false    | Check each category against the given Application to see if it is currently in use by the Application, returned by the is_selected attribute. |

#### Response: 200

Categories retrieved! The request was successful and the categories are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - categories (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### GET /country

Retrieve a list of countries an Application can choose to operate in (should the Vendor OEM support it). An Application may be associated with many countries.

**Parameters**

| in    | name             | type   | required | description                                                                                                                                  |
|-------|------------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string | false    | Check each country against the given Application to see if it is currently in use by the Application, returned by the is_selected attribute. |

#### Response: 200

Countries retrieved! The request was successful and the countries are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - countries (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### GET /permission

Retrieve a list of supported permissions an Application can request access to. An Application can use many permissions. A SmartDeviceLink Application requires certain data permissions about the mobility experience. These permissions are chosen by the developer and should be synchronized with OEM systems or SDL Server implementations.

**Parameters**

| in    | name             | type   | required | description                                                                                                                                   |
|-------|------------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string | false    | Check each permission against the given Application to see if it is currently in use by the Application, returned by the hmi_level attribute. |

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

### POST /vendor

# Requires Admin Access
 Create one or more vendors.

**Parameters**

| in   | name | required | description                          |
|------|------|----------|--------------------------------------|
| body | body | true     | An array of Vendor objects to create |

**Request Body**

- (object)
  - vendors (array) (optional)
    - (object)
      - id (int64) (optional) A unique integer assigned to the vendor.
      - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
      - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
      - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
      - name (string) The vendor's name.
      - email (string) The vendor's email address.
      - icon_url (string) (optional) A URL to an image representing the vendor's logo.
      - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
      - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
      - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
      - created_ts (string, date-time) (optional) The DateTime the vendor was created.
      - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
      - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 201

Vendor(s) created! The vendors provided were successfully created and are returned in the response body.

**Schema**

N/A

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### PUT /vendor

# Requires Admin Access
 This operation performs a full overwrite of the vendor's metadata, therefore you must send all metadata about a vendor, even if a particular attribute hasn't changed. Partial updates are performed via PATCH, which is currently unsupported.

**Parameters**

| in   | name | required | description                          |
|------|------|----------|--------------------------------------|
| body | body | true     | An array of Vendor objects to update |

**Request Body**

- (object)
  - vendors (array) (optional)
    - (object)
      - id (int64) (optional) A unique integer assigned to the vendor.
      - is_admin (boolean) (optional) Whether or not the vendor has administrative API access
      - is_app_consumer (boolean) (optional) Whether or not the vendor is capable of reading application data (when application vendors have granted them access).
      - sdlc_member_level (int32) (optional) The vendor's SDLC membership level, 1 being the highest.
      - name (string) The vendor's name.
      - email (string) The vendor's email address.
      - icon_url (string) (optional) A URL to an image representing the vendor's logo.
      - webhook_url (string) (optional) A URL to which the vendor wishes to receive webhook HTTP POST requests.
      - public_key (string) (optional) The public_key of the vendor for accessing the SHAID API.
      - secret_key (string) (optional) The secret_key of the vendor for accessing the SHAID API.
      - created_ts (string, date-time) (optional) The DateTime the vendor was created.
      - updated_ts (string, date-time) (optional) The DateTime the vendor was last updated.
      - is_selected (boolean) (optional) GET /vendor requests only. Designates whether or not the provided application has authorized the vendor to view it.
      - errors (array) (optional) When a request fails with a HTTP 400 response, this property will contain an array of error objects describing what went wrong.
        - (object)
          - property (string) (optional) The name of the property that is erroneous.
          - message (string) (optional) An explanation about why the given property is erroneous.

#### Response: 200

Vendor(s) updated! The vendors provided were successfully updated and are returned in the response body.

**Schema**

N/A

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### GET /vendor

# Requires Admin Access
 Retrieve one or more vendors and metadata about them.

**Parameters**

| in    | name              | type    | required | description                                                                                                                          | range               | default |
|-------|-------------------|---------|----------|--------------------------------------------------------------------------------------------------------------------------------------|---------------------|---------|
| query | id                | integer | false    | Find a specific vendor by their ID.                                                                                                  |                     |         |
| query | application_uuid  | string  | false    | The application UUID to query in the context of to see if the Vendor has been granted read permissions by the application developer. |                     |         |
| query | sdlc_member_level | integer | false    | Limit the results to Vendors with this SDLC membership level.                                                                        | `0 <= integer <= 5` |         |
| query | is_admin          | boolean | false    | Limit the results to Vendors that either are or are not explicitly administrators                                                    |                     |         |
| query | is_app_consumer   | boolean | false    | Limit the results to Vendors that either are or are not explicitly app consumers.                                                    |                     |         |
| query | public_key        | string  | false    | Find the Vendor associated with this public_key. The secret_key parameter must also be provided for this to work.                    |                     |         |
| query | secret_key        | string  | false    | Find the Vendor associated with this secret_key. The public_key parameter must also be provided for this to work.                    |                     |         |
| query | limit             | integer | false    | The maximum number of results to return. Max 50.                                                                                     |                     | `50`    |
| query | offset            | integer | false    | The number of results to offset, for basic pagination.                                                                               |                     | `0`     |

#### Response: 200

Vendor(s) retrieved! The request was successful and any matching vendors are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - vendors (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

### POST /webhooks

### Summary
 Webhook events are sent to Vendors who have SDLC Membership level 1-2 and have opted to receive them. They are designed to assist SDL Policy Servers in maintaining a synchronized state of SDL application metadata to ensure Policy Tables are kept up-to-date.
 ### Success, Retry, and Failure

 A webhook is considered successful if it receives an HTTP 2XX response from your server within 5 seconds of the request. In the event of a failure, we will attempt to re-send individual webhooks up to 3 more times, with 30 minute intervals between each attempt. If all 4 attempts fail to respond with an HTTP 2XX response code within 5 seconds, no further attempts will be made to send the webhook, and an email will be sent to the contact information on file to notify you of the repeated failures.

 ### Requests
 Webhooks are sent via HTTP POST requests to the endpoint on file for certain vendors. Vendors can manage their webhook endpoint via the [SDL Developer Portal](https://smartdevicelink.com). The initial webhook attempt typically occurs within 5 seconds of the data being changed on SHAID, and retry attempts typically occur at 30 minute intervals.

 ### Supported Webhook Entities
 Only the `application` entity is currently sent in webhooks, but we may introduce support for more in the future. Please make sure your webhook receiver is designed to gracefully handle/ignore additional entity types over time.

**Parameters**

| in   | name | required | description                      |
|------|------|----------|----------------------------------|
| body | body | false    | The JSON payload of the webhook. |

**Request Body**

- (object)
  - entity (string) (optional) The type of entity the webhook notification is regarding.
  - uuid (string) (optional) In the event of an `application` entity, this respresents the application's UUID.
  - updated_ts (string, date-time) (optional) The DateTime the entity was updated which caused the webhook to be sent.
  - deleted_ts (string, date-time) (optional) The DateTime the entity was deleted which cased the webhook to be sent. Deleted entities will not have future webhook events and will no longer be available in GET requests.

#### Response: 404

This endpoint does not exist.

**Schema**

N/A
