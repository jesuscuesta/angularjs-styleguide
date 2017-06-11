# Pruebas de concepto Angular2

## Conclusiones

### Estructura del Proyecto

```
angular2-basic/
 ├──config/                         * our configuration
 |
 ├──src/                            * our source files that will be compiled to javascript
 |   ├──main.browser.ts             * our entry file for our browser environment
 │   │
 |   ├──index.html                  * our index page
 │   │
 |   ├──polyfills.ts                * our polyfills file
 │   │
 |   ├──vendor.ts                   * our vendor file
 │   │
 │   ├──app/                        * WebApp: folder
 |   |   ├──shared/                 * our shared modules, components, services and pipes
 |   |   ├──core/                   * our main application modules
 |   |   ├──modules/                * our entry file for our browser environment
 │   │   │
 │   │   ├──app.routing.ts          * a simple end-to-end test for /
 │   │   │
 │   │   ├──app.module.ts           * App.ts: a simple version of our App component components
 │   │   │
 │   │   ├──index.ts           * our source entry file
 │   │   .
 │   │
 │   └──assets/                * static assets
 │
 │
 ├──tslint.json                * typescript lint config
 ├──typedoc.json               * typescript documentation generator
 ├──tsconfig.json              * config that webpack uses for typescript
 ├──package.json               * what npm uses to manage it's dependencies
 └──webpack.config.js          * webpack main configuration file

```

### Starter Kit Minimo

**Incluido**
* Build con WebPack JIT y AoT
* Carga de Modulos Lazy Load exepto Main
* Estructura de Proyecto
    * Core / Shared / Modules
    * Modulo de AppShell en la App (Guia de estilo)
    * Los recursos de Modulos (Imagenes, etc.) en Assets global
* CSS
    * Plain CSS para la App
    * Plugin de SASS para WebPack
* Test
    * Calidad de Codigo: Codelyzer (http://codelyzer.com/)
    * Unitarios: Karma Mocha Jasmine --> con Polymer metemos Mocha 
    * Funcionales: Protractor
    * Reporting: los acordados con ALM de Angular1.5
* TypeDoc para Documentacion ( docuemtar TypeScript )

**Excluido**
* Modulo de cacheo u Offline
* Modulo internacionalizacion ( i18n )

## Puntos en comun

* Angular2 AoT
    * http://slides.com/agesteira/ng2-aot-wp2/

* Build
    * Webpack vs System:
        * WebPack nos convences a la mayoria pero tiramos por webpack, implicaría dominar webpack
            * Falta resolver incidencia con AoT
    * System (angular-seed) Necesitariamos hacer pruebas con AOT/Lazy load/i18n
    * Implementar construccion con AOT y JIT (JIT por defecto hasta que se solucione incidencia con AoT)

* AngularClass:
    * Utiliza hmr hecho por los de @angularClass
    * Eliminar todos los modulos de angularClass
    * E2E no funciona con angularClass (Dependencia rota)

* Arquitectura de Modulos:
    * Shared / Core / Modules
    * AppShell con el modulo principal, el resto con LazyLoad.
    * Arquitecturas redux no para angular2 basic
    * Imagenes/assets en componentes? Falta resolver
    * **ViewEncapsulation** define el tipo de encapsulacion a nivel de Componente.
        * Probar tipo de encapsulacion (default, emulada) (mirar tambien con jit o aot)
        * Emulated (con AoT queda resuelto) , Native (Polyfils) y None ¿¿??

* Routing:
    * Se redefinen las rutas cuando hay varias que definen la misma? se sobreescribe?
    * Authentication con Guards en el Route con Lazy Load
    * **router.events.subscribe** nos provee de Info de Navegación.
        * Navigation (se puede controlar las rutas y navegación)(spinners, google analytics)
    * **RouterModule - preLoadingModule**: PreloadAllModule (Precarga Selectiva)
    * **NonContentModule**: Carga por defecto on error

 * Cache / Offline:
    * OfflinePluing plugin util para definir la cache de la applicacion.
        * AppShell con el modulo main
    * Emplea serviceworkers.
    * appCache o ServiceWorkerCache? Pendiente de resolver   

* Herramientas:
    * webpack dashboad (swag para consola)
    * Augury (extension de chrome para debuggear Angular 2)

* Pruebas:
    * Pruebas unitarias dentro en el moduo
    Pruebas funcionales fuera

* Optimizaciones
    * Change detection OnPush (solo actualiza cuando se haga un cambio sobre una variable input) ( definir en el documento de buenas prácticas)
        * http://blog.thoughtram.io/angular/2016/02/22/angular-2-change-detection-explained.html
    * RouterModule: preLoadingModule (Precarga Selectiva). Existe opcion de PreloadAllModule
        * Definición a nivel de Modulo, no Component.

* Integracion con Polymer:
    * Web-componnets-shard: Chunks de HTML Imports
        * Util para Imports de web components (Polymer)
        * https://github.com/PolymerLabs/web-component-shards

* Rollup
    * Rollup js (webpack no combina aun con rollup) JSPM vs SystemJS ???

* ALM
    * Script para setear PATH en un prebuild
    * Test reporter sincronizado con ALM

* Configuración por entorno:
    * Configuracion por entornos con un json y con carga en tiempo de construccion

* Angular CLI esta muy verde.

### Tareas Pendientes

* Es necesatio profundizar en WebPack para dominarlo.
* Hacer pruebas con ALM. (comprobar ciclo con Serenity) Dependencias globales en ALM?
    * Propia integración continua
* Imagenes/assets en componentes? Falta resolver
* Web component shards (polymer) Si vamos hacer pruebas con Angular 2 y Polymer, (ver como incluirlo con webpack) (util para hacer los import de los html en webpack) Hablar de esto cuando hagamos la parte de Polymer

### Riesgos
