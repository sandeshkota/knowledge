### Dependency Injection (DI) ?
Dependency Injection is a design pattern in which a class asks for it's dependencies from external sources rather than creating itself.  

### Explain DI in Angular
DI in Angualr is hierarchial. Angular resolves depdendency from bottom-down approach. 
- First it checks for dependency within itself (component, directive etc..)
- Then it checks for it's parent class for dependency (parent component, parent directive etc..)
- Then it checks for dependency in it's module
- Atlast it will inject Null if it cannot resolve

### What are resolution modifiers in Angular DI ?
- @Optional : If angular couldn't resolve the dependency, it will inject null (so it shoulf be handled before using)

```javascript
@Injectable({ providedIn: 'root' })
export class UserService {
  GetUsers() { }
}

@Component({
  selector: 'app-content',
  templateUrl: '',
  styleUrls: []
})
export class AppComponent {
  constructor(@Optional private userService: UserService) {}
  
  public GetUsers() {
    if(this.userService !== null)
    {
        this.userService.GetUsers();
    }
  }
}
```

- @Self : Looks within it's own class to resolve the dependencies

```
@Component({
  providers: [ UserService ]
})
export class AppComponent {
  constructor(@Self private userService: UserService) {}
}
```

- @SkipSelf : Skips Looking it's own class to resolve the dependencies and instead goes through the hierarchy to resolve.

```
@Component({
  providers: [ UserService ]
})
export class AppComponent {
  constructor(@SkipSelf private userService: UserService) {}
}
```


- @Host : Looks to resolve the dependencies from the View (template / html) perspective.

```
@Component({ })
export class AppComponent {
  constructor(@Host private userService: UserService) {}
}
```


### What are Dependency Providers ? Types ?
- UseClass
- UseExisting
- UseValue
- UseFactory

### What are Dependency Injection Tokens ?
