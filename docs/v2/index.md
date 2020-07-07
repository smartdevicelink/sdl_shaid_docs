### [Click here for the full API documentation](https://shaid.smartdevicelink.com/docs)
# SHAID v2.6.0

Base URL: https://shaid.smartdevicelink.com/api/v2

- [Endpoints](#endpoints)
  - [GET /application](#get-application)
  - [PUT /application/approval/vendor](#put-applicationapprovalvendor)
  - [GET /category](#get-category)
  - [GET /country](#get-country)
  - [GET /service](#get-service)
  - [GET /permission](#get-permission)
  - [GET /locale](#get-locale)
  - [POST /webhooks](#post-webhooks)

# Endpoints





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





















## GET /category

Retrieve a list of supported categories an Application can choose to be listed under. An Application may only be associated with one category.

**Parameters**

| in    | name             | type                                    | required | description                                                                                                                                                                                                            |
|-------|------------------|-----------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string                                  | false    | Check each category against the given Application to see if it is currently in use by the Application, returned by the is_selected attribute.                                                                          |
| query | status           | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only match against the given `application_uuid` in the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`. |

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

## GET /country

Retrieve a list of countries an Application can choose to operate in (should the Vendor OEM support it). An Application may be associated with many countries.

**Parameters**

| in    | name             | type                                    | required | description                                                                                                                                                                                                            |
|-------|------------------|-----------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string                                  | false    | Check each country against the given Application to see if it is currently in use by the Application, returned by the is_selected attribute.                                                                           |
| query | status           | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only match against the given `application_uuid` in the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`. |

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













## GET /locale

Retrieve a list of RFC 5646 language codes. An Application can have many locales supported.

**Parameters**

| in    | name             | type                                    | required | description                                                                                                                                                                                                            |
|-------|------------------|-----------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query | application_uuid | string                                  | false    | Check each locale against the given Application to see if it is currently in use by the Application, returned by the is_selected attribute.                                                                            |
| query | status           | string: DEVELOPMENT, REVIEW, PRODUCTION | false    | Only match against the given `application_uuid` in the provided status. This parameter is only available for vendors with SHAID admin access; For non-admins, the value of this parameter will always be `PRODUCTION`. |

#### Response: 200

Locales retrieved! The request was successful and the locales are returned in the response body.

**Schema**

- (object)
  - meta (object) (optional)
    - request_id (string) A unique ID for the request
    - code (int32) The HTTP status code of the response
    - message (string) A readable summary of the request result
  - data (object) (optional)
    - locales (unspecified type) (optional)

#### Response: 400

Invalid request. The request is either missing data, has invalid data, or has conflicting data. See the response body for more details.

**Schema**

N/A

#### Response: 500

Internal server error.

**Schema**

N/A

## POST /webhooks

#### Not an actual endpoint. This section describes how webhooks are sent to third-party SDL Policy Servers

 ### Summary
 Webhook events are sent to Vendors who have SDLC Membership level 1-4, are tagged by the SDLC as an "App Consumer", and have opted to receive the events by providing a Webhook URL in their company profile. They are designed to assist SDL Policy Servers in maintaining a synchronized state of SDL application metadata to ensure Policy Tables are kept up-to-date.

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
  - action (string: UPSERT, DELETE) (optional) The action taken to cause the webhook.
  - uuid (string) (optional) In the event of an `application` entity, this respresents the application's UUID.
  - updated_ts (string, date-time) (optional) The DateTime the entity was updated which caused the webhook to be sent.
  - deleted_ts (string, date-time) (optional) The DateTime the entity was deleted which cased the webhook to be sent. Deleted entities will not have future webhook events and will no longer be available in GET requests.

#### Response: 404

This endpoint does not exist.

**Schema**

N/A
