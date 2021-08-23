### What are Pipes ?
Pipes in Angular are used to transform data from one format to another while rendering. Pipes doesn't change the actual value and instead only change the value/format for just showing it to users (in HTML).  
Create a Pope class and add it in the AppModule's declarations.
```javascript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({name: 'exponentialStrength'})
export class AppAppendPipe implements PipeTransform {
  transform(value: string): string {
    return "App - " + value;
  }
}
```
The above Pipe can be used as below,
```html
<span>{{ title | AppAppend }}</span>
```

### What are Parameterized Pipes ?
Is a type of pipe which accepts parameters which tells on how to transform the data. Ex:
```javascript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({name: 'exponentialStrength'})
export class MultiplierPipe implements PipeTransform {
  transform(value: number, multiplier: 2): string {
    return value * multiplier;
  }
}
```
The above Pipe can be used as below,
```html
<span>{{ numberValue | Multiplier: 3 }}</span>
```

### Pure v/s Impure Pipe ?
Pure Pipe is called when Angular detects a change in the value or the parameters passed to a pipe (default).
```javascript
@Pipe({
  name: 'filterPipe', 
  pure: true
})
export class FilterPipe {}
```
Impure Pipe is called for every change detection cycle no matter whether the value or the parameters passed changes.
```javascript
@Pipe({
  name: 'filterPipe', 
  pure: false
})
export class FilterPipe {}
```

### What does async pipe in angular does ?
The async pipe subscribes to an Observable or Promise and returns the latest value it has emitted.

```javascript
 @Component({
  selector: 'async-promise-pipe',
  template: `<div>
    <span>Wait for it... {{ greeting | async }}</span>
    <span>Updated at {{ updatedTime | async }}</span>
  </div>`
})
export class AsyncPromisePipeComponent {
  greeting: Promise<string>|null = null;
  
  updatedTime = new Observable<string>((observer: Observer<string>) => {
    setInterval(() => observer.next(new Date().toString()), 1000);
  });
}
```
