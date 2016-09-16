# Date-Time
Date-Time values can seem confusing or complicated, so let's keep it [simple](https://xkcd.com/1179/).  All date-time values sent to or from SHAID are in the string format described below.

!!! IMPORTANT
All date-time values are stored as ```Strings```.
!!!

## ISO 8601
SHAID uses [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) to display date/time values.

All date-time values are formatted as ```date``` + ```T``` + ```time```.
```
2016-07-15T20:49:59.130Z
```

### Dates
Dates are written as ```Year-Month-Day``` in the format ```YYYY-MM-DD```, with the month and day values zero padded.
```
2016-07-15
```

### Time
Times are written using the [24-hour clock system](https://en.wikipedia.org/wiki/24-hour_clock).  They include ```Hours:Minutes:Seconds.Milliseconds``` in the format ```hh:mm:ss.sss```. The hours, minutes, and seconds are single zero padded, while the milliseconds have a double zero padding.  As indicated above a ```T``` prefixes the time value separating the date from the time.  A ```Z``` at the end of the time value indicates the [+0 GMT](http://wwp.greenwichmeantime.com/info/iso.htm) timezone.

!!! IMPORTANT
All times are in the [+0 GMT](http://wwp.greenwichmeantime.com/info/iso.htm) timezone.
!!!

```
T20:49:59.130Z
```

### Date-Time Example
The time for July 15th 2016 at 8:49:59 pm, and 130 milliseconds, in the timezone of +0 GMT would look like:
```
2016-07-15T20:49:59.130Z
```
