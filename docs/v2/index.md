### [Click here for the full API documentation](https://shaid.smartdevicelink.com/docs)
# SHAID v2.0.0

Base URL: https|http://shaid.smartdevicelink.com/api/v2

- [Endpoints](#endpoints)
  - [GET /application](#get-application)
  - [GET /category](#get-category)
  - [GET /country](#get-country)
  - [GET /permission](#get-permission)
  - [POST /webhooks](#post-webhooks)

# Endpoints





## GET /application

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





## GET /category

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

## GET /country

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

## GET /permission

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







## POST /webhooks

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
