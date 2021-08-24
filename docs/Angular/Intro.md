### What is Angular
A JavaScript framework to build front end applications

### Angular JS v/s Angular

|  Angular JS  |      Angular    |
| :----------: | :-------------: |
|    .js       |       .ts       |
|    MVC       |  Component Tree |

### What is Type Script ?
Typescript is a super set of Javascript which adds the feature of type checking.  
In the end, Angluar converts typescript to javascript as browsers doesn't understand typescript yet. 

### Why not Angular 3 ?
To manage version that was there within the Angular libraries

### What are the key functionalities of Angular ?
- Directive
- Component
- Module
- Services
- Metadata
- Pipes
- Guards
- Routing
- Dependency Injection
- Change Detection (1way & 2way binding)

### What are metadata / annotations ?
The metadata is something which are added to a class / method / properties / parameters, which tells angular about it's behaviour.
- Class ( @Component , @Directive , @MNgModule , @Pipe , @Injectable )
- Method ( @HostListener )
- Properties ( @Output , @Input , @HostBinding )
- Parameters ( @Optional , @Self , @SkipSelf ) 

### What are Modules ? NgModule in Angular ?
Modules in Angualre is a logical enclosure of a certain functionality. Consists components, directives, pipes, etc.. related to a certain funcitonality
e.g. FormsModule, ReactiveFormsModule, HttpModule, BrowserModule, etc..

### Different Configuration in Angular Module ?
Declarations - The buildings blocks of this module - components, directives, pipes
Imports - List of other modules that are needed for this module
Exports - THe Components which should be exposed  to other modules when imported
Providers - The services which are required for this module. Angular keeps a track of this list and injects it wherever needed. Creates a singleton
Bootstrap - Tells angular which component to bootstrap at the start of the application

```javascript
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
  ],
  exports: [
    AppComponent,
  ],
  providers: [
    { provide: HTTP_INTERCEPTORS, useClass: JwtInterceptor, multi: true },
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### Crete a new Module and Import it in App Module
```javascript
// sample.module.ts file
import { NgModule } from '@angular/core';
import { SampleComponent } from './sample.component';

@NgModule({
  declarations: [ SampleComponent ],
  exports: [ SampleComponent ]
})
export class SampleModule {
}


// app.module.ts
import { NgModule } from '@angular/core';
import { SampleModule } from './sample.module'; 

@NgModule({
  imports: [ SampleModule ]
})
export class SampleModule {
}

// any component in AppModule
<app-sample></app-sample>
```
