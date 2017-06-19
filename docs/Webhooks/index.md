# Webhooks
Webhook events are sent to Vendors who have SDLC Membership level 1-2 and have opted to receive them. They are designed to assist SDL Policy Servers in maintaining a synchronized state of SDL application metadata to ensure Policy Tables are kept up-to-date.

## Success, Retry, and Failure
A webhook is considered successful if it receives an HTTP 2XX response from your server within 5 seconds of the request. In the event of a failure, we will attempt to re-send individual webhooks up to 3 more times, with 30 minute intervals between each attempt. If all 4 attempts fail to respond with an HTTP 2XX response code within 5 seconds, no further attempts will be made to send the webhook, and an email will be sent to the contact information on file to notify you of the repeated failures.

## Requests
All webhooks are sent via HTTP POST to the webhook URL provided via the SmartDeviceLink Developer Portal. The initial webhook attempt typically occurs within 5 seconds of the data being changed on SHAID, and retry attempts typically occur at 30 minute intervals.

## Application Webhook Type
Below is an example of a webhook package indicating that an SDL application has been modified.

```json
{
  "webhook_type": "application",
  "uuid": "7ef0dc6f-6c31-481d-b7c1-3ada0f8b7df2",
  "updated_ts": "2017-06-16T13:33:17.034"
}
`

## Other Webhook Types
There are currently no other webhook types, but we may introduce more in the future. Please make sure your webhook receiver is designed to gracefully handle additional types over time.
