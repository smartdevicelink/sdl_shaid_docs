# API Requests
The API follows typical RESTful practices and expects only JSON content types.

!!! IMPORTANT
All API requests require [Authentication](../Authentication).
!!!

## Headers
The following is a list of headers used by all API requests.

| Header Parameter | Type | Required | Default | Description |
|------------------|------|----------|---------|-------------|
| Authentication | String | No | ```undefined``` | An OAuth 2.0 access token is place here to authenticate each API request. |
| Content-Type | String | Yes | ```undefined``` | Only a value of ```application/json``` is supported. |

## Accepted HTTP Methods
Common HTTP methods are supported.

  * **GET** - Retrieves one or more resources from the server.
  * **PUT** - Updates one or more resources.  Data is typically placed in the request body.
  * **POST** - Creates one or more resources.  Data is typically placed in the request body.
  * **DELETE** - Removes one or more resources.

## URL
An API request URL can be broken down into five main components:

```PROTOCOL``` :// ```SHAID DOMAIN``` / ```API SERVICE NAME``` / ```API VERSION``` / ```API ENDPOINT```

For example, a request's URL to create new application IDs might look like:

```https``` :// ```shaid.smartdevicelink.com``` / ```maids``` / ```0``` / ```appids```

Additionally, some requests might allow for specific ```URL Parameters``` and ```Query Parameters```.

### Protocol
For external requests ```https``` must be used.  Internal API queries can make use of the less secure ```http``` protocol.

### SHAID Domain
For external requests ```shaid.smartdevicelink.com``` must be used.  Internal API queries can make use of the internal IP address of each API service.

### API Service Name
Several micro-services make up the SHAID application.  They can be accessed individually using their names.  See each service's document for more information.

### API Version
Each endpoint is versioned so the API interface will not change.  Zero is the very first version and increments for each newer version.

> Version is just a ```URL Parameter``` allowed in every API request.

### API Endpoint
The endpoint specifies the API method that should be called.

For example, when creating new application IDs the ```appids``` method should be called.
```
POST https://shaid.smartdevicelink.com/maids/0/appids
```

Learn more about each method in the individual API sections.

### Query Parameters
Query parameters can be included in a URL as a <a href="https://en.wikipedia.org/wiki/Query_string" target="_blank">query strings</a> and should be placed in the URL after a ```?```.

For example, searching for all active users might look like this:

```
GET https://shaid.smartdevicelink.com/userservice/0/users?active=true
```

### URL Parameters
Some API endpoints require one or more variables to be placed in the URL.  A common example is when referencing a single item by ID.  In the example below we are trying to get information about an user with an ID of ```1082347532289```.

```
GET https://shaid.smartdevicelink.com/maids/0/users/1082347532289
```

In the above example user ID is a URL parameter and when written in the API documentation will look something like this:

```
GET https://shaid.smartdevicelink.com/userservice/0/users/:userId
```

The ```:``` declares ```userId``` as a variable and ```userId``` is the variable name.


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
