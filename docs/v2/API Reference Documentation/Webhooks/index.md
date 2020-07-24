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