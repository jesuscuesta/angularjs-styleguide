
# Angular 1.X Style Guide (No Components Oriented)

## Purpose

The purpose of this style guide is to provide guidance and best practices on building Angular applications by showing conventions and examples in the proccess. 

## Index

  1. [AngularJS Application Structure](#angularJS-application-structure)
  1. [Best Practices](#best-practices)
  1. [Controllers](#controllers)
  1. [Services](#services)  
  1. [Factories](#factories)
  1. [Data Services](#data-services)
  1. [Directives](#directives)

## AngularJS Application Structure

1. Introduction 
2. Basic Structure
3. Lift guidelines
4. Proposed Structure
5. Benefits of the Modularized Approach
6. Develop Guidelines

### Introduction

As we build _AngularJS_ applications, the number of files grows rapidly and this can impact the organization and structure of the applications directory. 
The aim of this document is to define a directory structure, following best practices and conventions, that will allow us to build scalable and maintainable applications.

### Basic Structure

The first approximation is to organize the application by file types, *controllers*, *views* and *directives* has their own folder etc.This structure is OK for small applications, but when the number of controllers, services etc. starts to grow, adding or changing functionality means having to locate the files to edit, identify the code to change, and then making sure no other functionality is affected.

### The LIFT guidelines

To improve on the standard structure we can apply the LIFT guidelines when defining our desired directory structure:
 
 1.  **L**ocating our code is easy
 2.  **I**dentify code at a glance
 3.  **F**lat structure as long as we can
 4.   **T**ry to stay DRY (Don’t Repeat Yourself) or _T-DRY_
  
**Locate**: Locating code needs to be untuitive, simple and fast.

**Identify**: When we look at a file we expect to know what it contains and represents.

**Flat**: Nobody wants to search 7 levels of folders to find a file. Keep it as flat as possible.

**T-DRY**: This has more to do with conventions. E.g. Don't include _view_ or _controller_ in the name of a module if it's obvious what it does.

### Proposed Structure 

The key to a clear structure is to have a short term view of implementation and a long term vision. In other words, start small but keep in mind on where the app is heading.

Keeping this in mind, 

With this is mind and applying the LIFT guidelines, the directory structure proposal is shown below:

```
    app/
        app.module.js
        app.config.js
        app.routes.js
        layout/
            shell.html
            shell.controller.js
            header.html
            header.controller.js
            ...
        widgets/
            mydirective/
                mydirective.directive.js
                mydirective.directive.html
            mycomponent/
                mycomponent.component.js
                mycomponent.component.html
            ...
        services/
            data.service.js
            logger.service.js
            ...
        feature1/
            feature1.html
            feature1.css
            feature1.controller.js
            feature1.controller.spec.js
            feature1.routes.js
            feature1.module.js
        ...
        featureN/
            featureN.html
            featureN.css
            featureN.controller.js
            featureN.controller.spec.js
            featureN.routes.js
            featureN.module.js
  assets/
    img/   // Images and icons for your application
    css/   // All styles related files
    js/    // Non-angular js files
    libs/  // 3rd-party libs E.g. jQuery.
    fonts/ // 3rd-party fonts
    index.html
```

Where:

| Folder/File  | Description  |
|---|---|
| **index.html** | The _index.html_ lives at the root of the front-end structure. It will primarily handle loading in all the libraries and Angular elements. |
| **assets** | The assets folder is also pretty standard. It will contain all the assets needed for your app that are not related to your AngularJS code. |
| **app** | This is where the application lives!<br>The _app.module.js_ file will handle the setup of your app, load in AngularJS dependencies and so on.<br>The _app.route.js_ file will handle all the routes and the route configuration.<br>The _app.config.js_ file can be used to establish configuration globally for the app E.g. constants.<br><br>The app folder contains the following sub-directories:    |
| **layout** | Place components that define the overall layout of the application here. These may include a shell view and a controller to act as the container for the app, navigation, menus, content areas etc. |
| **widgets** |  Reusable components and directives for the application. |
| **services**  | Services provide some service to the app for shareable features such as remote data access, data caching, local storage, and logging for example. |
| **features1..N**  | These named folders represent features of the application. E.g. _login_, _session_, or _gallery_ for example.<br>Each controller, module, view etc. is in it's own file.<br>The folder also contains test scripts, and css particular to the view if necessary.<br>When the global router _app.route.js_ becomes too large to maintain easily, we can also define routes for each feature. <br><br> In [Reference #1](#resources) John Papa talks about the **3-7 file guideline**. If a feature contains more than 7 files, it may be time to divide that feature into smaller features.|
|   |   |

### Benefits of the Modularized Approach

#### Code maintainability

  - Following the approach above will logically compartmentalize your apps and you will easily be able to locate and edit code.

#### Scalable

  - Your code will be much easier to scale. Adding new directives and pages will not bloat existing folders. On-boarding new developers should also be much easier once the structure is explained. Additionally, with this approach, you will be able to drop features in and out of your app with relative ease, so testing new functionality or removing it should be a breeze.

#### Debugging

  - Debugging your code will be much easier with this modularized approach to app development. It will be easier to find the offending pieces of code and fix them.

#### Testing

  - Writing test scripts and testing modernized apps is a whole lot easier then non-modularized ones.

## Best Practices

### Controllers 

#### controllerAs View Syntax

  - Use the [`controllerAs`](http://www.johnpapa.net/do-you-like-your-angular-controllers-with-or-without-sugar/) syntax over the `classic controller with $scope` syntax.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#controlleras-view-syntax)
  ```html
  <div ng-controller="CustomerController as customer">
      {{ customer.name }}
  </div>
  ```

#### controllerAs Controller Syntax

  - Use the `controllerAs` syntax over the `classic controller with $scope` syntax.

  - The `controllerAs` syntax uses `this` inside controllers which gets bound to `$scope`

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#controlleras-controller-syntax)
  ```javascript
  /* see next section */
  function CustomerController() {
      this.name = {};
      this.sendMessage = function() { };
  }
  ```

#### controllerAs with vm

  - Use a capture variable for `this` when using the `controllerAs` syntax. Choose a consistent variable name such as `vm`, which stands for ViewModel.
  
[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#controlleras-with-vm)
  ```javascript
  function CustomerController() {
      var vm = this;
      vm.name = {};
      vm.sendMessage = function() { };
  }
  ```

  Note: You can avoid any [jshint](http://jshint.com/) warnings by placing the comment above the line of code. However it is not needed when the function is named using UpperCasing, as this convention means it is a constructor function, which is what a controller is in Angular.

  ```javascript
  /* jshint validthis: true */
  var vm = this;
  ```

  Note: When creating watches in a controller using `controller as`, you can watch the `vm.*` member using the following syntax. (Create watches with caution as they add more load to the digest cycle.)

  ```html
  <input ng-model="vm.title"/>
  ```

  ```javascript
  function SomeController($scope, $log) {
      var vm = this;
      vm.title = 'Some Title';

      $scope.$watch('vm.title', function(current, original) {
          $log.info('vm.title was %s', original);
          $log.info('vm.title is now %s', current);
      });
  }
  ```

  Note: When working with larger codebases, using a more descriptive name can help ease cognitive overhead & searchability. Avoid overly verbose names that are cumbersome to type.

  ```html
  <input ng-model="productVm.title">
  ```

#### Bindable Members Up Top


  - Place bindable members at the top of the controller, alphabetized, and not spread through the controller code.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#bindable-members-up-top)
  ```javascript
  function SessionsController() {
      var vm = this;

      vm.gotoSession = gotoSession;
      vm.refresh = refresh;
      vm.search = search;
      vm.sessions = [];
      vm.title = 'Sessions';

      ////////////

      function gotoSession() {
        /* */
      }

      function refresh() {
        /* */
      }

      function search() {
        /* */
      }
  }
  ```

  Note: If the function is a 1 liner consider keeping it right up top, as long as readability is not affected.

  ```javascript
  function SessionsController(sessionDataService) {
      var vm = this;

      vm.gotoSession = gotoSession;
      vm.refresh = sessionDataService.refresh; // 1 liner is OK
      vm.search = search;
      vm.sessions = [];
      vm.title = 'Sessions';
  }
  ```

#### Function Declarations to Hide Implementation Details


  - Use function declarations to hide implementation details. Keep your bindable members up top. When you need to bind a function in a controller, point it to a function declaration that appears later in the file. This is tied directly to the section Bindable Members Up Top. For more details see [this post](http://www.johnpapa.net/angular-function-declarations-function-expressions-and-readable-code/).

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#function-declarations-to-hide-implementation-details)

  Notice that the important stuff is scattered in the preceding example. In the example below, notice that the important stuff is up top. For example, the members bound to the controller such as `vm.avengers` and `vm.title`. The implementation details are down below. This is just easier to read.

  ```javascript
  /*
   * recommend
   * Using function declarations
   * and bindable members up top.
   */
  function AvengersController(avengersService, logger) {
      var vm = this;
      vm.avengers = [];
      vm.getAvengers = getAvengers;
      vm.title = 'Avengers';

      activate();

      function activate() {
          return getAvengers().then(function() {
              logger.info('Activated Avengers View');
          });
      }

      function getAvengers() {
          return avengersService.getAvengers().then(function(data) {
              vm.avengers = data;
              return vm.avengers;
          });
      }
  }
  ```

#### Defer Controller Logic to Services

  - Defer logic in a controller by delegating to services and factories.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#defer-controller-logic-to-services)
  ```javascript
  function OrderController(creditService) {
      var vm = this;
      vm.checkCredit = checkCredit;
      vm.isCreditOk;
      vm.total = 0;

      function checkCredit() {
         return creditService.isOrderTotalOk(vm.total)
            .then(function(isOk) { vm.isCreditOk = isOk; })
            .catch(showError);
      };
  }
  ```

#### Keep Controllers Focused

  - Define a controller for a view, and try not to reuse the controller for other views. Instead, move reusable logic to factories and keep the controller simple and focused on its view.

#### Assigning Controllers


  - When a controller must be paired with a view and either component may be re-used by other controllers or views, define controllers along with their routes.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#assigning-controllers)

Note: If a View is loaded via another means besides a route, then use the `ng-controller="Avengers as vm"` syntax.


  ```javascript

  // route-config.js
  angular
      .module('app')
      .config(config);

  function config($routeProvider) {
      $routeProvider
          .when('/avengers', {
              templateUrl: 'avengers.html',
              controller: 'Avengers',
              controllerAs: 'vm'
          });
  }
  ```

  ```html
  <!-- avengers.html -->
  <div>
  </div>
  ``` 
### Services

#### Singletons

  - Services are instantiated with the `new` keyword, use `this` for public methods and variables. Since these are so similar to factories, the use of factories is recommended instead for consistency.

    Note: [All Angular services are singletons](https://docs.angularjs.org/guide/services). This means that there is only one instance of a given service per injector.

  ```javascript
  // service
  angular
      .module('app')
      .service('logger', logger);

  function logger() {
    this.logError = function(msg) {
      /* */
    };
  }
  ```

  ```javascript
  // factory
  angular
      .module('app')
      .factory('logger', logger);

  function logger() {
      return {
          logError: function(msg) {
            /* */
          }
     };
  }
  ```

### Factories   

#### Single Responsibility

  - Factories should have a [single responsibility](https://en.wikipedia.org/wiki/Single_responsibility_principle), that is encapsulated by its context. Once a factory begins to exceed that singular purpose, a new factory should be created.

#### Singletons

  - Factories are singletons and return an object that contains the members of the service.

    Note: [All Angular services are singletons](https://docs.angularjs.org/guide/services).

#### Accessible Members Up Top

  - Expose the callable members of the service (its interface) at the top, using a technique derived from the [Revealing Module Pattern](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#revealingmodulepatternjavascript).

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#accessible-members-up-top)

  ```javascript
   
  function dataService() {
      var someValue = '';
      var service = {
          save: save,
          someValue: someValue,
          validate: validate
      };
      return service;

      ////////////

      function save() {
          /* */
      };

      function validate() {
          /* */
      };
  }
  ```

  This way bindings are mirrored across the host object, primitive values cannot update alone using the revealing module pattern.

#### Function Declarations to Hide Implementation Details

  - Use function declarations to hide implementation details. Keep your accessible members of the factory up top. Point those to function declarations that appears later in the file. For more details see [this post](http://www.johnpapa.net/angular-function-declarations-function-expressions-and-readable-code).

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#function-declarations-to-hide-implementation-details-1)

  ```javascript
  /**
   * recommended
   * Using function declarations
   * and accessible members up top.
   */
  function dataservice($http, $location, $q, exception, logger) {
      var isPrimed = false;
      var primePromise;

      var service = {
          getAvengersCast: getAvengersCast,
          getAvengerCount: getAvengerCount,
          getAvengers: getAvengers,
          ready: ready
      };

      return service;

      ////////////

      function getAvengers() {
          // implementation details go here
      }

      function getAvengerCount() {
          // implementation details go here
      }

      function getAvengersCast() {
          // implementation details go here
      }

      function prime() {
          // implementation details go here
      }

      function ready(nextPromises) {
          // implementation details go here
      }
  }
  ```

### Data Services 

#### Separate Data Calls

  - Refactor logic for making data operations and interacting with data to a factory. Make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#separate-data-calls)

  ```javascript
   
  // dataservice factory
  angular
      .module('app.core')
      .factory('dataservice', dataservice);

  dataservice.$inject = ['$http', 'logger'];

  function dataservice($http, logger) {
      return {
          getAvengers: getAvengers
      };

      function getAvengers() {
          return $http.get('/api/maa')
              .then(getAvengersComplete)
              .catch(getAvengersFailed);

          function getAvengersComplete(response) {
              return response.data.results;
          }

          function getAvengersFailed(error) {
              logger.error('XHR Failed for getAvengers.' + error.data);
          }
      }
  }
  ```

    Note: The data service is called from consumers, such as a controller, hiding the implementation from the consumers, as shown below.

  ```javascript
   

  // controller calling the dataservice factory
  angular
      .module('app.avengers')
      .controller('AvengersController', AvengersController);

  AvengersController.$inject = ['dataservice', 'logger'];

  function AvengersController(dataservice, logger) {
      var vm = this;
      vm.avengers = [];

      activate();

      function activate() {
          return getAvengers().then(function() {
              logger.info('Activated Avengers View');
          });
      }

      function getAvengers() {
          return dataservice.getAvengers()
              .then(function(data) {
                  vm.avengers = data;
                  return vm.avengers;
              });
      }
  }
  ```

#### Return a Promise from Data Calls

  - When calling a data service that returns a promise such as `$http`, return a promise in your calling function too.

[More Info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#return-a-promise-from-data-calls)

  ```javascript

  activate();

  function activate() {
      /**
       * Step 1
       * Ask the getAvengers function for the
       * avenger data and wait for the promise
       */
      return getAvengers().then(function() {
          /**
           * Step 4
           * Perform an action on resolve of final promise
           */
          logger.info('Activated Avengers View');
      });
  }

  function getAvengers() {
        /**
         * Step 2
         * Ask the data service for the data and wait
         * for the promise
         */
        return dataservice.getAvengers()
            .then(function(data) {
                /**
                 * Step 3
                 * set the data and resolve the promise
                 */
                vm.avengers = data;
                return vm.avengers;
        });
  }
  ```


### Directives   
#### Limit 1 Per File

  - Create one directive per file. Name the file for the directive. [More info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#directives)

    

    > Note: "**Best Practice**: Directives should clean up after themselves. You can use `element.on('$destroy', ...)` or `scope.$on('$destroy', ...)` to run a clean-up function when the directive is removed" ... from the Angular documentation.

  ```javascript
   
  /* calendar-range.directive.js */

  /**
   * @desc order directive that is specific to the order module at a company named Acme
   * @example <div acme-order-calendar-range></div>
   */
  angular
      .module('sales.order')
      .directive('acmeOrderCalendarRange', orderCalendarRange);

  function orderCalendarRange() {
      /* implementation details */
  }
  ```

    Note: There are many naming options for directives, especially since they can be used in narrow or wide scopes. Choose one that makes the directive and its file name distinct and clear. Some examples are below, but see the [Naming](#naming) section for more recommendations.

#### Manipulate DOM in a Directive

  - When manipulating the DOM directly, use a directive. If alternative ways can be used such as using CSS to set styles or the [animation services](https://docs.angularjs.org/api/ngAnimate), Angular templating, [`ngShow`](https://docs.angularjs.org/api/ng/directive/ngShow) or [`ngHide`](https://docs.angularjs.org/api/ng/directive/ngHide), then use those instead. For example, if the directive simply hides and shows, use ngHide/ngShow. [More info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#manipulate-dom-in-a-directive)
 
   
#### Provide a Unique Directive Prefix

  - Provide a short, unique and descriptive directive prefix such as `acmeSalesCustomerInfo` which would be declared in HTML as `acme-sales-customer-info`. [More info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#provide-a-unique-directive-prefix)

    Note: Avoid `ng-` as these are reserved for Angular directives. Research widely used directives to avoid naming conflicts, such as `ion-` for the [Ionic Framework](http://ionicframework.com/).

#### Restrict to Elements and Attributes

  - When creating a directive that makes sense as a stand-alone element, allow restrict `E` (custom element) and optionally restrict `A` (custom attribute). Generally, if it could be its own control, `E` is appropriate. General guideline is allow `EA` but lean towards implementing as an element when it's stand-alone and as an attribute when it enhances its existing DOM element. [More info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#restrict-to-elements-and-attributes)

  ```html
    
  <my-calendar-range></my-calendar-range>
  <div my-calendar-range></div>
  ```

  ```javascript
   
  angular
      .module('app.widgets')
      .directive('myCalendarRange', myCalendarRange);

  function myCalendarRange() {
      var directive = {
          link: link,
          templateUrl: '/template/is/located/here.html',
          restrict: 'EA'
      };
      return directive;

      function link(scope, element, attrs) {
        /* */
      }
  }
  ```

#### Directives and ControllerAs

  - Use `controller as` syntax with a directive to be consistent with using `controller as` with view and controller pairings. [More info +](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#directives-and-controlleras)

    Note: The directive below demonstrates some of the ways you can use scope inside of link and directive controllers, using controllerAs. I in-lined the template just to keep it all in one place.

    Note: Note that the directive's controller is outside the directive's closure. This style eliminates issues where the injection gets created as unreachable code after a `return`.

  ```html
  <div my-example max="77"></div>
  ```

  ```javascript
  angular
      .module('app')
      .directive('myExample', myExample);

  function myExample() {
      var directive = {
          restrict: 'EA',
          templateUrl: 'app/feature/example.directive.html',
          scope: {
              max: '='
          },
          link: linkFunc,
          controller: ExampleController,
          // note: This would be 'ExampleController' (the exported controller name, as string)
          // if referring to a defined controller in its separate file.
          controllerAs: 'vm',
          bindToController: true // because the scope is isolated
      };

      return directive;

      function linkFunc(scope, el, attr, ctrl) {
          console.log('LINK: scope.min = %s *** should be undefined', scope.min);
          console.log('LINK: scope.max = %s *** should be undefined', scope.max);
          console.log('LINK: scope.vm.min = %s', scope.vm.min);
          console.log('LINK: scope.vm.max = %s', scope.vm.max);
      }
  }

  ExampleController.$inject = ['$scope'];

  function ExampleController($scope) {
      // Injecting $scope just for comparison
      var vm = this;

      vm.min = 3;

      console.log('CTRL: $scope.vm.min = %s', $scope.vm.min);
      console.log('CTRL: $scope.vm.max = %s', $scope.vm.max);
      console.log('CTRL: vm.min = %s', vm.min);
      console.log('CTRL: vm.max = %s', vm.max);
  }
  ```

  ```html
  <!-- example.directive.html -->
  <div>hello world</div>
  <div>max={{vm.max}}<input ng-model="vm.max"/></div>
  <div>min={{vm.min}}<input ng-model="vm.min"/></div>
  ```

    Note: You can also name the controller when you inject it into the link function and access directive attributes as properties of the controller.

  ```javascript
  // Alternative to above example
  function linkFunc(scope, el, attr, vm) {
      console.log('LINK: scope.min = %s *** should be undefined', scope.min);
      console.log('LINK: scope.max = %s *** should be undefined', scope.max);
      console.log('LINK: vm.min = %s', vm.min);
      console.log('LINK: vm.max = %s', vm.max);
  }
  ```

  - Use `bindToController = true` when using `controller as` syntax with a directive when you want to bind the outer scope to the directive's controller's scope.

  ```html
  <div my-example max="77"></div>
  ```

  ```javascript
  angular
      .module('app')
      .directive('myExample', myExample);

  function myExample() {
      var directive = {
          restrict: 'EA',
          templateUrl: 'app/feature/example.directive.html',
          scope: {
              max: '='
          },
          controller: ExampleController,
          controllerAs: 'vm',
          bindToController: true
      };

      return directive;
  }

  function ExampleController() {
      var vm = this;
      vm.min = 3;
      console.log('CTRL: vm.min = %s', vm.min);
      console.log('CTRL: vm.max = %s', vm.max);
  }
  ```

  ```html
  <!-- example.directive.html -->
  <div>hello world</div>
  <div>max={{vm.max}}<input ng-model="vm.max"/></div>
  <div>min={{vm.min}}<input ng-model="vm.min"/></div>
  ```

## Resources

 1. [App structuring guidelines](https://johnpapa.net/angular-app-structuring-guidelines/). John Papa
 2. [Application Structure](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md#application-structure). John Papa - GitHub
