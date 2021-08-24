### What is Zone JS ?
A zone is an execution context that persists across async tasks. You can think of it as thread-local storage for JavaScript VMs

### What is NgZone
Helps in change detections. which is used to update angular bindings and several other functionalities

### Change Detection
Change detection - runs everytime something changes in angular. Suppose if a property/event is triggered for one component. Then the chage detection is triggered for all the components irrespective of whether it is needed or not.

### OnPush strategy
With this strategy, the template of the component will only be checked in 2 cases:
- one of the inputs of the component changed
- an event handler of the component was triggered

```javascript
import {ChangeDetectionStrategy, Component} from '@angular/core';

@Component({
  // ...
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class OnPushComponent {
  // ...
}
```
By doing this we are ensuring that change detection doesn't impact this component unless the above two cases are triggered


### RunOutsideAngular
Runs the logic that is specified outside angular change detection.
```javascript
@Component({})
export class SampleComponent {
  updated: boolean;
  
  constructor(private zone: NgZone){}
  
  // Do not Trigger Change Detection
  RunLogicWithoutChangeDetection() {
    this.zone.runOutsideAngular(() => {
       this.updated = true;
    });
  }

  // Trigger Change Detection
  RunLogicWithChangeDetection() {
    this.ngZone.run(() => {
        this.updated = true;
    });
  }
}
```
