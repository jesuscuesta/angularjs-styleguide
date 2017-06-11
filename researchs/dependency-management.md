# Dependency management
## [NPM]
[npm] is a [NodeJS](https://nodejs.org/es/docs/) package manager. As its name would imply, you can use it to install node programs. Also, if you use it in development, it makes it easier to specify and link dependencies.

On one hand [npm] was created to install modules used in a node.js environment, or development tools built using node.js such Karma, lint, minifiers and so on. [npm can install modules locally in a project ( by default in node_modules ) or globally to be used by multiple projects. In large projects the way to specify dependencies is by creating a file called package.json which contains a list of dependencies. That list is recognized by [npm when you run [npm install, which then downloads and installs them for you.

We see better to use [npm] in a project with Angular 2, where we can create console command aliases to handle Webpack and handle node dependencies.

In Polymer we will use NPM for all node modules, such as [Gulp] and all the [Gulp] plugins we need.

An example of "package.json" could be this:
```json
{
  "name": "myExample",
  "version": "0.0.1",
  "license": "MIT",
  "scripts": {
    "serve:dev": "webpack-dev-server --config config/webpack.dev.js --progress --profile --watch --content-base src/ --inline --hot",
    "serve:pro": "npm run build:pro & http-server dist --cors -o"
  },
  "dependencies": {
    "@angular/common": "2.2.1",
    "@angular/compiler": "2.2.1",
    "@angular/core": "2.2.1",
    "@angular/forms": "2.2.1",
    "@angular/http": "2.2.1",
    "@angular/material": "^2.0.0-alpha.10",
    "@angular/platform-browser": "2.2.1",
    "@angular/platform-browser-dynamic": "2.2.1",
    "@angular/platform-server": "2.2.1",
    "@angular/router": "3.2.1",
    "@angularclass/conventions-loader": "^1.0.2",
    "@angularclass/hmr": "~1.2.2",
    "@angularclass/hmr-loader": "~3.0.2",
    "assets-webpack-plugin": "^3.4.0"
  },
  "devDependencies": {
    "@types/hammerjs": "^2.0.33",
    "@types/jasmine": "^2.2.34",
    "@types/node": "^6.0.38",
    "@types/selenium-webdriver": "2.53.33",
    "@types/source-map": "^0.1.27",
    "@types/uglify-js": "^2.0.27",
    "@types/webpack": "^1.12.34",
    "imports-loader": "^0.6.5",
    "istanbul-instrumenter-loader": "0.2.0",
    "jasmine-spec-reporter": "^2.7.0",
    "json-loader": "^0.5.4",
    "karma": "^1.2.0"
  }
}

```

[Gulp]: https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md
[NPM]: https://www.npmjs.com/

## [Yarn](https://yarnpkg.com/)

Yarn caches every package it downloads so it never needs to download it again. It also parallelizes operations to maximize resource utilization so install times are faster than ever.

In the Node ecosystem, dependencies get placed within a node_modules directory in your project. However, this file structure can differ from the actual dependency tree as duplicate dependencies are merged together. The npm client installs dependencies into the node_modules directory non-deterministically. This means that based on the order dependencies are installed, the structure of a node_modules directory could be different from one person to another. These differences can cause “works on my machine” bugs that take a long time to hunt down.

Yarn resolves these issues around versioning and non-determinism by using lockfiles and an install algorithm that is deterministic and reliable. These lockfiles lock the installed dependencies to a specific version, and ensure that every install results in the exact same file structure in node_modules across all machines. The written lockfile uses a concise format with ordered keys to ensure that changes are minimal and review is simple.

The install process is broken down into three steps:

1. **Resolution**: Yarn starts resolving dependencies by making requests to the registry and recursively looking up each dependency.
2. **Fetching**: Next, Yarn looks in a global cache directory to see if the package needed has already been downloaded. If it hasn't, Yarn fetches the tarball for the package and places it in the global cache so it can work offline and won't need to download dependencies more than once. Dependencies can also be placed in source control as tarballs for full offline installs.
3. **Linking**: Finally, Yarn links everything together by copying all the files needed from the global cache into the local node_modules directory.

In addition to making installs much faster and more reliable, Yarn has additional features to further simplify the dependency management workflow.

- Compatibility with both the npm and bower workflows and supports mixing registries.
- Ability to restrict licenses of installed modules and a means for outputting license information.
- Exposes a stable public JS API with logging abstracted for consumption via build tools.
- Readable, minimal, pretty CLI output.

## [Bower](https://bower.io/)

Bower can manage components that contain HTML, CSS, JavaScript, fonts or even image files. Bower doesn’t concatenate or minify code or do anything else - it just installs the right versions of the packages you need and their dependencies.

Bower is a "package manager for the web." Bower lets you install and restore client-side packages, including JavaScript and CSS libraries. For example, with Bower you can install CSS files, fonts, client frameworks, and JavaScript libraries from external sources. Bower resolves dependencies and will automatically download and install all the packages you need. For example, if you configure Bower to load the Bootstrap package, the necessary jQuery package will automatically come along for the ride.

We will use bower for projects with Polymer, since all the Web Components that we need, we will manage them by Bower.

Bower can differentiate those dependencies that we are only going to use in production and the dependencies that will not be needed at the time of project development.

In "dependencies" we will have dependencies as a Web component and in "devDependencies" we will have packages like "web-component-tester" to help us in the unit tests in the development of the project.

An example of "bower.json" could be this:
```json
{
  "name": "MyExample",
  "authors": [
    "Me"
  ],
  "private": true,
  "dependencies": {
    "app-layout": "polymerelements/app-layout#^0.9.0",
    "app-route": "polymerelements/app-route#^0.9.1",
    "iron-flex-layout": "polymerelements/iron-flex-layout#^1.0.0",
    "iron-icon": "polymerelements/iron-icon#^1.0.0",
    "iron-iconset-svg": "polymerelements/iron-iconset-svg#^1.0.0",
    "iron-localstorage": "polymerelements/iron-localstorage#^1.0.0",
    "iron-media-query": "polymerelements/iron-media-query#^1.0.0",
    "iron-pages": "polymerelements/iron-pages#^1.0.0",
    "iron-selector": "polymerelements/iron-selector#^1.0.0",
    "paper-icon-button": "PolymerElements/paper-icon-button#~1.1.1",
    "polymer": "polymer/polymer#^1.4.0"
  },
  "devDependencies": {
    "web-component-tester": "^4.0.0"
  }
}
```