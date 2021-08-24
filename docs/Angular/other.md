### Difference b/w cosntructor and ngOnInit ?

### Types of Data Binding
Interpolation {{ }}
Property Binding [ ]
Event Binding ( )
Two Way Binding [( )]

### Difference b/w Interpolation and Property Binding ?
Interpolation is used for strings. Property binding can have any type.


### What is template variable ? How is it used ?
It is a way referring an element within a template

### What is service ?
A service is a class which is used to store a common functionality which is needed across module/s.


### ng-template
As the name suggests the <ng-template> is a template element that Angular uses with structural directives (*ngIf, *ngFor, [ngSwitch] and custom directives).
```html
  <div *ngIf="shouldPrint" >Hello World</div>  
```
It will be converted as
```html
  <ng-template *ngIf="shouldPrint">
    <div>Hello World</div>  
  </ng-template>
```
  
### ng-container
Is a grouping element that doesn't interfere with styles or layout because Angular doesn't put it in the DOM
```html
  <ng-container *ngFor="let item of items" >
    <span> {{item.name}} </span>
  </ng-container>
```
By doing this we are not printing any extra HTML element. If not for ng-container, we would have used div and it will be rendered which is actually not needed
  
### ng-content
They are used to create configurable components. This means the components can be configured depending on the needs of its user. This is also known as Content Projection.
```html
<!-- info.component -->
<div class="content">
  <h1> Welcome </h1>
  <ng-content></ng-content>
</div>
```
The ng-content will be replaced by the actual content where the component is used
```html
<info-component>
  <span> Copyrights @SK </span>
</info-component>
```

### Multiple Content Projections using ng-content
```html
<div class="content">
  <h1> Welcome </h1>
  <ng-content select="h2"></ng-content>
  <ng-content select="span"></ng-content>
</div>
```
usage
```html
<info-component>
  <h2> This is my first project </h2>
  <span> Copyrights @SK </span>
</info-component>
```

  
### ng-template
Used when a tempalte should be insterted in multiple places
```html
  <div>
    Welcome to my first site
    <ng-container *ngTemplateOutlet="copyrightInfo"></ng-container>
  </div>
  
  <div>
    Profile details
    <ng-container *ngTemplateOutlet="copyrightInfo"></ng-container>
  </div>
  
  <ng-template #copyrightInfo>
  </ng-template>
  
```
