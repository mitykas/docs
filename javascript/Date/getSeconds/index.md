---
title: 'getSeconds'
attributions:
  - 'Microsoft Developer Network: [Article](http://msdn.microsoft.com/en-us/library/ie/ct79zx09(v=vs.94).aspx)'
compatibility:
  feature: getSeconds
  topic: javascript
readiness: 'Ready to Use'
summary: 'Gets the seconds of a Date object, using local time.'
tags:
  - JS_Basic
  - JS_Method
uri: javascript/Date/getSeconds

---
## Summary

Gets the seconds of a Date object, using local time.

## Syntax

    dateObj.getSeconds()

## Return Value

Returns an integer between 0 and 59. Zero is returned when the time is less than one second into the current minute. If a **Date** object was created without specifying the time, by default the seconds value is 0.

## Examples

The following example shows how to use the **getSeconds** method.

``` js
var date = new Date("1/1/2001");
 document.write(date.getSeconds());
 document.write("<br/>");

 date.setSeconds(5);
 document.write(date.getSeconds());

 // Output:
 // 0
 // 5
```

## Remarks

The required dateObj reference is a **Date** object. To get the seconds value using Universal Coordinated Time (UTC), use the **getUTCSeconds** method.

## See also

### Other articles

-   [getUTCSeconds Method (Date)](/javascript/Date/getUTCSeconds)
-   [setSeconds Method (Date)](/javascript/Date/setSeconds)
-   [setUTCSeconds Method (Date)](/javascript/Date/setUTCSeconds)

