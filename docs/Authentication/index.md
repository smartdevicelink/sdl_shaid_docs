# Authentication
All API requests require authentication via a public and secret key-pair. Key pairs are enabled and distributed to Vendors with SDLC Membership Levels between 1 and 4.

### Authenticating Your Requests
Every SHAID API request must be authenticated by placing your Vendor key pair in the request `headers`.
```json
{
    "Content-Type": "application/json",
    "public_key": "abc123",
    "secret_key": "s3cr3t"
}
```

## Authentication Errors
The following HTTP response codes are related to authentication errors.

### Unauthorized (401)
Your API `public_key` and `secret_key` are not valid or your SDLC Membership Level does not allow SHAID access.

### Forbidden (403)
You are not authorized to perform the request. If you believe this is a mistake, please contact support@livio.io.
