---
title: 'getUTCMinutes'
attributions:
  - 'Microsoft Developer Network: [Article](http://msdn.microsoft.com/en-us/library/ie/7xt0y1cc(v=vs.94).aspx)'
compatibility:
  feature: getUTCMinutes
  topic: javascript
readiness: 'Ready to Use'
summary: 'Gets the minutes of a Date object using Universal Coordinated Time (UTC).'
tags:
  - JS_Basic
  - JS_Method
uri: javascript/Date/getUTCMinutes

---
## Summary

Gets the minutes of a Date object using Universal Coordinated Time (UTC).

## Syntax

    dateObj.getUTCMinutes()

## Return Value

Returns an integer between 0 and 59. Zero is returned the time is less than one minute after the hour. If a **Date** object was created without specifying the time, by default the UTC minute value is 0. However, in other time zones it may be different.

## Examples

The following example illustrates the use of the **getUTCMinutes** method.

``` js
var date = new Date("1/1/2001");
 document.write(date.getUTCMinutes());
 document.write("<br/>");

 date.setMinutes(5);
 document.write(date.getUTCMinutes());

 // Output:
 // 0
 // 5
```

## Remarks

The required dateObj reference is a **Date** object. To get the number of minutes stored using local time, use the **getMinutes** method.

## See also

### Other articles

-   [getMinutes Method (Date)](/javascript/Date/getMinutes)
-   [setMinutes Method (Date)](/javascript/Date/setMinutes)
-   [setUTCMinutes Method (Date)](/javascript/Date/setUTCMinutes)

