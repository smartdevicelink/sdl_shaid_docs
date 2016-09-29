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
Before an application can use a feature offered by SDL it must first be granted permission to do so.  These permissions are granted on a per RPC basis, meaning permission to use each RPC must be granted to an application.  RPCs are grouped based on common function into what we call Functional Groups.  Applications can request access to each Functional Group an OEM offers in their vehicle.

The following functional groups are available:

| Functional Group | Description | RPCs |
|------------------|-------------|------|
| Navigation | Turn by turn directions | showConstantTBT, alertManuever, updateTurnList |
| Vehicle Info | Vehicle information | externalTemperature, fuelLevel, fuelLevelState, etc. |
| Driving Characteristics | Vehicle operator related information | beltStatus, driverBraking, myKey, prndl, rpm |
| GPS & Speed | Location related information. | GPS, speed |
| Scrollable Msgs | Deliver text to the vehicle display that requires more than one screen for the entire message body | n/a |
| Audio Pass Through | Capture raw audio via vehicle microphone and transmit via BlueTooth to application. | n/a |
| B2B | Application is for non-consumer download | n/a |

Functional groups are stored as an ```array of strings```, for example:

```JSON
{
	"functionalGroups": [ "Navigation", "GPS & Speed" ]
}
```

### iOS URL Scheme
The [URL Scheme](https://developer.apple.com/library/content/featuredarticles/iPhoneURLScheme_Reference/Introduction/Introduction.html) is used by iOS applications to communicate or integrate with other multiple applications.  For example, a URL Scheme could be used by application A to launch application B to make a phone call.

URL Scheme are ```string``` values and look like the following:
```JSON
{
	"androidPackageName": "com.example.my.app"
}
```

### Last Updated
The date and time of when the application record was last updated.  This occurs when a user changes an application attribute on any SDL Server or Developer portal.  The value is a [date-time](../TIME) string, for example:

```JSON
{
	"lastUpdated": "2016-07-15T20:49:59.130Z"
}
```

### Last Updated By
The user who last updated the application record.  This is a ```string``` value that uniquely identifies the user in SHAID and SmartDeviceLink.com.

```JSON
{
	"lastUpdatedBy": "5684123aef654"
}
```

### Minimum Operating System
The lowest Android or iOS operating system supported by the application.  

For Android, this is the ```minSdlVersion``` found in the application's manifest file:
```JSON
{
	"minimumOperatingSystem": "14"
}
```

For iOS, this is the deployment target:
```JSON
{
	"minimumOperatingSystem": "8.1"
}
```

### Maximum Operating System
The highest Android or iOS operating system supported by the application in a vehicle.

For Android, this is the ```minSdlVersion``` found in the application's manifest file:
```JSON
{
	"minimumOperatingSystem": "17"
}
```

For iOS, this is the deployment target:
```JSON
{
	"minimumOperatingSystem": "8.5"
}
```

### Name
The name of the application.  This is a ```string``` value and looks like:

```JSON
{
	"name": "My App Name"
}
```
### Platform
The mobile platform your application is built on.  Available options are ```android``` or ```ios```, for example:

```JSON
{
	"platform": "Android"
}
```

### Notification Priority Level
There are several different priority levels that can be granted to an application's notifications.  This will determine when and where your application can notify the passengers.  One of the following levels can be selected based on the application's main function.

  | Priority Level | Description |
  |----------------|-------------|
  | Navigation | Provides turn-by-turn driving directions |
  | Communication | Provides services such as voice calling, message delivery, and/or other forms of communication. |
  | Normal | Deliver background alerts not related to Navigation or Communication. |
  | Emergency | Provides services similar to 911-type of help, heart monitoring, blood sugar monitoring, and the like. |
  | None | Does not deliver in-vehicle notifications. |

## User
Data about the submitting user.

### Email
The primary email address used to contact the user.  This is a ```string``` value that looks like:
```JSON
{
	"email": "myEmail@gmail.com"
}
```

### First Name
First name of the user.  This is a ```string``` value that looks like:
```JSON
{
	"firstName": "John"
}
```

### ID
A unique identifier for the user in SHAID and SmartDeviceLink.com.  This is a ```string``` value that looks like:
```JSON
{
	"id": "5684123aef654"
}
```

### Last Name
First name of the user.  This is a ```string``` value that looks like:
```JSON
{
	"lastName": "Smith"
}
```

### Phone Number
Phone number of the user.  This is a ```string``` value that looks like:
```JSON
{
	"phoneNumber": "9198675309"
}
```

### Primary Country
The country in which the user resides.  Used to direct submissions to the appropriate contact at an OEM.

The value for ```primaryCountryCode``` is a [ISO 3166 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code stored as a ```string```.  The value for ```primaryCountry``` is a user friendly name of the country stored as a ```string```.
```JSON
{
	"primaryCountryCode": "us",
	"primaryCountry": "United States of America"
}
```

> Note:  The ```primaryCountry``` friendly name should not be used to identify a country and should only be used to display what that country is to a user.

### Primary Language
The primary language of the user.  Used to direct submissions to the appropriate contact at an OEM.

The value is a  language code stored as a ```string```.
The value for ```primaryLanguageCode``` is a [ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1) language code stored as a ```string```.  The value for ```primaryLanguage``` is a user friendly name of the language stored as a ```string```.
```JSON
{
	"primaryLanguageCode": "en",
	"primaryLanguage": "English"
}
```

> Note:  The ```primaryLanguage``` friendly name should not be used to identify a language and should only be used to display what that language is to a user.
