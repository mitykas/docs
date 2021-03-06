---
title: 'text-decoration-line'
attributions:
  - 'Mozilla Developer Network [![cc-by-sa-small-wpd.svg](/assets/thumb/8/8c/cc-by-sa-small-wpd.svg/120px-cc-by-sa-small-wpd.svg.png)](http://creativecommons.org/licenses/by-sa/3.0/us/): [Article](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration-line)'
code_samples:
  - 'http://code.webplatform.org/gist/7283909'
compatibility:
  feature: text-decoration-line
  topic: css
overview_table:
  '[Initial value](/css/concepts/initial_value)': '`none`'
  'Applies to': 'All elements'
  '[Inherited](/css/concepts/inherited)': 'No'
  Media: visual
  '[Computed value](/css/concepts/computed_value)': 'as specified'
  Animatable: 'No'
  '[CSS Object Model Property](/css/concepts/cssom)': '`textDecorationLine`'
readiness: 'Ready to Use'
standardization_status: 'W3C Candidate Recommendation'
summary: 'Sets what kind of line decorations are added to an element, such as underlines, overlines, etc.'
tags:
  - CSS_Properties
  - CSS
uri: css/properties/text-decoration-line

---
## Summary

Sets what kind of line decorations are added to an element, such as underlines, overlines, etc.

## Overview table

[Initial value](/css/concepts/initial_value)
:   `none`

Applies to
:   All elements

[Inherited](/css/concepts/inherited)
:   No

Media
:   visual

[Computed value](/css/concepts/computed_value)
:   as specified

Animatable
:   No

[CSS Object Model Property](/css/concepts/cssom)
:   `textDecorationLine`

## Syntax

-   `text-decoration-line: blink`
-   `text-decoration-line: line-through`
-   `text-decoration-line: none`
-   `text-decoration-line: overline`
-   `text-decoration-line: underline`

## Values

none
:   Produces no text decoration.

underline
:   Each line of text is underlined.

overline
:   Each line of text has a line above it.

line-through
:   Each line of text has a line through the middle.

blink
:   The text alternates between visible and invisible.

## Examples

``` css
p:nth-child(1) { text-decoration-line: none; }
p:nth-child(2) { text-decoration-line: underline; }
p:nth-child(3) { text-decoration-line: overline; }
p:nth-child(4) { text-decoration-line: line-through; }
p:nth-child(5) { text-decoration-line: blink; }
```

[View live example](http://code.webplatform.org/gist/7283909)

## Notes

The text-decoration-line property is the equivalent of the text-decoration property before it was converted to a shorthand property in CSS Text Decoration Level 3.

## Related specifications

[CSS Text-decoration Level 3](http://www.w3.org/TR/css-text-decor-3/)
:   Working Draft
