### Angular 8
- Differential loading: lets you create two different bundles of your app. Attributes on the script tag in your index.html file let the browser request the most appropriate bundle; modern browsers will request a bundle that uses ES2015 JavaScript syntax and will be significantly smaller than the legacy bundle that uses ES5 syntax
- Ivy Compiler - opt in preview feature
- Bazel builder
- Webworker in Angular CLI
- lazy loading modules better way (earlier loadChildren: '../lazy.module#LazyModule) prone to errors since it is a string (new way - loadChildren: import('../lazy.module).then(m => m.LazyModule)))

### Angular 9
- Ivy - default compiler
- latest typesccript version support (3.6 & 3.7)
- Official components for youtube and google maps

### Angular 10
- Create project with --strict rules
- TS 3.9 support
- New date range picker
- CommonJS import warnings
