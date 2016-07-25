# API Requests
The API follows typical RESTful practices and expects only JSON content types. 

> Note:  All API requests require [Authentication]().

## Headers
The following is a list of allowed headers for all requests.

| Header Parameter | Type | Required | Default | Description |
|------------------|------|----------|---------|-------------|
| Authentication | String | No | ```undefined``` | A string OAuth 2.0 access token used to authenticate each API request. |
| Content-Type | String | Yes | ```undefined``` | Only a value of ```application/json``` is supported. |

## Accepted HTTP Methods
Common HTTP methods are supported.

  * GET - Retrieves one or more resources from the server.
  * PUT - Updates one or more resources.  Data is typically placed in the request body. 
  * POST - Creates one or more resources.  Data is typically placed in the request body. 
  * DELETE - Removes one or more resources.

## URL
An API request URL can be broken down into five parts:

```PROTOCOL``` :// ```DOMAIN``` / ```API SERVICE``` / ```VERSION``` / ```API ENDPOINT```

For example:

```https``` :// ```shaid.smartdevicelink.com``` / ```maids``` / ```0``` / ```appids```

### Protocol
For external requests ```https``` must be used.  Internal API queries can make use of the less secure ```http``` protocol.

### Domain
For external requests ```shaid.smartdevicelink.com``` must be used.  Internal API queries can make use of the internal IP address of each API service.

### API Service
Several micro-services make up the SHAID application.  They can be accessed individually using their names.

### Version
Each endpoint is versioned so the API interface will not change.  Zero is the very first version and increments for each newer version.
 
### API Endpoint
The endpoint is the API method to be called, such as ```appids``` to create new application IDs.  Learn more about these in the API sections.
 
## Example Request
An example request to create two new application IDs. 

```
"Headers": {
  "Authentication": "MyAccessTokenGoesHere",
  "Content-Type": "application/json"
}

POST https://shaid.smartdevicelink.com/maids/0/appids

"Body": {
  "numOfIds": 2
}
```

The example above shows two headers, one used for authentication and the other specifying the content type of our request body.  The HTTP method ```POST``` is used to create new data on the ```MAIDS``` API endpoint called ```appids``` with version ```0```.  In the body we have the data required to specify the creation of two new application IDs.
