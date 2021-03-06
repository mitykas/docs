---
title: 'createLinearGradient'
attributions:
  - 'Microsoft Developer Network: [Windows Internet Explorer API reference Article](http://msdn.microsoft.com/en-us/library/ie/hh828809%28v=vs.85%29.aspx)'
readiness: 'Ready to Use'
relationships:
  method_of:
    predicate: 'Method of '
    value: apis/canvas/CanvasRenderingContext2D
    href: /apis/canvas/CanvasRenderingContext2D
  return_type:
    predicate: 'Returns an object of type  '
    value: 'DOM Node'
    href: /apis/canvas/CanvasRenderingContext2D
standardization_status: 'W3C Candidate Recommendation'
summary: 'Returns a linear CanvasGradient initialized with the specified line as represented by the start point (x0, y0) and end point (x1, y1) of the gradient.'
tags:
  - API_Object_Methods
  - API
  - Canvas
uri: apis/canvas/CanvasRenderingContext2D/createLinearGradient

---
## Summary

Returns a linear CanvasGradient initialized with the specified line as represented by the start point (x0, y0) and end point (x1, y1) of the gradient.

Method of [apis/canvas/CanvasRenderingContext2D](/apis/canvas/CanvasRenderingContext2D)[apis/canvas/CanvasRenderingContext2D](/apis/canvas/CanvasRenderingContext2D)

## Syntax

``` js
var object = object.createLinearGradient(x0, y0, x1, y1);
```

## Parameters

### x0

 Data-type
:   Number

 The x-coordinate, in pixels, of the start point of the gradient.

### y0

 Data-type
:   Number

 The y-coordinate, in pixels, of the start point of the gradient.

### x1

 Data-type
:   Number

 The x-coordinate, in pixels, of the end point of the gradient.

### y1

 Data-type
:   Number

 The y-coordinate, in pixels, of the end point of the gradient.

## Return Value

Returns an object of type DOM NodeDOM Node

A **CanvasGradient** object that represents the new linear gradient.

## Examples

This example creates a diagonal (upper left to lower right) gradient, fading from red to yellow, and then places a rectangle filled with the gradient onto the canvas.

``` html
<canvas id="myCanvas" width="300" height="150" style="border:1px solid blue;"></canvas>
<p>. . .</p>
<script>
var can = document.getElementById("myCanvas");
var ctxt = can.getContext("2d");
var grdt = ctxt.createLinearGradient(0, 0, 150, 150);
grdt.addColorStop(0, "red");
grdt.addColorStop(1, "yellow");
ctxt.fillStyle = grdt;
ctxt.fillRect(20, 20, 150, 100);
</script>
```

## Related specifications

[W3C HTML Canvas 2D Context](http://www.w3.org/TR/2dcontext/)
:   W3C Candidate Recommendation
