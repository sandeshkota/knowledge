### Aggregation, Assocaition , Composition

### async - await? what happens if i ignore await ?
it basically fires and forgets

### Operator Overloading

### Method overriding and method hiding ?

### Extension methods ?

### How do extend a List<int> and add a multiply method ? Can you ?

### Generics ?
  
### Design Patterns in Angular
  
### Directive ?

### Services in Angular ? Singleton ?
  
### HTML 5 - new functionalities

### HTML 5 - deprecated functionalities

### IEnumerable v.s IEnumerator

### EF - several states ? 
Added, Modified, etc..

### JS - difference b/w named function and async function

### JS - Hosting ?

### JS - var v/s let ?

### Closure

### Ivy Engine

### AOT v/s JIT Compilers

### Jenkins - what are artificats

### Mocking ? Mocking libraries? Mocking static class ?
- Mocking
- Typemock, Moq, Rhinomock, etc.
- Static class can be mocked in Typemock
```csharp
// class
public static class MyClass [
  public static string Myfunction(){
    return "actual value";
  }
}

// mocking
Isolate.Fake.WhenCalled(() => MyClass.MyFunction()).WillReturn("mock");
```

### Cross Join, Full Join

### Indexes - How the non-clustered indexes work

### Singleton v/s Static class

### How do you remove if-else / conditional statements in Factory Design Pattern ?
  - Using the dictionary.

### Multicasting ?
  
### multi threading v/s asyn-await ?
  
### DockerFile ?
  
### Docker Compose ?
  
### Microservices ?
  
### Distributed transactions in Microservices ?

### .Net Core ? Other than cross platform, lightweight, better performance ?

### Kestrel Server ?
  
### Filters in MVC? .Net Core?
  
### Types of filters ? Before only ? Or after too ?

### use of Startup ?

### ConfigureService v/s Configure ?

### Difference b/w .Use() and .Run() in Configure ?
  
### CSRF Token ? Cross site Request Forgery
It is also called as Anti Forgery Token.   
- An attacked can ad a link and redirect to URL of his choice. And the server will never know since the link is as expected.
- To handle it, the server randomly creates and passes a token in the response and expects it to be there when a request is sent back. 
- Since the token is randomly geenrated the attacker cannot predict the token and insert a link.  
- Using this it ensures that the user is clicking on the link the server has sent and not something which is injected.
