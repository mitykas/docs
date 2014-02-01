{{Page_Title}}
{{Flags
|State=Ready to Use
|Editorial notes=
|Checked_Out=No
}}
{{Summary_Section|Performs a bitwise OR on the value of a variable and the value of an expression and assigns the result to the variable.}}
{{JS_Syntax
|Formats={{JS Syntax Format
|Format=result '''{{!}}=''' expression
}}
|Values={{JS Syntax Parameter
|Name=result
|Required=
|Description=Any variable.
}}{{JS Syntax Parameter
|Name=expression
|Required=
|Description=Any expression.
}}
}}
{{JS_Return_Value
|Description=
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=JavaScript
|Description=See Remarks.
|Code=var x = 5;
x {{!}}= 12; 
// result: x = 13
|LiveURL=
}}
}}
{{Remarks_Section
|Remarks=Using this operator is exactly the same as specifying:

 result = result {{!}} expression
The '''{{!}}=''' operator looks at the binary representation of the values of result and expression and does a bitwise OR operation on them. The result of this operation behaves like this:

 0101    (result)
 1100    (expression)
 ----
 1101    (output)
Any time either of the expressions has a 1 in a digit, the result has a 1 in that digit. Otherwise, the result has a 0 in that digit.
}}
{{Notes_Section
|Usage=
|Notes=
|Import_Notes=
}}
{{JS Object Listing}}
{{Topics | JS Basic}}
{{See_Also_Section
|Manual_links=* [[javascript/operators/bitwise or{{!}}Bitwise OR Operator ({{!}})]]
|External_links=
|Manual_sections=
}}
{{JS Topics
|JS Page Type=JS Basic
|Applies to=
}}
{{External_Attribution
|Is_CC-BY-SA=No
|Sources=MSDN
|MDN_link=
|MSDN_link=http://msdn.microsoft.com/en-us/library/ie/81bads72(v=vs.94).aspx
|HTML5Rocks_link=
}}