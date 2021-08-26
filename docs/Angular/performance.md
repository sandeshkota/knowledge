### What are different steps to improve performance of an Angular application ?
- AOT - removes dependency on the compiler in the browser.
- Lazy Loading - Load moduels based on need
- Differential Loading
- InjectableIn services - Instead of adding it in providers: [] so that it will be removed if not used - tree shaking
- Enable OnPush change detection strategy OR NgZone - RunOutsideAngular()
