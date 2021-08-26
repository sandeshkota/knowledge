### Types of Testing in Angular
- Unit Testing : Testing the unit in isolation. By faking it's dependents
- Integration Testing : Testing the component along with it's view. By faking the other dependents
- E2E (End to End) Testing : Testing the application as a whole, like an end user interaction.

### Testing Libraries for Angular
- Unit & Integration Tests: Jasmine Testing Library & Karma Test Runner
- E2E Tests: Protrator library
- Assertion libraries: There are several assertion libraries we can use, which helps in asserting a particular behavior. Most common one is Chai.js

### Sample Unit Tests

- Example 1  
Code 
```javascript
// math.ts
export function increment(value: number): number {
  if (value < 0) {
    return 0;
  }
  
  return value + 1;
}
```
Test
```javascript
// math.spec.ts
import { increment } from './math';

describe('Increment', () => {

  it('should return 0 if input is negative', () => {
    const result = increment(-1);
    expect(result).toBe(0);
  })
  
  it('should increment the input by 1 if it is positive', () => {
    const result = increment(1);
    expect(result).toBe(2);
  })

})
```

- Example 2
Code
```javascript
```

Test
```javascript
```
