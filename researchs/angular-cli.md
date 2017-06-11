![](assets/angular_cli_logo.png)

# Angular CLI Analysis

## Introduction 

The objective of this article is to clarify some doubts around the new Angular CLI. The article gather information about its usage, advantages and limitations of the tool.  

## General Information
* Official site: [https://cli.angular.io/](https://cli.angular.io/)
* GitHub:  [https://github.com/angular/angular-cli](https://github.com/angular/angular-cli)
* Current version: v1.0.0-beta.17 **(still in Beta)** - for more info [link](https://github.com/angular/angular-cli/releases)

## Technical Information
* Build tool: [WebPack](https://webpack.github.io/)
* Testing Framework: 
    * [Codelyzer](https://github.com/mgechev/codelyzer) for code quality.
    * Karma as a test runner.
    * Jasmine for unit testing.
    * Protractor for end to end testing.
* App preview: [BrowserSync](https://www.browsersync.io/)

## Advantages 

The use of the Angular CLI will bring the following advantages:

### Good productivity tool:

Angular CLI comes with useful commands to generated component seeds which speed up the development significantly.

Among others you could find:  

* ng new <app-name> <options...>    
    To create the application
* ng build <options...>   
    To create the bundle of the application 
* ng test <options...>   
    To lunch the unit test 
* ng e2e  
    To lunch the ent to end tests
* ng serve <options...>   
    To preview the application on the browser
* ng install <addon-name>   
    To include pluggins on the CLI process 
* ...

### Fast setup:

Angular CLI provides a minimal project bases to have an application in seconds up and running in your browsers.
A good starting point to begin with the essential configuration:
* Build Targets and Environment Files
* Test configuration
* Bundling
* Proxy To Backend
* Project assets
* CSS preprocessor integration
    
### Supports sass, less and stylus 

WebPack simplify the build process integrating the style compilation automatically inside. 
At the same time, it simplify the usage of stylesheets in the app because only compiled resources are used. 

For more info [https://github.com/angular/angular-cli#css-preprocessor-integration](https://github.com/angular/angular-cli#css-preprocessor-integration)

## Inconveniences

It is important to have into account the following inconveniences before you start using the Angular CLI:

### Heavy

The amount of dependencies, plugins and components requested by the CLI are so large that It will take several minutes to download and install. 

In Numbers: 323 MB,  40,361 Files and 5,998 folders

### Slow Reload

The build process in production and development environment is slower than other approaches because of Webpack bundling process even though it is possible already to implement hot module reload in Webpack.
There are available different seeds with this approach. 

### Project scaffolding

Angular CLI enforces angular [style guide folder structure](https://angular.io/styleguide#!#application-structure) which is useful in early stages and small projects.

When the structure become complex, for example in projects with a scalable nature, the CLI seeds to create components lose potential.   

### Limited Configuration

Angular CLI provides predefined process very useful for developments but it limited 

But Angular CLI provide a way to setup some parameter thought a config file (angular-cli.json) such as build targets and environment, external resources, global Library Installation, test configuration files, and default App behavior (style extension, interface prefix or lazy load router). 

Even though, this customization capability is very limited, it could be useful for small projects with short scope and proof of concepts.

If you are a Webpack'er and need access to the blackbox, we will need to wait a bit. 

### Lack of stability

At this point Angular CLI is not stable. Since May when it was announced the first Beta version, it has been release 28 versions in the las three months.

For more information about the last releases: [https://github.com/angular/angular-cli/releases](https://github.com/angular/angular-cli/releases)

In some cases, new releases comes with breaking changes that affects the Angular2 application with the need of a migration 
For more Information about migrations: 

* [https://github.com/angular/angular-cli/wiki/Upgrading-from-Beta.10-to-Beta.12](https://github.com/angular/angular-cli/wiki/Upgrading-from-Beta.10-to-Beta.12)
* [https://github.com/angular/angular-cli/wiki/Upgrading-from-Beta.10-to-Beta.14](https://github.com/angular/angular-cli/wiki/Upgrading-from-Beta.10-to-Beta.14)

### Complex 3rd party support

In addition to the standard Angular2 procedure to include 3rd party libraries, the integration of new modules suppose additional steps which slow down the development. 

## Conclusion

At this point, Angular CLI is **not suitable** for its usage in big project, applications with scalable needs or projects with a distributed development approach.
On the other hand, it could be useful for projects with short projection or small scope such as proof of concepts or for learning purposes.  

## Sources

* [https://github.com/angular/angular-cli](https://github.com/angular/angular-cli)
* [https://medium.com/@martin_hotell/angular-cli-and-real-development-productivity-4ba3c1865eda#.abu2ul7uh](https://medium.com/@martin_hotell/angular-cli-and-real-development-productivity-4ba3c1865eda#.abu2ul7uh)
* [https://medium.com/@jeff.boothe/angular-cli-meets-webpack-7c9b1a1e1e89#.ug46puse9](https://medium.com/@jeff.boothe/angular-cli-meets-webpack-7c9b1a1e1e89#.ug46puse9)