{{Page_Title}}
{{Flags
|State=In Progress
|Editorial notes=
|Checked_Out=No
|High-level issues=Needs Review
|Content=Compatibility Incomplete
}}
{{Standardization_Status|W3C Working Draft}}
{{API_Name}}
{{Summary_Section|Asynchronously queues small amounts of HTTP data for transfer from the user agent to a web server. For example, it can be used to send analytics or diagnostics code without delaying the page's unload or affecting the performance of the navigation.}}
{{API_Object_Method
|Parameters={{Method Parameter
|Index=0
|Name=url
|Data type=any
|Description=DOMString
|Optional=No
}}{{Method Parameter
|Index=1
|Name=data
|Data type=any
|Description=Must be of one of the following types:
*ArrayBufferView
*Blob
*DOMString
*FormData
|Optional=No
}}
|Method_applies_to=dom/Navigator
|Example_object_name=navigator
|Return_value_name=result
|Javascript_data_type=Boolean
|Return_value_description=Boolean

'''Boolean'''. Returns one of the following possible values:

{{{!}} class="wikitable"
{{!}}-
!Return value
!Description
{{!}}-
{{!}}true
{{!}}The HTTP data was queued for transfer.
{{!}}-
{{!}}false
{{!}}The HTTP data was not queued for transfer.
{{!}}}
 
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=JavaScript
|Description=This example queues data for the server on the pagehide event.
|Code=function() {
  window.addEventListener('pagehide', logData, false);
  function logData() {
    navigator.sendBeacon(
      'https://putsreq.herokuapp.com/Dt7t2QzUkG18aDTMMcop',
       'Sent by a beacon!');
   }
}();
|LiveURL=
}}
}}
{{Notes_Section
|Usage=
|Notes=
|Import_Notes=
}}
{{Related_Specifications_Section
|Specifications={{Related Specification
|Name=Beacon
|URL=http://www.w3.org/TR/beacon/
|Status=W3C Working Draft
|Relevant_changes=
}}
}}
{{See_Also_Section
|Manual_links=
|External_links=
|Manual_sections=
}}
{{Topics|API, DOM}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}
{{Compatibility_Section
|Not_required=No
|Imported_tables=
|Desktop_rows=
|Mobile_rows=
|Notes_rows=
}}