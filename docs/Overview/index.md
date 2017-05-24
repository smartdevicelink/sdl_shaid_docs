# Overview
This documentation provides information about integrating with the Shared Application ID (SHAID) service. SHAID is a centralized service designed to keep information about SDL-supported applications synchronized across the SmartDeviceLink (SDL) ecosystem.

## Audience
If you are an Original Equipment Manufacturer (OEM) and have your own developer portal and/or SDL Server implementation, then you will need to consider integrating with SHAID.

## Abbreviations and Definitions
Abbreviations used in this document are collected in the table below

| Abbreviation | Meaning |
| :------------- | :------------- |
|JSON|JavaScript Object Notation|
|OEM|Original Equipment Manufacturer|
|RPC|Remote Procedure Call|
|SDE|Software Development Environment|
|SDL|SmartDeviceLink|
|SEE|Software Engineering Environment|
|SHAID|Shared Application ID|

## Dates and Date-Time
SHAID uses [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) to store and return date-time values.

All date-time values are formatted as ```date``` + ```T``` + ```time```.
```
2016-07-15T20:49:59.130Z
```
