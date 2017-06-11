# AngularJS Research

## Table of Contents

* [Analysis](#analysis)
    1. [Performance](#performance)
    2. [Browser compatibility](#browser-compatibility)
    3. [Mobile compatibility](#mobile-compatibility)
    5. [ECMAScript 6](#ecmascript-6)
    7. [Web components](#web-components)
    8. [Security](#security)
    9. [Learning curve](#learning-curve)
    9. [Knowledge needed](#knowledge-needed)
    10. [Stability](#stability)
    14. [Latest version](#latest-version)
    12. [Modules and libraries](#modules-and-libraries)
    11. [Development speed](#development-speed)
    13. [Community](#community)
    15. [Scalability](#scalability)
    16. [Important Projects](#important-projects)
    16. [AngularJS + Require](#angularjs-require) 
    17. [Time on the market](#time-on-the-market)
    18. [SEO friendly](#seo-friendly)
* [Strenghs and Weaknesses](#strenghs-and-weaknesses) 
* [Conclusion](#conclusion)
* [Table](#table)
* [Resources](#resources)


# Analysis

## Performance
AngularJS has serious problems with watchers and his digest cycle when it grows without control. AngularJS check in each digest cycle everything is been watching and this task can be a serious performance problem if we don't take care something like:
[11 tips to improve angularjs](https://www.alexkras.com/11-tips-to-improve-angularjs-performance/)
 * Minimize/Avoid Watchers
 * Avoid ng-repeat. If you have to use ng-repeat use infinite scrolling or pagination
 * Use Bind once when possible
 * Use $watchCollection instead of $watch (with a 3rd parameter)
 * Avoid repeated filters and cache data whenever possible
 * Use ng-if instead of ng-show (but confirm that ng-if is actually better for your use case)
 * Use console.time to benchmark your functions
 * Use native Javascript or Lodash for slow functions
 * Use Batarang to benchmark your watchers
 * Use Chrome Timeline and Profiler to identify performance bottlenecks

http://www.slideshare.net/nirkaufman/angularjs-performance-production-tips

### **ng-style** faster than ng-class
 * [testing ng-style](http://ansukla.github.io/ng-perf/demo-app/index.html#/ng-style)
 * [testing ng-class](http://ansukla.github.io/ng-perf/demo-app/index.html#/ng-class)

## Browser compatibility
| Internet explorer | Safari | Chrome | Firefox | Opera |
|---|---|---|---|---|
| ie9+ | 5+ | 30+ | 4+ | 11+ |

Please check out this official link if you plan to use angularJS on IE:
[https://docs.angularjs.org/guide/ie](https://docs.angularjs.org/guide/ie)> Internet Explorer 8 has issues with angularjs. Since version 1.3, AngularJS doesn't support ie8. We recommend use minimum ie9.

> Check browser compatibility of your project here: [https://www.browserstack.com/](https://www.browserstack.com/)

[source](https://en.wikipedia.org/wiki/Comparison_of_JavaScript_frameworks)

## Mobile compatibility
* mobile browsers (Android, Chrome mobile, ios safari, windows phone ie)

The JavaScript components complement **Apache Cordova**, the framework used for developing cross-platform mobile apps. It aims to simplify both the development and the testing of such applications by providing a framework for client-side model–view–controller (MVC) and model–view–viewmodel (MVVM) architectures, along with components commonly used in rich Internet applications.

https://en.wikipedia.org/wiki/AngularJS
## ECMAScript 6
* Pros
    * ES5:
        * You have a lot of browser support.
        * AngularJS documentation and all his examples are built in ES5.
    * ES6:
        * You have tail call optimization.
        * You have import statements.
        * Lamba's are pretty chill.
        * Immutable and block scoping objects with "const" and "let".
        * Classes and OO inheritence.
        * Functors, and all that functional goodness.
        * String templates that handle interpolation for you.
* Cons
    * ES5:
        * It doesn't have everything that ES6 has.
    * ES6:
        * It doesn't have all the support that ES5 has, but you can always transpile your ES6 code.

> We recommend use ES5 for AngularJS proyects because all the documentation are written in ES5.   

## Web components
Integrating Web Components with the Angular of today doesn't really work. It is simply not designed to work with Web Components technologies out of the box. Even if there are ways to make it sort of work, it'll always be a hack to rely on things like Mutation Observers, especially when keeping in mind that this work-around only works when the element reflects its changes back to its attributes. Also, creating directives for every single event that a custom element could fire, isn't really a comfortable option.

However, we shouldn't forget that this only applies to web components that need to notify the outside world. Components that just need data from the outside world, can be used right away along with Angular without any further hacks.

> AngularJS gives us the ability to build our application oriented to components, but these components only have life within AngularJS and do not follow the standard. 

## Security
AngularJS adverts about his best practices for secure your application. Following this tips: 
 * Use the latest AngularJS possible
 * If an attacker has access to control Angular templates or expressions, they can exploit an Angular application via an XSS attack, regardless of the version.
    * Generating Angular templates on the server containing user-provided content. This is the most common pitfall where you are generating HTML via some server-side engine such as PHP, Java or ASP.NET.
    * Passing an expression generated from user-provided content in calls to the following methods on a scope
        * $watch(userContent, ...)
        * $watchGroup(userContent, ...)
        * $watchCollection(userContent, ...)
        * $eval(userContent)
        * $evalAsync(userContent)
        * $apply(userContent)
        * $applyAsync(userContent)
    * Passing an expression generated from user-provided content in calls to services that parse expressions
        * $compile(userContent)
        * $parse(userContent)
        * $interpolate(userContent)
    * Passing an expression generated from user provided content as a predicate to orderBy pipe
        * {{ value | orderBy : userContent }}
    * Do not mix client and server templates
    * Do not use user input to generate templates dynamically
    * Do not run user input through $scope.$eval (or any of the other expression parsing functions listed above)
    * Consider using CSP (but don't rely only on CSP)
 * HTTP Requests: Whenever your application makes requests to a server there are potential security issues that need to be blocked. Both server and the client must cooperate in order to eliminate these threats. Angular comes pre-configured with strategies that address these issues, but for this to work backend server cooperation is required.
 * Cross Site Request Forgery (XSRF/CSRF) : Protection from XSRF is provided by using the double-submit cookie defense pattern. For more information please visit XSRF protection.
 * JSON Hijacking Protection : Protection from JSON Hijacking is provided if the server prefixes all JSON requests with following string ")]}',\n". Angular will automatically strip the prefix before processing it as JSON. For more information please visit JSON Hijacking Protection.
 * Strict Contextual Escaping : Strict Contextual Escaping (SCE) is a mode in which AngularJS requires bindings in certain contexts to require a value that is marked as safe to use for that context.
    This mode is implemented by the $sce service and various core directives.
    * Be aware that marking untrusted data as safe via calls to $sce.trustAsHtml, etc is dangerous and will lead to Cross Site Scripting exploits. 
 * Using Local Caches :
    * There are various places that the browser can store (or cache) data. Within Angular there are objects created by the $cacheFactory. These objects, such as $templateCache are used to store and retrieve data, primarily used by $http and the script directive to cache templates and other data.
    * Similarly the browser itself offers localStorage and sessionStorage objects for caching data.
    * Attackers with local access can retrieve sensitive data from this cache even when users are not authenticated.
    * For instance in a long running Single Page Application (SPA), one user may "log out", but then another user may access the application without refreshing, in which case all the cached data is still available.

Source: https://docs.angularjs.org/guide/security
## Learning curve
Commonly Known as a steep learning curve. AngularJS require adaptation framework, to know what the life cycle of its implementation and as the stages of compilation and rendering AngularJS work.

## Knowledge needed
 * Javascript ECMAScript 5
 * API REST
 * Pattern designs
 * AngularJS components

## Stability
Currently AngularJS has the version 1.5.8 and with the arrival of Angular 2, Google has ensured that both versions will be maintained in parallel and so far has not been said that AngularJS is going to deprecate, but you have to consider his migration to Angular 2.

## Latest version
* Latest version 1.5.8
https://github.com/angular/angular.js/blob/master/CHANGELOG.md

## Community
 * Mainly maintained by Google
 * Angular community on Google+ (+80k members)
    https://plus.google.com/communities/115368820700870330756
 * Stackoverflow

There is a lot of documentation on the internet on any subject in AngularJS. It is easy to find answers and code examples.

## Modules and libraries
 * Angular modules (+2k modules created)
    http://ngmodules.org/

## Development speed
AngularJS is a complete framework with which we can start developing our application from the first time without worrying about the project structure, routing, etc.
To this end, we propose Angle Angle Basic kit for component-oriented starter 1.5, which gives a starting point for your project following the best practices. 

 * Choosing javascript mvc framework http://www.funnyant.com/choosing-javascript-mvc-framework/
 * AngularJS vs Backbone vs Ember https://medium.com/@alexbardas/improving-the-productivity-and-focus-with-angularjs-33d8c0ac11f1#.inl4uxz38
 
## Scalability
AngularJS can work in parallel with its components and feature oriented programming.

## Important Projects
* Youtube for ps3
* Vevo
* Soundnode: Soundcloud for Desktop
* Tools for Education

## AngularJS + Require
AngularJS is an SPA (single-page application) framework, which means that all our application AngularJS load in the initial charge, this can be ideal in certain cases of use and small applications. But in very large applications can be very time consuming, and there are solutions like AngularJS + Require that allow our application to load asynchronously, using only the modules you need. But be careful, because it can be costly if our application is really small.

## Time on the market
* Release date: October 20, 2010; 5 years ago

## SEO Friendly
Angular, as  a single page application framework doesn't work well with content crawlers and search engines such as Google or Bing. In order to make it work, a secondary tool like prerender.io becomes necessary to optimize the web SEO

# Strenghs and Weaknesses

## Strenghs
* Powerful and complete framework
* Mainly maintained by Google
* Common framework used in our days, a great active community.
* There is a lot of libraries and documentation.

## Weakness
* Performance very slow on big and complex applications if isn't controlled correctly. 
* Steep learning curve.
* Doesn't use web components instead of it use AngularJS components. R
* Reuse components only works on AngularJS applications.

# Conclusion
AngularJS is a stable and powerful framework to built medium and scalable applications. Commonly used for Management applications, education, etc. Easily maintainable.

# Table

| low |  | medium |   | High |
|---|---|---|---|---|---|---|---|---|
| ![](assets/images/1.png) | ![](assets/images/2.png)  | ![](assets/images/3.png) | ![](assets/images/4.png) |  ![](assets/images/5.png)    | ![](assets/images/6.png) |

| Category | Score |
|----------|-------|
| Community | ![](assets/images/5.png) |
| Learning curve | ![](assets/images/3.png) |
| Performance | ![](assets/images/3.png) |
| Browser Compatibility | ![](assets/images/3.png) |
| Mobile Compatibility | ![](assets/images/3.png) |
| ES5 | ![](assets/images/5.png) |
| ES6 | ![](assets/images/3.png) |
| Web components | ![](assets/images/1.png) |
| Reuse components | ![](assets/images/4.png) |
| Security | ![](assets/images/4.png) |
| Time on market | ![](assets/images/4.png) |
| Scalability | ![](assets/images/4.png) |
| Knowledge needed | ![](assets/images/4.png) |
| Development speed | ![](assets/images/5.png) |
| Modules and libraries | ![](assets/images/5.png) |
| Stability | ![](assets/images/5.png) |
| SEO | ![](assets/images/2.png) |


## Qualification

| **AngularJS 1.5+** | Qualification | ![](assets/images/4.png) |
|----|------|-----|

> This research has been documented by the resources mentioned above on this document and the FrontStack team can't make test to verify the fully complexity of AngularJS and it is based on our own experience.

# Resources
[Modules for angularjs](http://ngmodules.org/)