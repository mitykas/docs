---
title: 'forward'
attributions:
  - 'Microsoft Developer Network: [[Windows Internet Explorer API reference](http://msdn.microsoft.com/en-us/library/ie/hh828809%28v=vs.85%29.aspx) Article]'
notes:
  - 'Summary, examples, compatibility, clean-up of MSDN import'
readiness: 'Not Ready'
relationships:
  method_of:
    predicate: 'Method of '
    value: dom/History
    href: /dom/History
  return_type:
    predicate: 'Returns an object of type  '
    value: 'DOM Node'
    href: /dom/History
standardization_status: Non-Standard
tags:
  - API_Object_Methods
  - DOM
  - Needs_Summary
  - Needs_Examples
uri: dom/History/forward

---
Method of [dom/History](/dom/History)[dom/History](/dom/History)

## Syntax

``` js
var object = object.forward();
```

## Return Value

Returns an object of type DOM NodeDOM Node

Type: **HRESULT**

If this method succeeds, it returns **S\_OK**. Otherwise, it returns an **HRESULT** error code.

## Notes

### Remarks

This method performs the same action as when a user clicks the **Forward** button in the browser. Calling the **forward** method works the same as calling the **go** method with a parameter of `1`. An error does not occur if the user tries to go beyond the end of the history. Instead, the user remains at the current page.

### Syntax

### Standards information

There are no standards that apply here.

## See also

### Related pages

-   `history`
-   `Reference`
-   `back`
-   `go`
