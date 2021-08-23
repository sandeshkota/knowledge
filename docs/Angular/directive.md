### What are Directives ?
Directives tells angular how an element is rendered.

### Types of Directives ?
- Structural Directive : Changes the structure of the DOM element. e.g. *ngIf , *ngFor, [ngSwitch] (*ngSwitchCase, *ngSwitchDefault) etc..
- Attribute Directive : Adds behavior to the existing DOM element. e.g. [ngClass], [ngStyle], [hidden] etc..
- Component : Are Directives with a Template.

### Components
Components are the basic building block of Angular. Angular constructs component tree which is used to render the page. It tells angular how a component should be displayed and also how to handle bahviors of a component. 

```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
}
```

### Component v/s Directive
Directives add behavior to existing DOM or change the structure of existing DOM
Components are used to create UI. Components are directives with a template.
