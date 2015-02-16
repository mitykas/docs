{{Page_Title}}
{{Flags
|State=Ready to Use
|Editorial notes=
|Checked_Out=No
|High-level issues=Needs Review
}}
{{Standardization_Status|W3C Working Draft}}
{{API_Name}}
{{Summary_Section|Templates allow you to declare fragments of markup which are parsed as HTML, go unused at page load, but can be instantiated later on at runtime.}}
{{Markup_Element
|DOM_interface=dom/HTMLTemplateElement
|Content=The content of a <code><template></code> element is a hidden portion of the DOM and does not render on page load: scripts don't run, text or images don't display, audio doesn't play, and so forth. Neither are the child nodes of the <code><template></code> accessible with the JavaScript <code>getElementbyId()</code> or <code>querySelector()</code> methods.

Templates can be placed anywhere inside of the <code><head></code>, <code><body></code>, and <code><frameset></code> elements; It can also be used as a child of a <code>&lt;table&gt;</code> or a <code><select></code> element.
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=HTML
|Description====Basic example===
|Code=<syntaxhighlight>
<table>
<tr>
  <template id="cells-to-repeat">
    <td>some content</td>
  </template>
</tr>
</table>
</syntaxhighlight>
|LiveURL=
}}{{Single Example
|Language=JavaScript
|Description=To use a template, you need to activate it. Otherwise its content will not render. The simplest way to do this is by creating a deep copy of its <code>.content </code>using <code>cloneNode()</code>. The <code>.content</code> property is read-only and references a <code>DocumentFragment</code> containing the guts of a template.
|Code=var t = document.querySelector('#mytemplate');
t.content.querySelector('img').src = 'logo.png'; // Populate the src at runtime.
document.body.appendChild(t.content.cloneNode(true));
|LiveURL=
}}{{Single Example
|Language=HTML
|Description====Shadow DOM example===
But the more interesting use of the <code>&lt;template&gt;</code> tag is in concert with the Shadow DOM and the <code>&lt;content&gt;</code> tag. Use the Shadow DOM to achieve an encapsulation of the presentation (style) of the element and the <code>[[html/elements/content|&lt;content&gt;]]</code> tag to provide separation of content from the element. The element (shadow host) is implemented with a <code>&lt;template&gt;</code> that encapsulates the styles, thereby providing a boiler plate, and a <code>[[html/elements/content|&lt;content&gt;]]</code> tag, thereby providing for the reuse of the template for different content.
|Code=<syntaxhighlight>
<template id="nameTagTemplate">
<style>
  …
</style>
<div class="outer">
  <div class="boilerplate">
    Hi! My name is
  </div>
  <div class="name">
    <content></content>
  </div>
</div>
</template>

<div id="nameTag"></div>
</syntaxhighlight>
|LiveURL=
}}{{Single Example
|Language=JavaScript
|Description=Now all you have to do to stamp out the element is run your template through the ShadowRoot.
|Code=var shadow = document.querySelector('#nameTag').webkitCreateShadowRoot();
var template = document.querySelector('#nameTagTemplate');
document.querySelector('#nameTag').textContent = 'Shellie';
shadow.appendChild(template.content);
template.remove();
|LiveURL=
}}
}}
{{Notes_Section
|Usage=The template contents are hidden implicitly since they are not part of the document. The template element itself must be hidden through the user agent style sheet, as in the following:

<syntaxhighlight lang="css">
@namespace "http://www.w3.org/1999/xhtml";

template {
    display : none;
}
</syntaxhighlight>
|Notes=* If you're using [https://code.google.com/p/modpagespeed/ modpagespeed], be careful of this [http://code.google.com/p/modpagespeed/issues/detail?id=625 bug]. Templates that define inline <code><style scoped></code>, many be moved to the <code>head</code> with PageSpeed's CSS rewriting rules.
* There's no way to "prerender" a template, meaning you cannot preload assets, process JS, download initial CSS, etc. That goes for both server and client. The only time a template renders is when it goes live.
* Be careful with nested templates. They don't behave as you might expect, and nested templates must be activated separately.
|Import_Notes=
}}
{{Related_Specifications_Section
|Specifications={{Related_Specification
|Name=HTML 5.1
|URL=http://www.w3.org/TR/html51/scripting-1.html#the-template-element
|Status=W3C Working Draft
|Relevant_changes=
}}{{Related_Specification
|Name=HTML 5
|URL=http://www.w3.org/TR/html5/scripting-1.html#the-template-element
|Status=W3C Recommendation
|Relevant_changes=
}}
}}
{{See_Also_Section
|Topic_clusters=Web Components
|Manual_links=
|External_links=* [http://www.html5rocks.com/en/tutorials/webcomponents/template/ HTML's New Template Tag]
* [http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/ Shadow DOM 101]
|Manual_sections=
}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=HTML5Rocks
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=http://www.html5rocks.com/en/tutorials/webcomponents/template/
}}
{{Compatibility_Section
|Not_required=No
|Imported_tables=
|Desktop_rows={{Compatibility Table Desktop Row
|Chrome_supported=Yes
|Chrome_version=26
|Chrome_prefixed_supported=Unknown
|Chrome_prefixed_version=
|Firefox_supported=Unknown
|Firefox_version=
|Firefox_prefixed_supported=Unknown
|Firefox_prefixed_version=
|Internet_explorer_supported=Unknown
|Internet_explorer_version=
|Internet_explorer_prefixed_supported=Unknown
|Internet_explorer_prefixed_version=
|Opera_supported=Unknown
|Opera_version=
|Opera_prefixed_supported=Unknown
|Opera_prefixed_version=
|Safari_supported=Unknown
|Safari_version=
|Safari_prefixed_supported=Unknown
|Safari_prefixed_version=
}}
|Mobile_rows=
|Notes_rows=
}}