# Frontend generic vulnerabilities

## Client XSS
On the front end, a Cross-Site Scripting vulnerability happens when dynamic data is sent to a user without being validated for malicious content. In the case of tweet deck, the dynamic data was the tweet, and the malicious content was the executable JavaScript code being tweeted.

Most often, XSS vulnerabilities occur when websites or applications don’t remove executable code from input fields that their users have access to. For example, a web developer working on a photo sharing application must ensure that only images can be uploaded in the required fields, and that those image fields will remove broken links, incorrect file extensions, and malicious code.

How do you protect against XSS? Start by using frameworks and services that have built in protection against these kinds of attacks. Learn more about protecting against XSS

[https://www.owasp.org/index.php/Special:Search/Cross-site_Scripting_(XSS](https://www.owasp.org/index.php/Special:Search/Cross-site_Scripting_(XSS)

## Iframes

Iframes have been around for quite some time, and have several different use cases. They can also cause a lot of trouble. It’s important to remember that displaying content inside of an Iframe means you’re trusting that content not to be vulnerable or malicious. Iframes and XSS attacks usually go hand in hand, meaning that malicious content inside of an Iframe can go on to effect your users. If the content inside of the Iframe is coming from your domain, its important to make sure that the Iframed content is secure and not vulnerable to an attack.

Luckily theres a great way to protect against these vulnerabilities using the sandbox attribute.

[http://www.html5rocks.com/en/tutorials/security/sandboxed-iframes/](http://www.html5rocks.com/en/tutorials/security/sandboxed-iframes/)

## CORS

If you’ve ever wanted to share resources across subdomains, you’ve most likely had to deal with Cross-Origin resource sharing. When CORS is used irresponsibly, it can allow anyone to send a request to your server, potentially revealing sensitive information in the response. If you’ve ever set Access-Control-Allow-Origin to *, its worth making sure that you haven’t compromised your site.

[https://code.google.com/archive/p/html5security/wikis/CrossOriginRequestSecurity.wiki](https://code.google.com/archive/p/html5security/wikis/CrossOriginRequestSecurity.wiki) 

## Cookies

Libraries like jQuery Cookie make it very easy to set cookies without having to rely on a server. When working with cookies, it is important to remember that they can be vulnerable to XSS and CORS exploits. Their also not encrypted by default, which means a password stored in a cookie over http will be stored in plain text. Be sure to check out this tutorial by Treehouse which provides a list of ways to make your cookies more secure.

[http://blog.teamtreehouse.com/how-to-create-totally-secure-cookies](http://blog.teamtreehouse.com/how-to-create-totally-secure-cookies)

## Front End Security and HTML5

HTML5 elements and API’s have been known to contain security vulnerabilities every so often. Although browsers are quick to implement fixes, it’s always a good idea to keep this in mind when working with sensitive content. html5sec.org provides an overview of vulnerabilities in HTML5 elements, along with the browser versions that are vulnerable to them.

[https://html5sec.org/](https://html5sec.org/)

<hr>

# Top Ten Web Application Risks


* 1. Injection **
* 2. Broken Authentication and Session Management ***
* 3. Cross-site Scripting (XSS) ***
* 4. Insecure Direct Object References **
* 5. Security Misconfiguration **
* 6. Sensitive Data Exposure *****
* 7. Missing Function Level Access Control ***** 
* 8. Cross-Site Request Forgery (CSRF) *
* 9. Using Components with Known Vulnerabilities ****
* 10. Unvalidated Redirect and Forwards ***

> \***** More critical <br>
\**** <br>
\*** <br>
\** <br>
\* less critical


<hr>

# Common frontend attacks
 1. URL Misinterpretation
 2. Directory Browsing
 3. Retrieving "non-web" Files
 4. Reverse Proxying
 5. Java Decompilation
 6. Source Code Disclosure
 7. Input Validation
 8. SQL Query Poisoning
 9. Session Hijacking
 10. Buffer Overflows
 

# AngularJS vulnerabilities
Like any other technology, AngularJs is not impervious to attack. Angular does, however, provide buit-in protection from basic security holes including cross-site scription and HTML injection attacks. Angular JS does round-trip escaping on all strings for you and even offers XSRF protection for server-side communication.

[http://www.slideshare.net/kevinhakanson/ng-owasp-ndc](http://www.slideshare.net/kevinhakanson/ng-owasp-ndc)

OWASP Top 10 for AngularJS Applications: [https://github.com/hakanson/ng-owasp](https://github.com/hakanson/ng-owasp)

## 1. Injection
* $sanitize ngSanitize module provides functionality to sanitize HTML.
    ```js
    <script src="angular-sanitize.js"></script>

    angular.module('app', ['ngSanitize']);
    ```
* $sce is a service that provides Strict Contextual Escaping (SCE) services to AngularJS.

    * Checkout the example 1
    * Expression Sandboxing
    Design your application in such a way that users cannot change client-side templates.
    * Do not mix client and server templates
    * Do not use user input to generate templates dynamically
    * Do no run user input through $scope.$eval
* $interpolate service is used by the HTML $compile service for data binding
* angular-translate
    * $translateProvides.useSanitizeValueStrategy() ->
        * **sanitize** (sanitize HTML in the translation text using $sanitize)
        * **escape** (escapes HTML in the translation)
        * **sanitizeParameters** (sanitizes HTML in the value of the interpolation parameters using $sanitize)
        * **escapeParameters** (escapes HTML in the values of the interpolation parameters)
        * example
        ```js
        $translateProvider.translations('en', {
            GREETING: '<b>hello</b> {{name}}',
            GREETINGGX: '<b>hello</b> {{name | uppercase}}'
        });
        $translateProvider.useSanitizeValueStrategy('sanitize');
        ```
> Be aware that marking untrusted data as safe via calls to $sce.trustAsHtml, etc is dangerous and will lead to Cross Site Scripting exploits.
## 2. Broken Authentication and Session Management
* Use interceptors to indentify the user login status and react depending of api respond status.
* Clear user data when api logout the user.

## 3. Cross-site Scription(XSS)
Cross-Site-Scripting means that attacker can insert custim js code which is then displayed in the user browser.

3 Types:
* <b>stored</b> * (input js in a field -> DB -> sent back to the page)
* <b>reflected</b> *** (input js in the url, send the url to a user, js executed)
* <b>DOM-based</b> ***** (input triggers js logic that manipulates the DOM and insert custom js)
> Remember: any external input is UNTRUSTED!
We must avoid mixing user input with js code

Preventing:
* Since AngularJS 1.3, the HTML compiler will escape all {{}} & ng-bind by default.
* Use $sceProvider & $SanitizeProvider

* Content Security Policy is an added layer of security that helps to detect and mitigate certain types of attacks, including XSS and data injection attacks.
* CSP compability [http://caniuse.com/#feat=contentsecuritypolicy](http://caniuse.com/#feat=contentsecuritypolicy)
* ngCsp is a angular module enables CSP support. When this mode is on AngularJS will evaluate all expressions up to 30% slower that in non-CSP mode, but no security violations will be raised.
```html
<!doctype html>
<html ng-app ng-csp>
...
...
</html> 
```
* W3C Subresource Integrity. A validation scheme, extending several HTML elements with an integrity attribute that contains a cryptographic hash of the representation of the resource
```html
<script src="alert.js"
    integrity="sha256-quigoirbgosdnfdsklfjsdklfhjurf/Tng="
    crossorigin="anonymous"></script> 
``` 
> this will prevent somethings like :
```js
document.body.appendChild(document.createElement("script"))
.appendChild(document.createTextNode("alert('xss')"))
```

## 4. Sensitive Data Exposure
* ngStore module contains services that provide access to local "disk" storage provided by native browser APIs like localStorage, sessionStorage and IndexedDB. All services within the ngStore module will support encryption, managed through the $localDB service.
* angular-cache a very useful replacement for Angular's $cacheFactory. The storage mode for a cache can be "memory", "localStorage", "sessionStorage" or a custom implementation.

When is storage cleared?
* variable / memory - when page closes
* session cookie - when browser closes
* sessionStorage - when browser closes
* persistent cookie - when expires
* localStorage - when explicity cleared
* indexedDB - when explicity cleared

> Attackers with local access can retrieve sensitive data from this cache even when users are not authenticated.
For instance in a long running Single Page Application (SPA), one user may "log out", but then another user may access the application without refreshing, in which case all the cached data is still available. Remember clear all sensible data after logout.
[https://www.whitehatsec.com/blog/web-storage-security/](https://www.whitehatsec.com/blog/web-storage-security/)

## 5. Tokens and interceptors
* Pass authentication token on every HTTP request (interceptors & $resource) 
* JWT in angular [http://github.com/auth0/angular-jwt](http://github.com/auth0/angular-jwt) Storing and retrieving tokens on the client 

Managing tokens
```js
$http(...).then(function(response) {
    currentToken.jwt = response.data.access_token;
})

tokenPayload = jwtHelper.decodeToken(jwt);
date = jwtHelper.getTokenExpirationDate(jwt);
bool = jwtHelper.isTokenExpired(jwt);
```

### Sending Tokens
* Cookies
    *Pros
        * sent automatically
        * no code required on the client
    *Cons
        * sent automatically
        * even when do not wanted
        * less control on validity
        * stored on client disk
* Headers
    *Pros
        * sent only explicitely
        * not stored on disk
        * unless you want to
        * more control
        * also prevents CSRF
    *Cons
        * require code on the client side
        * but this is normal in SPAs

### Storing tokens

In memory or sessionStorage:
    * works only on current tab
    * automatically closed

In localStorage:
    * persistent
    * work across multiple tabs
    * requires explicit expiration

[http://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage](http://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage)

### Routing support for auth:
* Redirect to login if not authenticated
* redirect to login if token expired
* optionally, redirect back to original URL
* redirect to error page if route not authorized in the current profile
* Use uiRoute instead of ngRoute, more capabilities.







## 6. Using components with known Vulnerabilities
Components, such as libraries, frameworks, and other software modules, almost always run with full privileges. If a vulnerable component is exploited, such an attack can facilitate serious data loss or server takeover. Applications using components with known vulnerabilities may undermine application defenses and enable a range of possible attacks and impacts.

* retire.js 

Retire.js has these parts:

* A command line scanner
* A grunt plugin
* A Chrome extension
* A Firefox extension
* Burp and OWASP Zap plugin

## 7. Use the latest AngularJS possible
Like any software library, it is critical to keep AngularJS up to date. Please track the CHANGELOG and make sure you are aware of upcoming security patches and other updates.

## 8. Security misconfiguration
* Man in the middle. HTTPS EVERYWHERE 
* Be careful with CORS. Avoid Allow-Origin "*" unless have very strong authentication and authorization.
* Remember to tell the browser to enable stronger protection. https://www.owasp.org/index.php/List_of_useful_HTTP_headers


## 9. JSON Hijacking Protection
Protection from JSON Hijacking is provided if the server prefixes all JSON requests with following string ")]}',\n". Angular will automatically strip the prefix before processing it as JSON. For more information please visit 
[JSON Hijacking Protection](https://docs.angularjs.org/api/ng/service/$http#json-vulnerability-protection)

Bear in mind that calling $http.jsonp, like in our Yahoo! finance example, gives the remote server (and, if the request is not secured, any Man-in-the-Middle attackers) instant remote code execution in your application: the result of these requests is handed off to the browser as regular tag.

# Interest links
[https://www.owasp.org/index.php/Main_Page](https://www.owasp.org/index.php/Main_Page)
[OWSAP Secure Coding Principles](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-66-1024.jpg?cb=1445499026)
[OWASP Testing Guide](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-66-1024.jpg?cb=1445499026)
[SOLID Desing Principles](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-66-1024.jpg?cb=1445499026)
[Attack Vectors & Vulnerabilities](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-67-1024.jpg?cb=1445499026)
[OWASP Guidelines](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-67-1024.jpg?cb=1445499026)
[JS Frameworks Security](http://image.slidesharecdn.com/cloudconf-2015-bonamico-angular-security-full-151022072800-lva1-app6892/95/angularjs-security-defend-your-single-page-application-67-1024.jpg?cb=1445499026)
[Slides Carlo Bonamico](http://es.slideshare.net/carlo.bonamico/angularjs-security-defend-your-single-page-application)