### Explain Angular Directive / Component life cycle.
Angular has following life cycle hooks for a directive / component
- ngOnChanges (many)
- ngOnInit (once)
- ngDoCheck (many)
- ngAfterContentInit (once)
- ngAfterContentChecked (many)
- ngAfterViewInit (once)
- ngAfterViewChecked (many)
- ngOnDestroy (once)

### ng-content


### ElementRef
A wrapper around the native element through which we can access the HTML element
```html
<div #hello>Hello Angular</div>
```
```javascript
@ViewChild('hello', { static: false }) divHello: ElementRef;

print() {
  console.log(this.divHello.nativeElement);
}
```

### Hostbinding and HostListener
HostBinding is used to bind the decorated element's property in the directive
```html
<span #myDirective ></span>
```
```javascript
// myDirective
@HostBinding('style.color') color;

changeColor() {
  this.color = "red";
}
```

HostListener - Listening to the event of the decorated element
```javascript
// myDirective
@HostListener('mouseenter') onMouseEnter(){
}
```

### ElementRef or HostBinding & HostListener
ElementRef is ot preferred since it gives direct access to the native DOM element which makes it vulnerable to XSS attacks whereas HostBinding and HostListener are handled by Angular and is safer way.
