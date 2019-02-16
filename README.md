# HijriDate API Documentation

***

&nbsp;

## Constructor

Creates a JavaScript <code class="hdate"><strong>HijriDate</strong></code> instance that represents a single moment in time.
<code class="hdate">HijriDate</code> objects use a
[Unix&nbsp;Time&nbsp;Stamp](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_16), an integer value that is the number of
milliseconds since 1&nbsp;January&nbsp;1970&nbsp;UTC which is equivalent to 22&nbsp;Syawwal&nbsp;1389&nbsp;UTC.

***

## Syntax

<pre><code><span class="keyword">new</span> <span class="hdate">HijriDate</span>();
<span class="keyword">new</span> <span class="hdate">HijriDate</span>(<i class="value">value</i>);
<span class="keyword">new</span> <span class="hdate">HijriDate</span>(<i class="value">fullYear</i>, <i class="value">monthIndex</i>[, <i class="value">day</i>[, <i class="value">hours</i>[, <i class="value">minutes</i>[, <i class="value">seconds</i>[, <i class="value">milliseconds</i>]]]]]);
</code></pre>

<p class="note"><strong>Note:</strong> JavaScript <code class="hdate">HijriDate</code> objects can only be instantiated by calling JavaScript
<code class="hdate">HijriDate</code> as a constructor: calling it as a regular function (i.e. without the <code class="keyword">new</code> operator) will return
a string rather than a <code class="hdate">HijriDate</code> object; unlike other JavaScript object types, JavaScript <code class="hdate">HijriDate</code>
objects have no literal syntax.</p>

<h3><span class="subtitle">Parameters</span></h3>

<p class="note"><strong>Note:</strong> The argument <code class="value">monthIndex</code> is 0-based. This means that
<code class="value">Muharram&nbsp;=&nbsp;0</code> and <code class="value">Dhul-Hijja&nbsp;=&nbsp;11</code>.</p>

<p class="note"><strong>Note:</strong> Where <code class="hdate">HijriDate</code> is called as a constructor with more than one argument, if values are greater
than their logical range (e.g. 16 is provided as the month value or 70 for the minute value), the adjacent value will be adjusted. E.g.
<code><span class="keyword">new</span>&nbsp;<span class="hdate">HijriDate</span>(<span class="value">1439</span>,&nbsp;<span class="value">16</span>,&nbsp;<span class="value">1</span>)</code>
is equivalent to
<code><span class="keyword">new</span>&nbsp;<span class="hdate">HijriDate</span>(<span class="value">1440</span>,&nbsp;<span class="value">4</span>,&nbsp;<span class="value">1</span>)</code>,
both create a date for <code class="value">1440-05-01</code> (note that the month is 0-based). Similarly for other values:
<code><span class="keyword">new</span>&nbsp;<span class="hdate">HijriDate</span>(<span class="value">1440</span>,&nbsp;<span class="value">4</span>,&nbsp;<span class="value">1</span>,&nbsp;<span class="value">0</span>,&nbsp;<span class="value">70</span>)</code>
is equivalent to
<code><span class="keyword">new</span>&nbsp;<span class="hdate">HijriDate</span>(<span class="value">1440</span>,&nbsp;<span class="value">4</span>,&nbsp;<span class="value">1</span>,&nbsp;<span class="value">1</span>,&nbsp;<span class="value">10</span>)</code>
which both create a date for <code class="value">1440-05-01T01:10:00</code>.</p>

<p class="note"><strong>Note:</strong> Where <code class="hdate">HijriDate</code> is called as a constructor with more than one argument, the specified
arguments represent local time. If UTC is desired, use
<code><span class="keyword">new</span>&nbsp;<span class="hdate">HijriDate</span>(<span class="hdate">HijriDate.UTC</span>(<span class="value">...</span>))</code>
with the same arguments.</p>

<code class="value">value</code><br>
A [Unix&nbsp;Time&nbsp;Stamp](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_16) which is an integer value representing the number of milliseconds since 22&nbsp;Syawwal&nbsp;1389, 00:00:00.000&nbsp;UTC.

<code class="value">fullYear</code><br>
Integer value representing the full year. Allow value below 1 (0 or negative value) that indicates before Hijra era. Value 0 for 1&nbsp;BH, -1 for 2&nbsp;BH, and so forth.

<code class="value">monthIndex</code><br>
Integer value representing the month, beginning with 0 for Muharram to 11 for Dhul-Hijja.

<code class="value">day</code> <span class="option">optional</span><br>
Integer value representing the day of the month.

<code class="value">hours</code> <span class="option">optional</span><br>
Integer value representing the hour of the day.

<code class="value">minutes</code> <span class="option">optional</span><br>
Integer value representing the minute segment of a time.

<code class="value">seconds</code> <span class="option">optional</span><br>
Integer value representing the second segment of a time.

<code class="value">milliseconds</code> <span class="option">optional</span><br>
Integer value representing the millisecond segment of a time.

***

## Description

*   If no arguments are provided, the constructor creates a JavaScript <code class="hdate">HijriDate</code> object for the current date and time according to
system settings for timezone offset.

*   If at least two arguments are supplied, missing arguments are either set to 1 (if the day is missing) or 0 for all others.

*   The JavaScript Hijri date is based on a time value that is milliseconds since midnight 22&nbsp;Syawwal&nbsp;1389&nbsp;UTC. A day holds 86,400,000
milliseconds. The JavaScript <code class="hdate">HijriDate</code> object range is -103,757,843 days to 104,249,991 days relative to
22&nbsp;Syawwal&nbsp;1389&nbsp;UTC.

*   The JavaScript <code class="hdate">HijriDate</code> object provides uniform behavior across platforms. The time value can be passed between systems to
create a date that represents the same moment in time.

*   The JavaScript <code class="hdate">HijriDate</code> object supports a number of UTC (universal) methods, as well as local time methods. UTC, also known as
Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard. The local time is the time known to the computer where JavaScript is executed.

*   Invoking JavaScript <code class="hdate">HijriDate</code> as a function (i.e., without the <code class="keyword">new</code> operator) will return a string
representing the specified date and time.

***

## Properties

<code><span class="hdate">HijriDate</span>.<span class="hdate">DIFF</span></code><br>
A constant integer value (i.e. -42,521,587,200,000) that is milliseconds value of 1&nbsp;Muharram&nbsp;0001 (equivalent to 19&nbsp;July&nbsp;0622) relative to
22&nbsp;Syawwal&nbsp;1389 (equivalent to 1&nbsp;January&nbsp;1970).

<code><span class="hdate">HijriDate</span>.<span class="hdate">MOON_CYCLE</span></code><br>
A constant float (i.e. 29.5305882) that is average value of one synodic month of the Moon to completes one orbit around the Earth in days.

<code><span class="hdate">HijriDate</span>.<span class="hdate">prototype</span></code><br>
Allows the addition of properties to a JavaScript <code class="hdate">HijriDate</code> object.

***

## Methods

<code><span class="hdate">HijriDate.dayCount</span>(<span class="value">monthCount</span>)</code><br>
Returns the number of days for a given number of Hijri month specified by <code class="value">monthCount</code> parameter since Muharram&nbsp;0001.

<code><span class="hdate">HijriDate.dayCountInMonth</span>(<span class="value">monthCount</span>)</code><br>
Returns the number of days in a certain Hijri month specified by <code class="value">monthCount</code> parameter.
<code class="value">monthCount&nbsp;=&nbsp;0</code> is equivalent to Muharram&nbsp;0001, <code class="value">monthCount&nbsp;=&nbsp;1</code> is equivalent to
Safar&nbsp;0001, <code class="value">monthCount&nbsp;=&nbsp;12</code> is equivalent to Muharram&nbsp;0002, and so forth. Conversely, if
<code class="value">monthCount&nbsp;=&nbsp;-1</code> then return value will be negative, it is equivalent to Dhul-Hijja&nbsp;0001&nbsp;BH.

<code><span class="hdate">HijriDate</span>.<span class="hdate">now</span>()</code><br>
Returns the numeric value corresponding to the current time - the number of milliseconds elapsed since 22&nbsp;Syawwal&nbsp;1389, 00:00:00&nbsp;UTC, with leap seconds ignored.

<code><span class="hdate">HijriDate</span>.<span class="hdate">UTC</span>()</code><br>
Accepts the same parameters as the longest form of the constructor (i.e. 2 to 7) and returns the number of milliseconds since 22&nbsp;Syawwal&nbsp;1389, 00:00:00&nbsp;UTC, with leap seconds ignored.

***

## JavaScript <code class="hdate">HijriDate</code> instance

All <code class="hdate">HijriDate</code> instances inherit from <code><span class="hdate">HijriDate</span>.<span class="hdate">prototype</span></code>. The
prototype object of the <code class="hdate">HijriDate</code> constructor can be modified to affect all <code class="hdate">HijriDate</code> instances.

<h3><span class="subtitle"><code style="color:#fff;background-color:transparent">HijriDate.prototype</code> Methods</span></h3>

<h3><span class="subtitle">Getter</span></h3>

<code>.<span class="hdate">getDate</span>()</code><br>
Returns the day of the month (1-29&nbsp;or&nbsp;1-31) for the specified date according to local time.

<code>.<span class="hdate">getDay</span>()</code><br>
Returns the day of the week (0-6) for the specified date according to local time.

<code>.<span class="hdate">getFullYear</span>()</code><br>
Returns the year (4 digits for 4-digit years) of the specified date according to local time.

<code>.<span class="hdate">getHours</span>()</code><br>
Returns the hour (0-23) in the specified date according to local time.

<code>.<span class="hdate">getMilliseconds</span>()</code><br>
Returns the milliseconds (0-999) in the specified date according to local time.

<code>.<span class="hdate">getMinutes</span>()</code><br>
Returns the minutes (0-59) in the specified date according to local time.

<code>.<span class="hdate">getMonth</span>()</code><br>
Returns the month index (0-11) in the specified date according to local time.

<code>.<span class="hdate">getSeconds</span>()</code><br>
Returns the seconds (0-59) in the specified date according to local time.

<code>.<span class="hdate">getTime</span>()</code><br>
Returns the numeric value of the specified date as the number of milliseconds since 22&nbsp;Syawwal&nbsp;1389, 00:00:00&nbsp;UTC (negative for prior times).

<code>.<span class="hdate">getTimezoneOffset</span>()</code><br>
Returns the time-zone offset in minutes for the current locale.

<code>.<span class="hdate">getUTCDate</span>()</code><br>
Returns the day (date) of the month (1-29&nbsp;or&nbsp;1-30) in the specified date according to universal time.

<code>.<span class="hdate">getUTCDay</span>()</code><br>
Returns the day of the week (0-6) in the specified date according to universal time.

<code>.<span class="hdate">getUTCFullYear</span>()</code><br>
Returns the year (4 digits for 4-digit years) in the specified date according to universal time.

<code>.<span class="hdate">getUTCHours</span>()</code><br>
Returns the hours (0-23) in the specified date according to universal time.

<code>.<span class="hdate">getUTCMilliseconds</span>()</code><br>
Returns the milliseconds (0-999) in the specified date according to universal time.

<code>.<span class="hdate">getUTCMinutes</span>()</code><br>
Returns the minutes (0-59) in the specified date according to universal time.

<code>.<span class="hdate">getUTCMonth</span>()</code><br>
Returns the month (0-11) in the specified date according to universal time.

<code>.<span class="hdate">getUTCSeconds</span>()</code><br>
Returns the seconds (0-59) in the specified date according to universal time.

<h3><span class="subtitle">Setter</span></h3>

<code>.<span class="hdate">setDate</span>()</code><br>
Sets the day of the month for a specified date according to local time.

<code>.<span class="hdate">setFullYear</span>()</code><br>
Sets the full year (e.g. 4 digits for 4-digit years) for a specified date according to local time.

<code>.<span class="hdate">setHours</span>()</code><br>
Sets the hours for a specified date according to local time.

<code>.<span class="hdate">setMilliseconds</span>()</code><br>
Sets the milliseconds for a specified date according to local time.

<code>.<span class="hdate">setMinutes</span>()</code><br>
Sets the minutes for a specified date according to local time.

<code>.<span class="hdate">setMonth</span>()</code><br>
Sets the month for a specified date according to local time.

<code>.<span class="hdate">setSeconds</span>()</code><br>
Sets the seconds for a specified date according to local time.

<code>.<span class="hdate">setTime</span>()</code><br>
Sets the Date object to the time represented by a number of milliseconds since 22&nbsp;Syawwal&nbsp;1389, 00:00:00&nbsp;UTC, allowing for negative numbers for times prior.

<code>.<span class="hdate">setUTCDate</span>()</code><br>
Sets the day of the month for a specified date according to universal time.

<code>.<span class="hdate">setUTCFullYear</span>()</code><br>
Sets the full year (e.g. 4 digits for 4-digit years) for a specified date according to universal time.

<code>.<span class="hdate">setUTCHours</span>()</code><br>
Sets the hour for a specified date according to universal time.

<code>.<span class="hdate">setUTCMilliseconds</span>()</code><br>
Sets the milliseconds for a specified date according to universal time.

<code>.<span class="hdate">setUTCMinutes</span>()</code><br>
Sets the minutes for a specified date according to universal time.

<code>.<span class="hdate">setUTCMonth</span>()</code><br>
Sets the month for a specified date according to universal time.

<code>.<span class="hdate">setUTCSeconds</span>()</code><br>
Sets the seconds for a specified date according to universal time.

<h3><span class="subtitle">Conversion getter</span></h3>

<code>.<span class="hdate">toDateString</span>()</code><br>
Returns the "date" portion of the <code class="hdate">HijriDate</code> as a human-readable string like "Jum&nbsp;JAk&nbsp;03&nbsp;1440".

<code>.<span class="hdate">toISOString</span>()</code><br>
Converts a date to a string following the ISO 8601 Extended Format.

<code>.<span class="hdate">toJSON</span>()</code><br>
Returns a string representing the <code class="hdate">HijriDate</code> using <code>.<span class="hdate">toISOString</span>()</code>. Intended for use by
<code><span class="keyword">JSON</span>.<span class="keyword">stringify</span>()</code>.

<code>.<span class="hdate">toString</span>()</code><br>
Returns a string representing the specified <code class="hdate">HijriDate</code> object. Overrides the
<code><span class="keyword">Object</span>.<span class="keyword">prototype</span>.<span class="keyword">toString</span>()</code> method.

<code>.<span class="hdate">toTimeString</span>()</code><br>
Returns the "time" portion of the <code class="hdate">HijriDate</code> as a human-readable string.

<code>.<span class="hdate">toUTCString</span>()</code><br>
Converts a date to a string using the UTC timezone.

<code>.<span class="hdate">valueOf</span>()</code><br>
Returns the primitive value of a <code class="hdate">HijriDate</code> object. Overrides the
<code><span class="keyword">Object</span>.<span class="keyword">prototype</span>.<span class="keyword">valueOf</span>()</code> method.

<h3><span class="subtitle">Extended getter</span></h3>

By using this library, the following methods will be added to <code><span class="keyword">Date</span>.<span class="keyword">prototype</span></code> as well.

<code>.<span class="hdate">getDayCountInMonth</span>()</code><br>
Returns the day count in a specified month according to local time.

<code>.<span class="hdate">getUTCDayCountInMonth</span>()</code><br>
Returns the day count in a specified month according to universal time.

&nbsp;

&nbsp;

&nbsp;

---
### Designed&nbsp;by:&nbsp;<span class="tag" style="color:#fff;background-color:#f44336">Z</span>&nbsp;<span class="tag" style="color:#000;background-color:#ffeb3b">u</span>&nbsp;<span class="tag black" style="color:#fff;background-color:#000">l</span>&nbsp;<span class="tag" style="color:#000;background-color:#00bcd4">N</span>&nbsp;<span class="tag" style="color:#fff;background-color:#9c27b0">s</span>
### Gorontalo,&nbsp;10&nbsp;February&nbsp;2019
---

<style rel="stylesheet" type="text/css">
.hdate{color:#009688}
.keyword{color:#2196F3}
.value{color:#f44336}
pre{border-left:6px solid #009688;padding-left:16px;background-color:#ddffdd}
pre>code{background-color:#ddffdd}
.note{border-left:6px solid #ffeb3b;padding:8px 8px 8px 16px;background-color:#ffffcc}
.option{border-left:4px solid #616161;background-color:#f1f1f1;margin-left:16px;padding:2px 6px 2px 12px}
.subtitle{color:#fff;background-color:#616161;padding:2px 8px 2px 24px}
.tag{display:inline-block;width:36px;padding:12px 0px;text-align:center}
</style>
