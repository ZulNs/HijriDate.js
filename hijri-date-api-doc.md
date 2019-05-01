# HijriDate API Documentation

&nbsp;

## Constructor
Creates a JavaScript **`HijriDate`** instance that represents a single moment in time. `HijriDate` objects use a [Unix Time Stamp](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_16), an integer value that is the number of milliseconds since 1 January 1970 UTC which is equivalent to 22 Syawwal 1389 UTC.

### Syntax
```javascript
new HijriDate();
new HijriDate(value);
new HijriDate(fullYear, monthIndex[, day[, hours[, minutes[, seconds[, milliseconds]]]]]);
```

**Note:** JavaScript `HijriDate` objects can only be instantiated by calling JavaScript `HijriDate` as a constructor: calling it as a regular function (i.e. without the `new` operator) will return a string rather than a `HijriDate` object.

### Parameters
**Note:** The argument `monthIndex` is 0-based. This means that `Muharram = 0` and `Dhul-Hijja = 11`.

**Note:** Where `HijriDate` is called as a constructor with more than one argument, if values are greater than their logical range (e.g. 16 is provided as the month value or 70 for the minute value), the adjacent value will be adjusted. E.g. `new HijriDate(1439, 16, 1)` is equivalent to `new HijriDate(1440, 4, 1)`, both create a date for `1440-05-01` (note that the month is 0-based). Similarly for other values: `new HijriDate(1440, 4, 1, 0, 70)` is equivalent to `new HijriDate(1440, 4, 1, 1, 10)` which both create a date for `1440-05-01T01:10:00`.

**Note:** Where `HijriDate` is called as a constructor with more than one argument, the specified arguments represent local time. If UTC is desired, use `new HijriDate(HijriDate.UTC(...))` with the same arguments.

- **`value`**<br>
  A [Unix Time Stamp](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_16) which is an integer value representing the number of milliseconds since 22 Syawwal 1389, 00:00:00.000 UTC.

- **`fullYear`**<br>
  Integer value representing the full year. Allow value below 1 (0 or negative value) that indicates before Hijra era. Value 0 for 1 BH, -1 for 2 BH, and so forth.

- **`monthIndex`**<br>
  Integer value representing the month, beginning with 0 for Muharram to 11 for Dhul-Hijja.

- **`day`** > optional<br>
  Integer value representing the day of the month.

- **`hours`** (optional)<br>
  Integer value representing the hour of the day.

- **`minutes`** (optional)<br>
  Integer value representing the minute segment of a time.

- **`seconds`** (optional)<br>
  Integer value representing the second segment of a time.

- **`milliseconds`** (optional)<br>
  Integer value representing the millisecond segment of a time.

### Description
* If no arguments are provided, the constructor creates a JavaScript `HijriDate` object for the current date and time according to
system settings for timezone offset.

* If at least two arguments are supplied, missing arguments are either set to 1 (if the day is missing) or 0 for all others.

* The JavaScript Hijri date is based on a time value that is milliseconds since midnight 22 Syawwal 1389 UTC. A day holds 86,400,000 milliseconds. The JavaScript `HijriDate` object range is -103,757,843 days to 104,249,991 days relative to 22 Syawwal 1389 UTC.

* The JavaScript `HijriDate` object provides uniform behavior across platforms. The time value can be passed between systems to create a date that represents the same moment in time.

* The JavaScript `HijriDate` object supports a number of UTC (universal) methods, as well as local time methods. UTC, also known as Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard. The local time is the time known to the computer where JavaScript is executed.

* Invoking JavaScript `HijriDate` as a function (i.e., without the `new` operator) will return a string representing the specified date and time.

## Properties
- **`HijriDate.DIFF`**<br>
  A constant integer value (i.e. -42,521,587,200,000) that is milliseconds value of 1 Muharram 0001 (equivalent to 19 July 0622) relative to 22 Syawwal 1389 (equivalent to 1 January 1970).

- **`HijriDate.MOON_CYCLE`**<br>
  A constant float (i.e. 29.5305882) that is average value of one synodic month of the Moon to completes one orbit around the Earth in days.

- **`HijriDate.prototype`**<br>
  Allows the addition of properties to a JavaScript `HijriDate` object.

## Methods
- **`HijriDate.dayCount(monthCount)`**<br>
  Returns the number of days for a given number of Hijri month specified by `monthCount` parameter since Muharram 0001.

- **`HijriDate.dayCountInMonth(monthCount)`**<br>
  Returns the number of days in a certain Hijri month specified by `monthCount` parameter. `monthCount = 0` is equivalent to Muharram 0001, `monthCount = 1` is equivalent to Safar 0001, `monthCount = 12` is equivalent to Muharram 0002, and so forth. Conversely, if `monthCount = -1` then return value will be negative, it is equivalent to Dhul-Hijja 0001 BH.

- **`HijriDate.now()`**<br>
  Returns the numeric value corresponding to the current time - the number of milliseconds elapsed since 22 Syawwal 1389, 00:00:00 UTC, with leap seconds ignored.

- **`HijriDate.UTC()`**<br>
  Accepts the same parameters as the longest form of the constructor (i.e. 2 to 7) and returns the number of milliseconds since 22 Syawwal 1389, 00:00:00 UTC, with leap seconds ignored.

## JavaScript `HijriDate` instance
All `HijriDate` instances inherit from `HijriDate.prototype`. The prototype object of the `HijriDate` constructor can be modified to affect all `HijriDate` instances.

### `HijriDate.prototype` Methods
#### Getter
- **`.getDate()`**<br>
  Returns the day of the month (1-29 or 1-31) for the specified date according to local time.

- **`.getDay()`**<br>
  Returns the day of the week (0-6) for the specified date according to local time.

- **`.getFullYear()`**<br>
  Returns the year (4 digits for 4-digit years) of the specified date according to local time.

- **`.getHours()`**<br>
  Returns the hour (0-23) in the specified date according to local time.

- **`.getMilliseconds()`**<br>
  Returns the milliseconds (0-999) in the specified date according to local time.

- **`.getMinutes()`**<br>
  Returns the minutes (0-59) in the specified date according to local time.

- **`.getMonth()`**<br>
  Returns the month index (0-11) in the specified date according to local time.

- **`.getSeconds()`**<br>
  Returns the seconds (0-59) in the specified date according to local time.

- **`.getTime()`**<br>
  Returns the numeric value of the specified date as the number of milliseconds since 22 Syawwal 1389, 00:00:00 UTC (negative for prior times).

- **`.getTimezoneOffset()`**<br>
  Returns the time-zone offset in minutes for the current locale.

- **`.getUTCDate()`**<br>
  Returns the day (date) of the month (1-29 or 1-30) in the specified date according to universal time.

- **`.getUTCDay()`**<br>
  Returns the day of the week (0-6) in the specified date according to universal time.

- **`.getUTCFullYear()`**<br>
  Returns the year (4 digits for 4-digit years) in the specified date according to universal time.

- **`.getUTCHours()`**<br>
 Returns the hours (0-23) in the specified date according to universal time.

- **`.getUTCMilliseconds()`**<br>
  Returns the milliseconds (0-999) in the specified date according to universal time.

- **`.getUTCMinutes()`**<br>
  Returns the minutes (0-59) in the specified date according to universal time.

- **`.getUTCMonth()`**<br>
  Returns the month (0-11) in the specified date according to universal time.

- **`.getUTCSeconds()`**<br>
  Returns the seconds (0-59) in the specified date according to universal time.

#### Setter
- **`.setDate()`**<br>
  Sets the day of the month for a specified date according to local time.

- **`.setFullYear()`**<br>
  Sets the full year (e.g. 4 digits for 4-digit years) for a specified date according to local time.

- **`.setHours()`**<br>
  Sets the hours for a specified date according to local time.

- **`.setMilliseconds()`**<br>
  Sets the milliseconds for a specified date according to local time.

- **`.setMinutes()`**<br>
  Sets the minutes for a specified date according to local time.

- **`.setMonth()`**<br>
  Sets the month for a specified date according to local time.

- **`.setSeconds()`**<br>
  Sets the seconds for a specified date according to local time.

- **`.setTime()`**<br>
  Sets the Date object to the time represented by a number of milliseconds since 22 Syawwal 1389, 00:00:00 UTC, allowing for negative numbers for times prior.

- **`.setUTCDate()`**<br>
  Sets the day of the month for a specified date according to universal time.

- **`.setUTCFullYear()`**<br>
  Sets the full year (e.g. 4 digits for 4-digit years) for a specified date according to universal time.

- **`.setUTCHours()`**<br>
  Sets the hour for a specified date according to universal time.

- **`.setUTCMilliseconds()`**<br>
  Sets the milliseconds for a specified date according to universal time.

- **`.setUTCMinutes()`**<br>
  Sets the minutes for a specified date according to universal time.

- **`.setUTCMonth()`**<br>
  Sets the month for a specified date according to universal time.

- **`.setUTCSeconds()`**<br>
  Sets the seconds for a specified date according to universal time.

#### Conversion getter
- **`.toDateString()`**<br>
  Returns the "date" portion of the `HijriDate` as a human-readable string like "Jum JAk 03 1440".

- **`.toISOString()`**<br>
  Converts a date to a string following the ISO 8601 Extended Format.

- **`.toJSON()`**<br>
  Returns a string representing the `HijriDate` using `.toISOString()`. Intended for use by `JSON.stringify()`.

- **`.toString()`**<br>
  Returns a string representing the specified `HijriDate` object. Overrides the `Object.prototype.toString()` method.

- **`.toTimeString()`**<br>
  Returns the "time" portion of the `HijriDate` as a human-readable string.

- **`.toUTCString()`**<br>
  Converts a date to a string using the UTC timezone.

- **`.valueOf()`**<br>
  Returns the primitive value of a `HijriDate` object. Overrides the `Object.prototype.valueOf()` method.

#### Extended getter
By using this library, the following methods will be added to `Date.prototype` as well.

- **`.getDayCountInMonth()`**<br>
  Returns the day count in a specified month according to local time.

- **`.getUTCDayCountInMonth()`**<br>
  Returns the day count in a specified month according to universal time.

&nbsp;

&nbsp;

&nbsp;

---
### Designed by: ZulNs
#### Gorontalo, 10 February 2019
---
