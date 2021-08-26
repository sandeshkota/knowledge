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
  });
  
  it('should increment the input by 1 if it is positive', () => {
    const result = increment(1);
    expect(result).toBe(2);
  });

})
```

- Example 2
Code
```javascript
// vote.component.ts

export class VoteComponent {
  totalVotes: number = 0;
  
  upVote() {
    this.totalVotes++;
  }
  
  downVote() {
    this.totalVotes--;
  }
}
```

Test
```javascript
// vote.component.spec.ts
import { VoteComponent } from './vote.component';
  
describe('VoteComponent', () => {
  let component: VoteComponent;
  
  beforeEach(() => {
    component = new VoteComponent();
  });

  it('should increment totalVotes when upvoted', () => {
    component.upVote();
    
    expect(component.totalVotes).toBe(1);
  });
  
  it('should decrement totalVotes when downvoted', () => {
    component.upVote();
    
    expect(component.totalVotes).toBe(-1);
  });

})
```

###  Jasmine Test setup and Tear Down
```javascript

// suite
describe('VoteComponent', () => {
  beforeEach(() => {
    // runs before each test run
  });

  afterEach(() => {
    // runs after each test run
  });

  beforeAll(() => {
    // runs once before suite run
  });
  
  afterAll(() => {
    // runs once after suite run
  });

  // test
  it('should test', () => {
  });
})
```

- Example 3
```javascript
@Component({
  selector: 'lightswitch-comp',
  template: `
    <button (click)="clicked()">Click me!</button>
    <span>{{message}}</span>`
})
export class LightswitchComponent {
  isOn = false;
  clicked() { this.isOn = !this.isOn; }
  get message() { return `The light is ${this.isOn ? 'On' : 'Off'}`; }
}
```
Tests
```javascript
describe('LightswitchComp', () => {
  it('#clicked() should toggle #isOn', () => {
    const comp = new LightswitchComponent();
    expect(comp.isOn).toBe(false, 'off at first');
    comp.clicked();
    expect(comp.isOn).toBe(true, 'on after click');
    comp.clicked();
    expect(comp.isOn).toBe(false, 'off after second click');
  });
});
```

### Angular TestBed
The TestBed is the most important of the Angular testing utilities. The TestBed creates a dynamically-constructed Angular test module that emulates an Angular @NgModule.
Sample
```typescript
let service: ValueService;

beforeEach(() => {
  TestBed.configureTestingModule({ providers: [ValueService] });
});


it('should use ValueService', () => {
  service = TestBed.inject(ValueService);
  expect(service.getValue()).toBe('real value');
});
```

Mocking an object
```typescript
let masterService: MasterService;
let valueServiceSpy: jasmine.SpyObj<ValueService>;

beforeEach(() => {
  const spy = jasmine.createSpyObj('ValueService', ['getValue']);

  TestBed.configureTestingModule({
    // Provide both the service-to-test and its (spy) dependency
    providers: [
      MasterService,
      { provide: ValueService, useValue: spy }
    ]
  });
  // Inject both the service-to-test and its (spy) dependency
  masterService = TestBed.inject(MasterService);
  valueServiceSpy = TestBed.inject(ValueService) as jasmine.SpyObj<ValueService>;
});
```

Testing HTTP services
```javascript
let httpClientSpy: { get: jasmine.Spy };
let heroService: HeroService;

beforeEach(() => {
  // TODO: spy on other methods too
  httpClientSpy = jasmine.createSpyObj('HttpClient', ['get']);
  heroService = new HeroService(httpClientSpy as any);
});
```

### Sample Integration Tests
- Example 1
```javascript
describe('BannerComponent (minimal)', () => {
  it('should create', () => {
    TestBed.configureTestingModule({declarations: [BannerComponent]});
    const fixture = TestBed.createComponent(BannerComponent);
    const component = fixture.componentInstance;
    //  const bannerElement: HTMLElement = fixture.nativeElement;
    expect(component).toBeDefined();
  });
});
```

- Example 2
```javascript
@Component({
  selector: 'app-banner',
  template: '<h1>{{title}}</h1>',
  styles: ['h1 { color: green; font-size: 350%}']
})
export class BannerComponent {
  title = 'Test Tour of Heroes';
}
```
Test
```javascript
let component: BannerComponent;
let fixture: ComponentFixture<BannerComponent>;
let h1: HTMLElement;

beforeEach(() => {
  TestBed.configureTestingModule({
    declarations: [ BannerComponent ],
  });
  fixture = TestBed.createComponent(BannerComponent);
  component = fixture.componentInstance; // BannerComponent test instance
  h1 = fixture.nativeElement.querySelector('h1');
});

// create component doesn't bind data - so h1 will be empty
it('no title in the DOM after createComponent()', () => {
  expect(h1.textContent).toEqual('');
});

// by detecting changes - the data is bound
it('should display original title after detectChanges()', () => {
  fixture.detectChanges();
  expect(h1.textContent).toContain(component.title);
});
```

- Example 3 : Automate Change detection
```javascript
TestBed.configureTestingModule({
  declarations: [ BannerComponent ],
  providers: [
    { provide: ComponentFixtureAutoDetect, useValue: true }
  ]
});

it('should display original title', () => {
  // Hooray! No `fixture.detectChanges()` needed
  expect(h1.textContent).toContain(component.title);
});
```

### To fake/mock
```javascript
let userServiceStub: Partial<UserService>;

beforeEach(() => {
  // stub UserService for test purposes
  userServiceStub = {
    isLoggedIn: true,
    user: { name: 'Test User' },
  };

  TestBed.configureTestingModule({
     declarations: [ WelcomeComponent ],
     providers: [ { provide: UserService, useValue: userServiceStub } ],
  });

  fixture = TestBed.createComponent(WelcomeComponent);
  comp    = fixture.componentInstance;

  // UserService from the root injector
  userService = TestBed.inject(UserService);

  //  get the "welcome" element by CSS selector (e.g., by class name)
  el = fixture.nativeElement.querySelector('.welcome');
});

// UserService actually injected into the component
userService = fixture.debugElement.injector.get(UserService);

// UserService from the root injector
userService = TestBed.inject(UserService);
```

With Spy
```javascript
beforeEach(() => {
  testQuote = 'Test Quote';

  // Create a fake TwainService object with a `getQuote()` spy
  const twainService = jasmine.createSpyObj('TwainService', ['getQuote']);
  // Make the spy return a synchronous Observable with the test data
  getQuoteSpy = twainService.getQuote.and.returnValue(of(testQuote));

  TestBed.configureTestingModule({
    declarations: [TwainComponent],
    providers: [{provide: TwainService, useValue: twainService}]
  });

  fixture = TestBed.createComponent(TwainComponent);
  component = fixture.componentInstance;
  quoteEl = fixture.nativeElement.querySelector('.twain');
});
```

### Commands
Run tests ``` ng test ```  

Run test with code coverage ``` ng test --code-coverage ```
OR
angular.json configuration
```
"test": {
  "options": {
    "codeCoverage": true
  }
}
```

