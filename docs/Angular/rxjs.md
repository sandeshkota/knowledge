### What is reactive programming ?
Reactive Programming is programming with asynchronous data streams

### What are Observables ?
Angular makes use of observables as an interface to handle a variety of common asynchronous operations

### Observables v/s Promises
Observables can emit multiple values. Promises can return only value (resolve OR reject)
Observables are lazy - runs only when there is a subscription.
Observables are cancelable.
Observables can be sync and async. Promises are always async.


### RxJS
Is a library which helps implementing reactive programming in Angular


### Multicasting Observables


### Subjects in RxJS
- Regular Subject
- Behavior Subject
- Async Subject

### How do you handle errors with observables
``` CatchError() ```

### Operators in RxJS

#### Creation Operators:
These operators are used to create observables from various sources, such as arrays, promises, and events. Examples include of, from, interval, timer, and fromEvent.

**of** operator is used to create an observable that emits a sequence of values, in order, and then completes.
```
import { of } from 'rxjs';

const numbers = of(1, 2, 3, 4, 5);

numbers.subscribe(result => console.log(result));
// Output: 1, 2, 3, 4, 5
```

**from** operator is used to create an observable from an array, a promise, or an iterable object
```
import { from } from 'rxjs';

const numbers = from([1, 2, 3, 4, 5]);

numbers.subscribe(result => console.log(result));
// Output: 1, 2, 3, 4, 5
```

**interval** operator is used to create an observable that emits an incremental sequence of integers at a specified interval.
```
import { interval } from 'rxjs';

const numbers = interval(1000);

numbers.subscribe(result => console.log(result));
// Output: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, ...
```

**fromEvent** operator is used to create an observable that emits events from a specified DOM element.
```
import { fromEvent } from 'rxjs';

const button = document.querySelector('button');
const clicks = fromEvent(button, 'click');

clicks.subscribe(result => console.log(result));
// Output: MouseEvent { ... }
```

**defer** operator is used to create an observable that only gets created when it's subscribed to, allowing for the values to be generated on demand
```
import { defer } from 'rxjs';

const numbers = defer(() => {
  const random = Math.floor(Math.random() * 10);
  return of(random);
});

numbers.subscribe(result => console.log(result));
// Output: A random integer between 0 and 9
```

#### Transformation Operators: 
These operators are used to transform the emissions of an observable into a new observable. Examples include map, pluck, switchMap, mergeMap, concatMap, scan, and buffer.

**map:** This operator takes an observable and applies a function to each emission, returning a new observable with the transformed values.
```
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

const source = of(1, 2, 3, 4, 5);
const example = source.pipe(map(x => x * 10));
example.subscribe(console.log); // Output: 10, 20, 30, 40, 50
```
In this example, map is used to multiply each emitted value by 10, returning a new observable with the transformed values.


**pluck:** This operator takes an observable that emits objects and extracts a specific property from each object, returning a new observable with only those properties.
```
import { from } from 'rxjs';
import { pluck } from 'rxjs/operators';

const source = from([{ name: 'Alice', age: 30 }, { name: 'Bob', age: 25 }, { name: 'Charlie', age: 35 }]);
const example = source.pipe(pluck('name'));
example.subscribe(console.log); // Output: Alice, Bob, Charlie
```
In this example, pluck is used to extract the name property from each object emitted by the input observable, returning a new observable with only the name values.

**switchMap:** This operator takes an observable and returns a new observable that is based on the most recent emission of the input observable. This is often used to handle asynchronous operations that need to be canceled or updated based on a new input.
```
import { fromEvent } from 'rxjs';
import { switchMap } from 'rxjs/operators';

const button = document.getElementById('button');
const click$ = fromEvent(button, 'click');

const example = click$.pipe(
  switchMap(() => fetch('https://jsonplaceholder.typicode.com/posts'))
);

example.subscribe(data => console.log(data)); // Output: Array of post objects
```
In this example, switchMap is used to cancel previous HTTP requests and only emit the results of the most recent one, which is triggered by a click event.

**mergeMap:** This operator takes an observable and returns a new observable that emits the results of applying a function to each emission of the input observable. This is similar to map, but the output function returns another observable instead of a value.
```
import { fromEvent } from 'rxjs';
import { mergeMap } from 'rxjs/operators';

const button = document.getElementById('button');
const click$ = fromEvent(button, 'click');

const example = click$.pipe(
  mergeMap(() => fetch('https://jsonplaceholder.typicode.com/posts'))
);

example.subscribe(data => console.log(data)); // Output: Array of post objects
```
In this example, mergeMap is used to create a new observable for each click event, emitting the results of all HTTP requests.


**concatMap:** This operator takes an observable and returns a new observable that emits the results of applying a function to each emission of the input observable. However, it waits for each inner observable to complete before emitting the next one.
```
import { of } from 'rxjs';
import { concatMap, delay } from 'rxjs/operators';

const source = of(1, 2, 3);
const example = source.pipe(
  concatMap(value => of(value).pipe(delay(1000)))
);

example.subscribe(console.log); // Output: 1, 2, 3 (with a 1-second delay between each)
```
In this example, concatMap is used to emit the results of each inner observable in order, waiting for each one to complete before emitting the next one.


**scan:** This operator takes an observable and applies an accumulator function to each emission, returning a new observable with the accumulated values.
```
import { of } from 'rxjs';
import { scan } from 'rxjs/operators';

const source = of(1, 2, 3, 4, 5);
const example = source.pipe(scan((acc, curr) => acc + curr, 0));
example.subscribe(console.log); // Output: 1, 3, 6, 10, 15
```
In this example, scan is used to accumulate the values emitted by the input observable, returning a new observable with the running total of the values.


#### Filtering Operators: 
These operators are used to filter the emissions of an observable based on certain criteria. Examples include filter, distinct, take, skip, debounceTime, and throttleTime.


#### Combination Operators: 
These operators are used to combine multiple observables into a single observable. Examples include merge, concat, combineLatest, zip, and race.


#### Utility Operators: 
These operators are used for various purposes, such as debugging, error handling, and metadata retrieval. Examples include tap, catchError, retry, finalize, and materialize.


#### Multicasting Operators: 
These operators are used to multicast the emissions of an observable to multiple subscribers. Examples include share, publish, publishReplay, and shareReplay.

