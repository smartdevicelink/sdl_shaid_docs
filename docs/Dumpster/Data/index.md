# Data
The following data can be synchronized between developer portals and SDL Servers using Dumpster.

## Application
Data about the mobile application.

### Android Package Name
The [package name](https://developer.android.com/guide/topics/manifest/manifest-element.html) serves as a unique identifier for Android applications.  Once publish an application **package name cannot be changed**;  doing so would cause the application to be treated as a brand new application.

Packages names are ```string``` values and look like the following:

```JSON
{
	"androidPackageName": "com.example.my.app"
}
```

### Application ID
A ```string``` value that uniquely identifies an application in the SDL ecosystem.  Take for example:

```JSON
{
	"applicationId": "123e4567-e89b-12d3-a456-426655440000"
}
```

### Date Created
The date and time of when the application record was created.  This occurs when a user generates a new application ID.  The value is a [date-time](../TIME) string, for example:

```JSON
{
	"dateCreated": "2016-07-15T20:49:59.130Z"
}
```
### Description
Description of what the application is or does.  A string value, for example:

```JSON
{
	"description": "This app is like uber for shaming people"
}
```

### Functional Groups
### iOS URL Scheme
### Last Updated
### Last Updated By
### Minimum Operating System
### Maximum Operating System
### Name
### Platform
### Notification Priority Level
There are several different priority levels that can be granted to an application's notifications.  This will determine when and where your application can notify the passengers.  One of the following levels can be selected based on the applicaiton's main function.

  | Priority Level | Description |
  |----------------|-------------|
  | Navigation | Provides turn-by-turn driving directions |
  | Communication | Provides services such as voice calling, message delivery, and/or other forms of communication. |
  | Normal | Deliver background alerts not related to Navigation or Communication. |
  | Emergency | Provides services similar to 911-type of help, heart monitoring, blood sugar monitoring, and the like. |
  | None | Does not deliver in-vehicle notifications. |


Groups: [ "Vehicle Info", "B2B License (Ford Only)", "B2B License (Toyota Only)", ]




## User
Data about the submitting user.

### Email
### First Name
### Last Name
### Phone Number
### Primary Country
### Primary Language
