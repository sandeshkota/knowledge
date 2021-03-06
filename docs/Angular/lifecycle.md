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

### ngOnInit 
This event is called when Angular binds the tempalte to the components properties

### ngAfterContentInit
This event is triggered after the content projection. Content Projection is a technique wherein you can send the template/view information from parent to child.  
@ContentChild() property is bound only after this lifecycle event.

### ngAfterViewInit
This event is triggered after the child component is bound. 
@ViewChild() property is bound only after this lifecycle event.

### ngOnDestroy
This event is called when Angular starts destroying the component (may be bcoz of navigation wherenin it has to load another component in it's place)

### ElementRef
A wrapper around the native element through which we can access the HTML element
- A directive - injected in constructor

```javascript
@Directive({ selector: '[highlight]' })

export class HighlightDirective implements OnChanges {
  defaultColor =  'rgb(211, 211, 211)'; // lightgray
  @Input('highlight') bgColor = '';

  constructor(private el: ElementRef) {
  }

  ngOnChanges() {
    this.el.nativeElement.style.backgroundColor = this.bgColor || this.defaultColor;
  }
}
```

- Child element

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
