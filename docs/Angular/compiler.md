### What is a Compiler
Angular Compiler compiles the code into Javascript and also bundles it into JS files. During bundling the compiler does several activities like tree-shaking, minification, etc.

### Why Compiler
Browser doesn't understands the (ts) code that is written for angular. Angular compiler understands the code and helps the browser to render it.

### Ivy Compiler
Ivy is improved compiler and runtime which is completely released with Angular 9. 

### Types of Compiler in Angular
JIT - Compiles the app in the browser at run time. Default when you run ```ng serve``` OR ```ng build```
AOT - Compiles the app at build time. ```ng build --aot``` , ```ng serve --aot``` and ```ng build --prod``` builds with AOT compilation

### Advantages of AOT
- Faster rendering: Browser downloads pre vompiled version of the app.
- Smaller Angular framework download size - doesn't require downloading angular compiler.
- Fewer asynchronous requests - it inlines HTML templates and CSS style sheets within the application javascript (thus eliminates seperate HTTP calls to download them).
- Detect template errors earlier - detects and reports template binding errors at build time.
- Better Security - Copiles HTML templates and components into JS files. So there won't be any injection attacks.

## Tree Shaking
A concept of removing unused code (module/component/class etc.)
