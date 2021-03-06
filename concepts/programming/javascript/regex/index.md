---
title: 'Regular Expressions'
attributions:
  - 'This article contains content originally from external sources, including ones licensed under the CC-BY-SA license. [![cc-by-sa-small-wpd.png](/assets/public/c/c8/cc-by-sa-small-wpd.png)](http://creativecommons.org/licenses/by-sa/3.0/us/)'
  - 'Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network: [Article](https://developer.mozilla.org/en-US/docs/JavaScript/Guide/Regular_Expressions)'
notes:
  - 'Require manual conversion! See https://github.com/webplatform/mediawiki-conversion/issues/24'
readiness: 'Not Ready'
tags:
  - JavaScript
  - Needs_Summary
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - concepts/programming/javascript/regex/js/objects/RegExp
    - concepts/programming/javascript/regex/js
    - concepts/programming/javascript/regex/js/objects/RegExp/exec
    - concepts/programming/javascript/regex/js/objects/RegExp/test
    - concepts/programming/javascript/regex/js/objects/String/match
    - concepts/programming/javascript/regex/js/objects/String/search
    - concepts/programming/javascript/regex/js/objects/String/replace
    - concepts/programming/javascript/regex/js/objects/String/split
uri: concepts/programming/javascript/regex

---
<h2 id="Creating_a_Regular_Expression">Creating a Regular Expression</h2>
<p>You construct a regular expression in one of two ways:</p>
<ul><li>Using a regular expression literal, as follows:
      <pre>
var re = /ab+c/;
</pre>
    <p>Regular expression literals provide compilation of the regular expression when the script is evaluated. When the regular expression will remain constant, use this for better performance.</p>
  </li>
  <li>Calling the constructor function of the <code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/RegExp&amp;action=edit&amp;redlink=1" class="new">RegExp</a></code> object, as follows:
      <pre>
var re = new RegExp("ab+c");
</pre>
    <p>Using the constructor function provides runtime compilation of the regular expression. Use the constructor function when you know the regular expression pattern will be changing, or you don't know the pattern and are getting it from another source, such as user input.</p>
  </li>
</ul><h2 id="Writing_a_Regular_Expression_Pattern">Writing a Regular Expression Pattern</h2>
<p>A regular expression pattern is composed of simple characters, such as <code>/abc/</code>, or a combination of simple and special characters, such as <code>/ab*c/</code> or <code>/Chapter (\d+)\.\d*/</code>. The last example includes parentheses which are used as a memory device. The match made with this part of the pattern is remembered for later use, as described in <a href="#Using_Parenthesized_Substring_Matches">Using Parenthesized Substring Matches</a>.</p>
<h3 id="Using_Simple_Patterns">Using Simple Patterns</h3>
<p>Simple patterns are constructed of characters for which you want to find a direct match. For example, the pattern <code>/abc/</code> matches character combinations in strings only when exactly the characters 'abc' occur together and in that order. Such a match would succeed in the strings "Hi, do you know your abc's?" and "The latest airplane designs evolved from slabcraft." In both cases the match is with the substring 'abc'. There is no match in the string "Grab crab" because it does not contain the substring 'abc'.</p>
<h3 id="Using_Special_Characters">Using Special Characters</h3>
<p>When the search for a match requires something more than a direct match, such as finding one or more b's, or finding white space, the pattern includes special characters. For example, the pattern <code>/ab*c/</code> matches any character combination in which a single 'a' is followed by zero or more 'b's (<code>*</code> means 0 or more occurrences of the preceding item) and then immediately followed by 'c'. In the string "cbbabbbbcdebc," the pattern matches the substring 'abbbbc'.</p>
<p>The following table provides a complete list and description of the special characters that can be used in regular expressions.</p>
<table><caption> Table 4.1 Special characters in regular expressions.
</caption>
<tr><th scope="col"> Character
</th>
<th style="text-align:left;" scope="col"> Meaning
</th></tr><tr><th scope="row" id="special-backslash"> <code>\</code>
</th>
<td> Either of the following:
<ul><li> For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally.
<dl><dt> <code>/b/</code></dt>
<dd> matches the character "<i>b</i>". By placing a backslash in front of <i>b</i>, that is by using <code>/\b/</code>, the character becomes special to mean match a word boundary.</dd></dl></li>
<li> For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally.
<dl><dt> <code>*</code></dt>
<dd> is a special character that means 0 or more occurrences of the preceding item should be matched; for example, <code>/a*/</code> means match 0 or more a's. To match <code>*</code> literally, precede it with a backslash; for example, <code>/a\*/</code> matches 'a*'.</dd>
<dt> Also</dt>
<dd> do not forget to escape \ itself while using the <code>new RegExp("pattern")</code> notation since <code>\</code> is also an escape character in strings.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-caret"><code>^</code>
</th>
<td>
<ul><li> Matches beginning of input. If the multiline flag is set to true, also matches immediately after a line break character.</li>
<li> For example;
<dl><dt> <code>/^A/</code></dt>
<dd> does not match the 'A' in "an A", but does match the 'A' in "An E". This character means 'not' when it appears as the first character in a character set pattern.</dd>
<dt> <code>/[^A-Za-z\s]/</code></dt>
<dd> matches any character that is not a letter or whitespace, and so would match the '3' in "I have 3 sisters".</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-dollar"> <code>$</code>
</th>
<td>
<ul><li> Matches end of input. If the multiline flag is set to true, also matches immediately before a line break character.</li>
<li> For example;
<dl><dt> <code>/t$/</code></dt>
<dd> does not match the 't' in "eater", but does match it in "eat".</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-asterisk"> <code>*</code>
</th>
<td>
<ul><li> Matches the preceding character 0 or more times.</li>
<li> For example;
<dl><dt> <code>/bo*/</code></dt>
<dd> matches 'boooo' in "A ghost booooed" and "<i>b</i>" in "A bird warbled", but nothing in "A goat grunted".</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-plus"> <code>+</code>
</th>
<td>
<ul><li> Matches the preceding character 1 or more times. Equivalent to <code>{1,}</code></li>
<li> For example;
<dl><dt> <code>/a+/</code></dt>
<dd> matches the 'a' in "candy" and all the a's in "caaaaaaandy".</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-questionmark"> <code>?</code>
</th>
<td>
<ul><li> Matches the preceding character 0 or 1 time. Equivalent to {0,1}.</li>
<li> For example;
<dl><dt> <code>/e?le?/</code></dt>
<dd> matches the 'el' in "angel" and the 'le' in "angle" and also the 'l' in "oslo".</dd>
<dt> </dt>
<dd> If used immediately after any of the quantifiers <code>*</code>, <code>+</code>, <code>?</code>, or <code>{}</code>, makes the quantifier non-greedy (matching the minimum number of times), as opposed to the default, which is greedy (matching the maximum number of times). </dd>
<dt> <code>/\d+/</code> non-global</dt>
<dd> match "123abc" return "123", if using /\d+?/, only "1" will be matched.</dd></dl></li>
<li> Also used in lookahead assertions, described under x(?=y) and x(?!y) in this table.&lt;/p&gt;</li></ul></td></tr><tr><th scope="row" id="special-dot"> <code>.</code>
</th>
<td>
<ul><li> (The decimal point) matches any single character except the newline character.</li>
<li> For example;
<dl><dt> <code>/.n/</code></dt>
<dd> matches 'an' and 'on' in "nay, an apple is on the tree", but not 'nay'.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-capturing-parentheses"> <code>(x)</code>
</th>
<td>
<ul><li> Matches 'x' and remembers the match. These are called capturing parentheses.</li>
<li> For example;
<dl><dt> <code>/(foo)/</code></dt>
<dd> matches and remembers 'foo' in "foo bar." The matched substring can be recalled from the resulting array's elements <code>[1]</code>, ..., <code>[n]</code>.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-non-capturing-parentheses"> <code>(?:x)</code>
</th>
<td>
<ul><li> Matches 'x' but does not remember the match. These are called non-capturing parentheses. The matched substring can not be recalled from the resulting array's elements <code>[1]</code>, ..., <code>[n]</code></li></ul></td></tr><tr><th scope="row" id="special-lookahead"> <code>x(?=y)</code>
</th>
<td>
<ul><li> Matches 'x' only if 'x' is followed by 'y'. This is called a lookahead.</li>
<li> For example;
<dl><dt> <code>/Jack(?=Sprat)/</code></dt>
<dd> matches 'Jack' only if it is followed by 'Sprat'. <code>/Jack(?=Sprat|Frost)/</code> matches 'Jack' only if it is followed by 'Sprat' or 'Frost'. However, neither 'Sprat' nor 'Frost' is part of the match results.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-negated-look-ahead"> <code>x(?!y)</code>
</th>
<td>
<ul><li> Matches 'x' only if 'x' is not followed by 'y'. This is called a negated lookahead.</li>
<li> For example;
<dl><dt> <code>/\d+(?!\.)/</code></dt>
<dd> matches a number only if it is not followed by a decimal point. The regular expression <code>/\d+(?!\.)/.exec("3.141")</code> matches '<code>141</code>' but not '<code>3.141</code>'.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-or"> <code>x|y</code>
</th>
<td>
<ul><li> Matches either 'x' or 'y'.</li>
<li> For example;
<dl><dt> <code>/green|red/</code></dt>
<dd> matches 'green' in "green apple" and 'red' in "red apple."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-quantifier"> <code>{n}</code>
</th>
<td>
<ul><li> Where <code>n</code> is a positive integer. Matches exactly <code>n</code> occurrences of the preceding character.</li>
<li> For example;
<dl><dt> <code>/a{2}/</code></dt>
<dd> doesn't match the 'a' in "candy," but it matches all of the a's in "caandy," and the first two a's in "caaandy."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-quantifier-range"> <code>{n,m}</code>
</th>
<td>
<ul><li> Where <code>n</code> and <code>m</code> are positive integers. Matches at least <code>n</code> and at most <code>m</code> occurrences of the preceding character. When either <code>n</code> or <code>m</code> is zero, it can be omitted.</li>
<li> For example;
<dl><dt> <code>/a{1,3}/</code></dt>
<dd> matches nothing in "cndy", the 'a' in "candy," the first two a's in "caandy," and the first three a's in "caaaaaaandy" Notice that when matching "caaaaaaandy", the match is "aaa", even though the original string had more a's in it.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-character-set"> <code>[xyz]</code>
</th>
<td>
<ul><li> A character set. Matches any one of the enclosed characters. You can specify a range of characters by using a hyphen. Special characters (such as the dot (<code>.</code>) and the asterisk (<code>*</code>)) do not have any special meaning inside a character set. They need not be escaped. Escape sequences also work.</li>
<li> For example;
<dl><dt> <code>[abcd]</code></dt>
<dd> is the same as <code>[a-d]</code>. They match the 'b' in "brisket" and the 'c' in "city". <code>/[a-z.]+/</code> and <code>/[\w.]+/</code> both match everything in "<code>test.i.ng</code>".</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-negated-character-set"> <code>[^xyz]</code>
</th>
<td>
<ul><li> A negated or complemented character set. That is, it matches anything that is not enclosed in the brackets. You can specify a range of characters by using a hyphen. Everything that works in the normal character set also works here.</li>
<li> For example;
<dl><dt> <code>[^abc]</code></dt>
<dd> is the same as <code>[^a-c]</code>. They initially match 'r' in "brisket" and 'h' in "chop."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-backspace"> <code>[\b]</code>
</th>
<td>
<ul><li> Matches a backspace <code>(U+0008)</code>. (Not to be confused with <code>\b</code>.) </li></ul></td></tr><tr><th scope="row" id="special-word-boundary"> <code>\b</code>
</th>
<td>
<ul><li> Matches a word boundary. A word boundary matches the position where a word character is not followed or preceeded by another word-character. Note that a matched word boundary is not included in the match. In other words, the length of a matched word boundary is zero. (Not to be confused with <code>[\b]</code>.)</li>
<li> For example;
<dl><dt>  <code>/\bmoo/</code></dt>
<dd> matches the 'moo' in "moon"</dd>
<dt>  <code>/oo\b/</code></dt>
<dd> does not match the 'oo' in "moon", because 'oo' is followed by 'n' which is a word character;</dd>
<dt>  <code>/oon\b/</code></dt>
<dd> matches the 'oon' in "moon", because 'oon' is the end of the string, thus not followed by a word character;</dd>
<dt>  <code>/\w\b\w/</code></dt>
<dd> will never match anything, because a word character can never be followed by both a non-word and a word character.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-non-word-boundary"> <code>\B</code>
</th>
<td>
<ul><li> Matches a non-word boundary. This matches a position where the previous and next character are of the same type: Either both must be words, or both must be non-words. The beginning and end of a string are considered non-words.</li>
<li> For example;
<dl><dt> <code>/\B../</code></dt>
<dd> matches 'oo' in "noonday" </dd>
<dt> <code>/y\B./</code></dt>
<dd> matches 'ye' in "possibly yesterday."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-control"> <code>\c<em>X</em></code>
</th>
<td>
<ul><li> Where <em>X</em> is a character ranging from A to Z. Matches a control character in a string.</li>
<li> For example;
<dl><dt> <code>/\cM/</code></dt>
<dd> matches control-M (U+000D) in a string.</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-digit"> <code>\d</code>
</th>
<td> *  Matches a digit character. Equivalent to <code>[0-9]</code>.
<ul><li> For example;
<dl><dt> <code>/\d/</code> or <code>/[0-9]/</code></dt>
<dd> matches '2' in "B2 is the suite number."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-non-digit"> <code>\D</code>
</th>
<td>
<ul><li> Matches any non-digit character. Equivalent to <code>[^0-9]</code>.</li>
<li> For example;
<dl><dt> <code>/\D/</code> or <code>/[^0-9]/</code></dt>
<dd> matches 'B' in "B2 is the suite number."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-form-feed"> <code>\f</code>
</th>
<td>
<ul><li> Matches a form feed <code>(U+000C)</code>.</li></ul></td></tr><tr><th scope="row" id="special-line-feed"> <code>\n</code>
</th>
<td>
<ul><li> Matches a line feed <code>(U+000A)</code>.</li></ul></td></tr><tr><th scope="row" id="special-carriage-return"> <code>\r</code>
</th>
<td> *  Matches a carriage return (U+000D).
</td></tr><tr><th scope="row" id="special-white-space"> <code>\s</code>
</th>
<td>
<ul><li> Matches a single white space character, including space, tab, form feed, line feed. Equivalent to <code>[ \f\n\r\t\v​\u00A0\u1680​\u180e\u2000​\u2001\u2002​\u2003\u2004​\u2005\u2006​\u2007\u2008​\u2009\u200a​\u2028\u2029​\u2028\u2029​\u202f\u205f​\u3000]</code>.</li>
<li> For example;
<dl><dt> <code>/\s\w*/</code></dt>
<dd> matches ' bar' in "foo bar."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-non-white-space"> <code>\S</code>
</th>
<td>
<ul><li>  Matches a single character other than white space. Equivalent to <code>[^ \f\n\r\t\v​\u00A0\u1680​\u180e\u2000​\u2001\u2002​\u2003\u2004​\u2005\u2006​\u2007\u2008​\u2009\u200a​\u2028\u2029​\u2028\u2029​\u202f\u205f​\u3000]</code>.</li>
<li> For example;
<dl><dt> <code>/\S\w*/</code></dt>
<dd> matches 'foo' in "foo bar."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-tab"> <code>\t</code>
</th>
<td>
<ul><li> Matches a tab <code>(U+0009)</code>.</li></ul></td></tr><tr><th scope="row" id="special-vertical-tab"> <code>\v</code>
</th>
<td>
<ul><li> Matches a vertical tab <code>(U+000B)</code>. </li></ul></td></tr><tr><th scope="row" id="special-word"> <code>\w</code>
</th>
<td>
<ul><li> Matches any alphanumeric character including the underscore. Equivalent to <code>[A-Za-z0-9_]</code>.</li>
<li> For example;
<dl><dt> <code>/\w/</code></dt>
<dd> matches 'a' in "apple," '5' in "$5.28," and '3' in "3D."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-non-word"> <code>\W</code>
</th>
<td>
<ul><li> Matches any non-word character. Equivalent to <code>[^A-Za-z0-9_]</code>.</li>
<li> For example;
<dl><dt> <code>/\W/</code> or <code>/[^A-Za-z0-9_]/</code></dt>
<dd> matches '%' in "50%."</dd></dl></li></ul></td></tr><tr><th scope="row" id="special-backreference"> <code>\<em>n</em></code>
</th>
<td>
<ul><li> Where <em>n</em> is a positive integer. A back reference to the last substring matching the <em>n</em> parenthetical in the regular expression (counting left parentheses).</li>
<li> For example;
<dl><dt> <code>/apple(,)\sorange\1/</code></dt>
<dd> matches 'apple, orange,' in "apple, orange, cherry, peach." </dd></dl></li></ul></td></tr><tr><th scope="row" id="special-null"> <code>\0</code>
</th>
<td>
<ul><li> Matches a NULL (U+0000) character. Do not follow this with another digit, because <code>\0&lt;digits&gt;</code> is an octal escape sequence.</li></ul></td></tr><tr><th scope="row" id="special-hex-escape"> <code>\xhh</code>
</th>
<td>
<ul><li> Matches the character with the code hh (two hexadecimal digits)</li></ul></td></tr><tr><th scope="row" id="special-unicode-escape"> <code>\uhhhh</code>
</th>
<td>
<ul><li> Matches the character with the code hhhh (four hexadecimal digits).</li></ul></td></tr></table><h3 id="Using_Parentheses">Using Parentheses</h3>
<p>Parentheses around any part of the regular expression pattern cause that part of the matched substring to be remembered. Once remembered, the substring can be recalled for other use, as described in <a href="#Using_Parenthesized_Substring_Matches">Using Parenthesized Substring Matches</a>.</p>
<p>For example, the pattern <code>/Chapter (\d+)\.\d*/</code> illustrates additional escaped and special characters and indicates that part of the pattern should be remembered. It matches precisely the characters 'Chapter ' followed by one or more numeric characters (<code>\d</code> means any numeric character and <code>+</code> means 1 or more times), followed by a decimal point (which in itself is a special character; preceding the decimal point with \ means the pattern must look for the literal character '.'), followed by any numeric character 0 or more times (<code>\d</code> means numeric character, <code>*</code> means 0 or more times). In addition, parentheses are used to remember the first matched numeric characters.</p>
<p>This pattern is found in "Open Chapter 4.3, paragraph 6" and '4' is remembered. The pattern is not found in "Chapter 3 and 4", because that string does not have a period after the '3'.</p>
<p>To match a substring without causing the matched part to be remembered, within the parentheses preface the pattern with <code>?:</code>. For example, <code>(?:\d+)</code> matches one or more numeric characters but does not remember the matched characters.</p>
<h2 id="Working_with_Regular_Expressions">Working with Regular Expressions</h2>
<p>Regular expressions are used with the <code>RegExp</code> methods <code>test</code> and <code>exec</code> and with the <code>String</code> methods <code>match</code>, <code>replace</code>, <code>search</code>, and <code>split</code>. These methods are explained in detail in the <a href="/w/index.php?title=concepts/programming/javascript/regex/js&amp;action=edit&amp;redlink=1" class="new">JavaScript Reference</a>.</p>
<table class="standard-table"><caption style="text-align: left">
    Table 4.2 Methods that use regular expressions</caption>
  &lt;thead&gt;
    <tr><th scope="col">Method</th>
      <th scope="col">Description</th>
    </tr>
  &lt;/thead&gt;
  &lt;tbody&gt;
    <tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/RegExp/exec&amp;action=edit&amp;redlink=1" class="new">exec</a></code></td>
      <td>A <code>RegExp</code> method that executes a search for a match in a string. It returns an array of information.</td>
    </tr><tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/RegExp/test&amp;action=edit&amp;redlink=1" class="new">test</a></code></td>
      <td>A <code>RegExp</code> method that tests for a match in a string. It returns true or false.</td>
    </tr><tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/String/match&amp;action=edit&amp;redlink=1" class="new">match</a></code></td>
      <td>A <code>String</code> method that executes a search for a match in a string. It returns an array of information or null on a mismatch.</td>
    </tr><tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/String/search&amp;action=edit&amp;redlink=1" class="new">search</a></code></td>
      <td>A <code>String</code> method that tests for a match in a string. It returns the index of the match, or -1 if the search fails.</td>
    </tr><tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/String/replace&amp;action=edit&amp;redlink=1" class="new">replace</a></code></td>
      <td>A <code>String</code> method that executes a search for a match in a string, and replaces the matched substring with a replacement substring.</td>
    </tr><tr><td><code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/String/split&amp;action=edit&amp;redlink=1" class="new">split</a></code></td>
      <td>A <code>String</code> method that uses a regular expression or a fixed string to break a string into an array of substrings.</td>
    </tr>
  &lt;/tbody&gt;
</table><p>When you want to know whether a pattern is found in a string, use the <code>test</code> or <code>search</code> method; for more information (but slower execution) use the <code>exec</code> or <code>match</code> methods. If you use <code>exec</code> or <code>match</code> and if the match succeeds, these methods return an array and update properties of the associated regular expression object and also of the predefined regular expression object, <code>RegExp</code>. If the match fails, the <code>exec</code> method returns <code>null</code> (which converts to <code>false</code>).</p>
<p>In the following example, the script uses the <code>exec</code> method to find a match in a string.</p>
<pre>
var myRe = /d(b+)d/g;
var myArray = myRe.exec("cdbbdbsbz");
</pre>
<p>If you do not need to access the properties of the regular expression, an alternative way of creating <code>myArray</code> is with this script:</p>
<pre>
var myArray = /d(b+)d/g.exec("cdbbdbsbz");
</pre>
<p>If you want to construct the regular expression from a string, yet another alternative is this script:</p>
<pre>
var myRe = new RegExp("d(b+)d", "g");
var myArray = myRe.exec("cdbbdbsbz");
</pre>
<p>With these scripts, the match succeeds and returns the array and updates the properties shown in the following table.</p>
<table><caption style="text-align: left">
    Table 4.3 Results of regular expression execution.</caption>
  &lt;thead&gt;
    <tr><th scope="col">Object</th>
      <th scope="col">Property or index</th>
      <th scope="col">Description</th>
      <th scope="col">In this example</th>
    </tr>
  &lt;/thead&gt;
  &lt;tbody&gt;
    <tr><td rowspan="4"><code>myArray</code></td>
      <td> </td>
      <td>The matched string and all remembered substrings.</td>
      <td><code>["dbbd", "bb"]</code></td>
    </tr><tr><td><code>index</code></td>
      <td>The 0-based index of the match in the input string.</td>
      <td><code>1</code></td>
    </tr><tr><td><code>input</code></td>
      <td>The original string.</td>
      <td><code>"cdbbdbsbz"</code></td>
    </tr><tr><td><code>[0]</code></td>
      <td>The last matched characters.</td>
      <td><code>"dbbd"</code></td>
    </tr><tr><td rowspan="2"><code>myRe</code></td>
      <td><code>lastIndex</code></td>
      <td>The index at which to start the next match. (This property is set only if the regular expression uses the g option, described in <a href="#Advanced_Searching_With_Flags">Advanced Searching With Flags</a>.)</td>
      <td><code>5</code></td>
    </tr><tr><td><code>source</code></td>
      <td>The text of the pattern. Updated at the time that the regular expression is created, not executed.</td>
      <td><code>"d(b+)d"</code></td>
    </tr>
  &lt;/tbody&gt;
</table><p>As shown in the second form of this example, you can use a regular expression created with an object initializer without assigning it to a variable. If you do, however, every occurrence is a new regular expression. For this reason, if you use this form without assigning it to a variable, you cannot subsequently access the properties of that regular expression. For example, assume you have this script:</p>
<pre>
var myRe = /d(b+)d/g;
var myArray = myRe.exec("cdbbdbsbz");
console.log("The value of lastIndex is " + myRe.lastIndex);
</pre>
<p>This script displays:</p>
<pre>
The value of lastIndex is 5
</pre>
<p>However, if you have this script:</p>
<pre>
var myArray = /d(b+)d/g.exec("cdbbdbsbz");
console.log("The value of lastIndex is " + /d(b+)d/g.lastIndex);
</pre>
<p>It displays:</p>
<pre>
The value of lastIndex is 0
</pre>
<p>The occurrences of <code>/d(b+)d/g</code> in the two statements are different regular expression objects and hence have different values for their <code>lastIndex</code> property. If you need to access the properties of a regular expression created with an object initializer, you should first assign it to a variable.</p>
<h3 id="Using_Parenthesized_Substring_Matches">Using Parenthesized Substring Matches</h3>
<p>Including parentheses in a regular expression pattern causes the corresponding submatch to be remembered. For example, <code>/a(b)c/</code> matches the characters 'abc' and remembers 'b'. To recall these parenthesized substring matches, use the <code>Array</code> elements <code>[1]</code>, ..., <code>[n]</code>.</p>
<p>The number of possible parenthesized substrings is unlimited. The returned array holds all that were found. The following examples illustrate how to use parenthesized substring matches.</p>
<h4 id="Example_1">Example 1</h4>
<p>The following script uses the <code><a href="/w/index.php?title=concepts/programming/javascript/regex/js/objects/String/replace&amp;action=edit&amp;redlink=1" class="new">replace()</a></code> method to switch the words in the string. For the replacement text, the script uses the <code>$1</code> and <code>$2</code> in the replacement to denote the first and second parenthesized substring matches.</p>
<pre>
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
console.log(newstr);
</pre>
<p>This prints "Smith, John".</p>
<h3 id="Advanced_Searching_With_Flags">Advanced Searching With Flags</h3>
<p>Regular expressions have four optional flags that allow for global and case insensitive searching. To indicate a global search, use the <code>g</code> flag. To indicate a case-insensitive search, use the <code>i</code> flag. To indicate a multi-line search, use the <code>m</code> flag. To perform a "sticky" search, that matches starting at the current position in the target string, use the <code>y</code> flag. These flags can be used separately or together in any order, and are included as part of the regular expression.</p>
<p>To include a flag with the regular expression, use this syntax:</p>
<pre>
var re = /pattern/flags;
</pre>
<p>or</p>
<pre>
var re = new RegExp("pattern", "flags");
</pre>
<p>Note that the flags are an integral part of a regular expression. They cannot be added or removed later.</p>
<p>For example, <code>re = /\w+\s/g</code> creates a regular expression that looks for one or more characters followed by a space, and it looks for this combination throughout the string.</p>
<pre>
var re = /\w+\s/g;
var str = "fee fi fo fum";
var myArray = str.match(re);
console.log(myArray);
</pre>
<p>This displays ["fee ", "fi ", "fo "]. In this example, you could replace the line:</p>
<pre>
var re = /\w+\s/g;
</pre>
<p>with:</p>
<pre>
var re = new RegExp("\\w+\\s", "g");
</pre>
<p>and get the same result.</p>
<p>The <code>m</code> flag is used to specify that a multiline input string should be treated as multiple lines. If the <code>m</code> flag is used, <code>^</code> and <code>$</code> match at the start or end of any line within the input string instead of the start or end of the entire string.</p>
<h2 id="Examples">Examples</h2>
<p>The following examples show some uses of regular expressions.</p>
<h3 id="Changing_the_Order_in_an_Input_String">Changing the Order in an Input String</h3>
<p>The following example illustrates the formation of regular expressions and the use of <code>string.split()</code> and <code>string.replace()</code>. It cleans a roughly formatted input string containing names (first name first) separated by blanks, tabs and exactly one semicolon. Finally, it reverses the name order (last name first) and sorts the list.</p>
<p><br/></p>
<pre class="js">
// The name string contains multiple spaces and tabs,
// and may have multiple spaces between first and last names.
var names = "Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ; Chris Hand ";

var output = ["---------- Original String\n", names + "\n"];

// Prepare two regular expression patterns and array storage.
// Split the string into array elements.

// pattern: possible white space then semicolon then possible white space
var pattern = /\s*;\s*/;

// Break the string into pieces separated by the pattern above and
// store the pieces in an array called nameList
var nameList = names.split(pattern);

// new pattern: one or more characters then spaces then characters.
// Use parentheses to "memorize" portions of the pattern.
// The memorized portions are referred to later.
pattern = /(\w+)\s+(\w+)/;

// New array for holding names being processed.
var bySurnameList = [];

// Display the name array and populate the new array
// with comma-separated names, last first.
//
// The replace method removes anything matching the pattern
// and replaces it with the memorized string—second memorized portion
// followed by comma space followed by first memorized portion.
//
// The variables $1 and $2 refer to the portions
// memorized while matching the pattern.

output.push("---------- After Split by Regular Expression");

var i, len;
for (i = 0, len = nameList.length; i &amp;lt; len; i++){
  output.push(nameList[i]);
  bySurnameList[i] = nameList[i].replace(pattern, "$2, $1");
}

// Display the new array.
output.push("---------- Names Reversed");
for (i = 0, len = bySurnameList.length; i &amp;lt; len; i++){
  output.push(bySurnameList[i]);
}

// Sort by last name, then display the sorted array.
bySurnameList.sort();
output.push("---------- Sorted");
for (i = 0, len = bySurnameList.length; i &amp;lt; len; i++){
  output.push(bySurnameList[i]);
}

output.push("---------- End");

console.log(output.join("\n"));

</pre>
<h3 id="Using_Special_Characters_to_Verify_Input">Using Special Characters to Verify Input</h3>
<p>In the following example, the user is expected to enter a phone number. When the user presses the "Check" button, the script checks the validity of the number. If the number is valid (matches the character sequence specified by the regular expression), the script shows a message thanking the user and confirming the number. If the number is invalid, the script informs the user that the phone number is not valid at all.</p>
<p>The regular expression looks for zero or one open parenthesis <code>\(?</code>, followed by three digits<code> \d{3}</code>, followed by zero or one close parenthesis <code>\)?</code>, followed by one dash, forward slash, or decimal point and when found, remember the character <code>([-\/\.])</code>, followed by three digits <code>\d{3}</code>, followed by the remembered match of a dash, forward slash, or decimal point <code>\1</code>, followed by four digits <code>\d{4}</code>.</p>
<p>The <code>Change</code> event activated when the user presses Enter sets the value of <code>RegExp.input</code>.</p>
<pre>
&lt;!DOCTYPE html&gt;
&lt;html&gt;  
  &lt;head&gt;  
    &lt;meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1"&gt;  
    &lt;meta http-equiv="Content-Script-Type" content="text/javascript"&gt;  
    &lt;script type="text/javascript"&gt;  
      var re = /\(?\d{3}\)?([-\/\.])\d{3}\1\d{4}/;  
      function testInfo(phoneInput){  
        var OK = re.exec(phoneInput.value);  
        if (!OK)  
          window.alert(RegExp.input + " isn't a phone number with area code!");  
        else
          window.alert("Thanks, your phone number is " + OK[0]);  
      }  
    &lt;/script&gt;  
  &lt;/head&gt;  
  &lt;body&gt;  
    &lt;p&gt;Enter your phone number (with area code) and then click "Check".
        &lt;br&gt;The expected format is like ###-###-####.&lt;/p&gt;
    &lt;form action="#"&gt;  
      &lt;input id="phone"&gt;&lt;button onclick="testInfo(document.getElementById('phone'));"&gt;Check&lt;/button&gt;
    &lt;/form&gt;  
  &lt;/body&gt;  
&lt;/html&gt;
</pre>
