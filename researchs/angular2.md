# Angular2 Research

This purpose of this article is analyze the Strengths and Weaknesses of Angular2 to compare it with other frameworks. 

# Table of Contents

* [Analysis](#Analysis)
    1. [Performance](#Performance)
    2. [Browser compatibility](#browser-compatibility)
    3. [Mobile compatibility](#mobile-compatibility)
    4. [Hybrid application](#hybrid-application)
    5. [ES5, ES6 & TypeScript](#es5-es6-typescript)
    7. [Web components](#web-components)
    8. [Security](#security)
    9. [Learning curve](#learning-curve)
    9. [Knowledge needed](#knowledge-needed)
    10. [Stability](#stability)
    11. [Development speed](#development-speed)
    12. [Modules and libraries](#modules-and-libraries)
    13. [Community](#community)
    14. [Latest version](#latest-version)
    15. [Scalability](#scalability)
    16. [Important Projects](#important-projects) 
    17. [Time on the market](#time-on-the-market)
    18. [SEO friendly](#seo-friendly)
* [Strengths and Weaknesses](#strengths-and-weaknesses) 
* [Conclusion](#conclusion)
* [Table](#table)
* [Sources](#sources)

# Analysis

## Performance

Angular2 has significantly improved the performance in contrast with its previous version AngularJS. 
The most important improvements consist of:
* Angular 2 uses the [zones mechanism](http://blog.thoughtram.io/angular/2016/01/22/understanding-zones.html) to make a lot of the reasoning about the digest cycle no longer necessary. 
* [Angular2 change detection](https://vsavkin.com/change-detection-in-angular-2-4f216b855d4c#.l2ofq125y) allows Angular 2 to detect precisely when the model has changed. The performance can be improved drastically with the new onPush change detection strategy, which specify that only the defined input properties start the update cycle.
* [Angular 2 preload strategy](https://vsavkin.com/angular-router-preloading-modules-ba3c75e424cb#.oaws8z3wr) allows Angular 2 to preload lazyLoaded modules meanwhile the app is active in order to improve the user experience. 
* Faster checking of a single binding
* Avoid scanning parts of the component tree
* Lazy Loading but not out of the box
* Pure vs Impure Pipes

The following list of practices will help to boost the performance of an Angular 2 applications base on [Minko Gechev research](https://github.com/mgechev/angular-performance-checklist):
 * Bundling
 * Minification and dead code elimination
 * Tree-shaking
 * Ahead-of-Time (AoT) Compilation
 * Compression
 * Server-side rendering
 * Caching and [use of Service Workers](https://github.com/angular/mobile-toolkit)

 For more info [https://github.com/mgechev/angular-performance-checklist](https://github.com/mgechev/angular-performance-checklist)
 
## Browser compatibility

Angular supports most recent browsers. This includes the following specific versions:

| Internet explorer | Safari | Chrome | Firefox | Edge |
|---|---|---|---|---|
| ie9+ | 7+ | Latest | Latest | 7 | Jelly Bean(4.1) | 11 | 13 | 

Original Source at [https://angular.io/docs/ts/latest/guide/browser-support.html](https://angular.io/docs/ts/latest/guide/browser-support.html)

### Mandatory polyfills

* These are the polyfills required to run an Angular application on each supported browser:

| Browsers (desktop & mobile) | Polyfills required |
|---|---|
| Chrome, Firefox, Edge, Safari 9+ | None |
| Safari 7 & 8, IE10 & 11, Android 4.1+ | [ES6](https://angular.io/docs/ts/latest/guide/browser-support.html#!#core-es6) |
| IE9 | [ES6 classList](https://angular.io/docs/ts/latest/guide/browser-support.html#!#classlist) |

More information about optional browser features and suggested polyfills in the next [Link](https://angular.io/docs/ts/latest/guide/browser-support.html)  

> To Check browser compatibility of your project here: [https://www.browserstack.com/](https://www.browserstack.com/)

## Mobile compatibility

Angular runs in most recent mobile browsers. This includes the following specific versions:

| iOS | Android | IE mobile |
|---|---|---|
| 7 | Jelly Bean (4.1) | 11 |

Original Source at [https://angular.io/docs/ts/latest/guide/browser-support.html](https://angular.io/docs/ts/latest/guide/browser-support.html)

## Hybrid application

There are several alternatives to develop Hybrid application with Angular2: Cordova, Ionic 2 & NativeScript.
All of them are open source frameworks, to build Mobile app with HTML, CSS & JS, that target multiple platforms with one code base in Javascript.

* [Cordova](https://cordova.apache.org/) 
    * Applications execute within wrappers targeted to all the platform relying on WebView to provide the user interface. 
    * Allow the access to native device APIs from the web view.
    * Plugins are an integral part of the cordova huge ecosystem.
    * Documentation [https://cordova.apache.org/docs/en/latest/](https://cordova.apache.org/docs/en/latest/)

* [Ionic 2](http://ionicframework.com/)
    * Set of Angular2 modules and components, optimized to provide a good mobile performance and improve de user experience.
    * Ionic2 CLI extend Cordova functionalities with more mobile features.  
    * Prototype Ionic app creator.
    * Market of components. [http://market.ionic.io/](http://market.ionic.io/)
    * Still in Beta.
    * Documentation [http://ionicframework.com/docs/v2/](http://ionicframework.com/docs/v2/)

* [NativeScript](https://www.nativescript.org/)
    * Generate native mobile apps with Angular, TypeScript or JavaScript.
    * Without WebView providing a better user experience and performance.
    * Supported by Telerik.
    * iOS, Android and (soon) Windows. 
    * Documentation [https://docs.nativescript.org/](https://docs.nativescript.org/)
    * More info [https://www.nativescript.org/nativescript-is-how-you-build-native-mobile-apps-with-angular](https://www.nativescript.org/nativescript-is-how-you-build-native-mobile-apps-with-angular)

## ES5, ES6 & TypeScript 

* Pros
    * ES5:
        * You have most browser support.
        * AngularJS documentation and all his examples are built in ES5.
    * ES6:
        * You have tail call optimization.
        * You have import statements.
        * Lamba's are pretty chill.
        * Immutable and block scoping objects with "const" and "let".
        * Classes and OO inheritence.
        * Functors, and all that functional goodness.
        * String templates that handle interpolation for you.
    * TypeScript:
        * Typed language.
        * Most of ES6 functionalities without the need of polyfills.
        * Support to powerful context assistant

* Cons
    * ES5:
        * It doesn't have everything that ES6 has.
    * ES6:
        * It doesn't have all the support that ES5 has, but you can always transpile your ES6 code.
    *TypeScript:
        * Need to be transpiled into ES6 or ES5
        * Proprietary Language

> It is recommended the use of TypeScript with Angular2 projects because big part of the official documentation, examples and the framework itself is written in TypeScript.   

## Web components

Angular2 component directives emulate Web Components behavior and it will be able to work with standard Web Components.

Like HTML5 spec web components, Angular 2 components have an extremely well defined life-cycle. As a result of this we can specify when different callback functions happen depending upon the state of a component.

Angular2 component [style](https://angular.io/docs/ts/latest/guide/component-styles.html) definition is powerful because the framework provides special selectors, component style loaders and different methods of style encapsulations.
It encapsulates the style inside the component avoiding css conflicts. There are three ways of encapsulation    
* Native, attaching native Shadow Dom to the component.
* Emulated, emulates Shadow Dom behaviour preprocessing the CSS.
* None, without encapsulation. Angular adds the styles to global styles.

Despite of the fact that the Angular components are based on the Web Components standard, can´t be used outside of an Angular environment, making the components less reusable than other libraries like Polymer.

## Security 

Angular2 comes with built-in protections against common web application vulnerabilities and attacks such as cross-site scripting attacks. It does not cover application-level security, such as authentication or authorization.

 * Sanitization and security contexts
    * Sanitization is the inspection of an untrusted value, turning it into a value that is safe to insert into the DOM.
    * Angular sanitizes untrusted values for HTML, Style and URL, but It is not possible to sanitizing URL that will be loaded and executed as code, like scripts.

 * Cross-site scripting (XSS) 
    * To systematically block XSS bugs, Angular treats all values as untrusted by default. When a value is inserted into the DOM from a template, via property, attribute, style, class binding, or interpolation, Angular sanitizes and escapes untrusted values.
    * Applications must prevent values that an attacker can control from ever making it into the source code of a template.  

 * Trusting safe values
    * Angular automatically sanitizes the URL, disables the dangerous code, and in development mode, logs this action to the console.

 * HTTP-level vulnerabilities
    * Cross-site request forgery: The Application must ensure that user requests originate in your own application with CSRF Token, Cookie strategy, etc.
    * Cross-site script inclusion (XSSI): The attack works overriding native JavaScript object constructors. Angular's Http library recognizes this convention and automatically strips the string.  

In addition to all the previous remarks, the following set of Best practices will help to improve the App security:  
 * Keep current with the latest Angular library releases.
 * Don't modify your copy of Angular.
 * Avoid Angular APIs marked in the documentation as [“Security Risk.”](https://angular.io/docs/ts/latest/guide/security.html#!#bypass-security-apis)

More Information in [https://angular.io/docs/ts/latest/guide/security.html](https://angular.io/docs/ts/latest/guide/security.html)

Auditing angular applications:
 * Angular applications must follow the same security principles as regular web applications, and must be audited as such. Angular-specific APIs that should be audited in a security review, such as the bypassSecurityTrust methods, are marked in the documentation as security sensitive.

## Learning curve 

Angular 2’s learning curve is much steeper that other similar frameworks. It is a very opinionated franework which simplify significantly the development but complicate the learning process with their own conventions. 
Even without TypeScript, their [Quickstart guide](https://angular.io/docs/js/latest/quickstart.html) starts out with an app that uses ES2015 JavaScript, NPM with 18 dependencies, etc.

Angular provides an Angular module called [UpgradeAdapter](https://angular.io/docs/ts/latest/guide/upgrade.html#!#upgrading-with-the-upgrade-adapter) in order to support progressive upgrade to Angular 2. Thanks to this module, Angular 2 components can be used in Angular 1 applications even using Angular 1 directives in Angular 2 components' templates.

## Knowledge needed

 * TypeScript and Transpile process  
 * Angular2 opinionated syntax, strict and verbose
 * bundling strategies
 * Designs pattern such us Observers and Componentization 
 * Zones

## Stability 
 * Angular2 has been recently released in September 15th, 2016.
 * In contrast with other framework, the stability of Angular2 is ensured by a dedicated Google team.

## Latest version
* [Latest version 2.1.0](https://github.com/angular/angular/releases)

Link to the changeLog [https://github.com/angular/angular/blob/master/CHANGELOG.md](https://github.com/angular/angular/blob/master/CHANGELOG.md)

## Community 
 * Mainly maintained by Google 
 * Angular community Size in numbers
    * Github Stars 17K
    * Github Forks 4,5K 
    * Github Contributors 342
    * Stackoverflow questions 21K
    * Stackoverflow followers 7,7K
 * One month since its official release, the angular2 community has grown significantly and has been very active foretelling the creation of a powerful community. 

## Modules and libraries 

 * NPM Angular modules (+2,5k modules created with Angular2 and ng2 references)
    * Source [https://www.npmjs.com/](https://www.npmjs.com/)

## Development speed  

Angular 2 is a Strict and Verbose framework that may need additional code but it guarantees consistency in the development.

TypeScript is a typed oriented language and provide to angular2 apps a powerful syntax to simplify the development decision process.
TypeScript support the integration with major context assistant to increase the productivity.

In other hand, Angular team has developed Angular CLI to simplify and speed up the development process with a powerful CLI that help to setup a project with a robust scaffold, creation of new component, testing, build, etc.

## Scalability 

Angular2 was specially conceived to work component oriented, allowing distributed teams to work at the same time in the same project concurrently.  
Due to Angular bundle nature, it is important to follow a scalable project structure and a build strategy for good first load timing, lazy loading and a good application performance. 

## Important Projects 
* YouTube App
* SoundCloud App
* GitHub profile search
    * For more info [http://builtwithangular2.com/](http://builtwithangular2.com/)

## Time on the market 
* Release date: September 15, 2016.

## SEO friendly

As a single page application framework, Angular 2 finds the same difficulties of other similiar technologies optimizing SEO. 
Angular 2 resolve those problems with [Angular Universal](https://github.com/angular/universal). This module adds Universal (isomorphic) JavaScript support for Angular 2. This means that the HTML can be rendered on server, in order to presents static content to the user in the shortest possible time. Because of this statics assets, Angular applications improves the app´s engagement and becomes SEO friendly.
Because of the Server-side rendering, Angular Universal makes necessary the content to be handled by a node server or similar.

# Strengths and Weaknesses 

## Strengths
* TypeScript: Typed data oriented syntax
* Powerful productivity tool
* Complete framework that contains everything needed to build apps
* Dependency Injection
* Server-side rendering
* Mainly maintained by Google
* Reusable components oriented Framework

## Weakness
* TypeScript: Proprietary language
* Steep learning curve. TypeScript and an opinionated syntax
* Difficult to integrate with other frameworks
* Slow and heavy as compared to native Web Components
* Limited Angular2 web components reutilization
* The documentation and modules are limited, but increasing considerably lately
* Complex bundling system in big projects

# Conclusion
Angular2 is powerful framework to build complex and scalable applications with powerful productivity features. 
Angular2 is Strict and Verbose which guarantees consistency in the development, but losing some freedom in the process.
As of today it would be risky to start using Angular2, but its time will come soon. 
In the meantime, From FrontStack we are working to reduce the uncertainty with style guides and kick Starter projects to guide the development with best practices.


# Table

| low | | medium | | High |
|---|---|---|---|---|
| ![](assets/images/1.png) | ![](assets/images/2.png)  | ![](assets/images/3.png) | ![](assets/images/4.png) |  ![](assets/images/5.png) |

| Category | Score |
|----------|-------|
| Community | ![](assets/images/5.png) |
| Learning curve | ![](assets/images/4.png) |
| Performance | ![](assets/images/4.png) |
| Browser Compatibility | ![](assets/images/3.png) |
| Mobile Compatibility | ![](assets/images/3.png) |
| ES5 | ![](assets/images/3.png) |
| ES6 | ![](assets/images/5.png) |
| Web components | ![](assets/images/4.png) |
| Reuse components | ![](assets/images/4.png) |
| Security | ![](assets/images/5.png) |
| Time on market | ![](assets/images/4.png) |
| Scalability | ![](assets/images/5.png) |
| Knowledge needed | ![](assets/images/4.png) |
| Development speed | ![](assets/images/5.png) |
| Modules and libraries | ![](assets/images/5.png) |
| Stability | ![](assets/images/2.png) |
| SEO | ![](assets/images/5.png) |


## Qualification

| **Angular 2** | Qualification | ![](assets/images/4.png) |
|----|------|-----|

> This research has been documented by the resources mentioned above on this document and the FrontStack team can't make test to verify the fully complexity of Angular2 and it is based on our own experience.

# Sources

* [https://dzone.com/articles/typed-front-end-with-angular-2](https://dzone.com/articles/typed-front-end-with-angular-2)
* [https://auth0.com/blog/more-benchmarks-virtual-dom-vs-angular-12-vs-mithril-js-vs-the-rest/](https://auth0.com/blog/more-benchmarks-virtual-dom-vs-angular-12-vs-mithril-js-vs-the-rest/)
* [http://www.codingpedia.org/jhadesdev/angular-1-vs-angular-2-a-high-level-comparison/](http://www.codingpedia.org/jhadesdev/angular-1-vs-angular-2-a-high-level-comparison/)
* [https://medium.com/javascript-scene/angular-2-vs-react-the-ultimate-dance-off-60e7dfbc379c#.orc4cxhho](https://medium.com/javascript-scene/angular-2-vs-react-the-ultimate-dance-off-60e7dfbc379c#.orc4cxhho)
* [https://vsavkin.com/](https://vsavkin.com/)