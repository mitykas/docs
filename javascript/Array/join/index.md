---
title: 'join'
attributions:
  - 'Microsoft Developer Network: [Article](http://msdn.microsoft.com/en-us/library/ie/59x7k999(v=vs.94).aspx)'
compatibility:
  feature: join
  topic: javascript
readiness: 'Ready to Use'
summary: 'Adds all the elements of an array separated by the specified separator string.'
tags:
  - JS_Basic
  - JS_Method
uri: javascript/Array/join

---
## Summary

Adds all the elements of an array separated by the specified separator string.

## Syntax

    join([ separator ])

**separator**
:   Optional. A string used to separate one element of an array from the next in the resulting String. If omitted, the array elements are separated with a comma.

## Examples

The following example illustrates the use of the **join** method.

``` js
var a, b;
 a = new Array(0,1,2,3,4);
 b = a.join( "-" ) ;
 document.write(b);

 // Output:
 // 0-1-2-3-4
```

## Remarks

If any element of the array is **undefined** or null , it is treated as an empty string.

## See also

### Specification

[15.4.4.5 Array.prototype.join (separator)](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.5) ECMAScript® Language Specification Standard ECMA-262 5.1 Edition / June 2011

