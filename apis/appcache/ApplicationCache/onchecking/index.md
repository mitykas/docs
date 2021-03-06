---
title: 'onchecking'
attributions:
  - 'Microsoft Developer Network: [Article](http://msdn.microsoft.com/en-us/library/ie/hh828809%28v=vs.85%29.aspx)'
relationships:
  applies_to:
    predicate: 'Property of '
    value: apis/appcache/ApplicationCache
    href: /apis/appcache/ApplicationCache
  return:
    predicate: 'Returns an object of type '
    value: 'null'
    href: /apis/appcache/ApplicationCache
standardization_status: 'W3C Editor''s Draft'
summary: 'The user agent is checking for an update, or attempting to download the manifest for the first time. This is always the first event in the sequence.'
tags:
  - API_Object_Properties
  - Appcache
  - API
  - Needs_Examples
uri: apis/appcache/ApplicationCache/onchecking

---
## Summary

The user agent is checking for an update, or attempting to download the manifest for the first time. This is always the first event in the sequence.

Property of [apis/appcache/ApplicationCache](/apis/appcache/ApplicationCache)[apis/appcache/ApplicationCache](/apis/appcache/ApplicationCache)

## Syntax

``` js
var result = window.applicationCache.onchecking;
window.applicationCache.onchecking = value;
```

## Return Value

Returns an object of type nullnull

## Notes

If more than one event is triggered and the **checking** event is included, the next events may include **noupdate**, **downloading**, **obsolete**, or **error**. Alternatively, you could use an anonymous delegate function such as

    object.onchecking = function (e) { … }

where e is the cached event.

## Related specifications

[W3C ApplicationCache Specification](http://dev.w3.org/html5/spec/single-page.html#application-cache-api)
:   W3C Editor's Draft
