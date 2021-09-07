### Aggregator Pattern
- Whenever a client requires information from two or three services.  
- Bring an a Aggregator service which calls two/more services, gets data, combines and returns it to client

### API Gateway
- Proxy service to route a request to concerned service. Can also act as Aggregator service.
- Entry point for all the services
- Helps in dealing with multiple Protocols

### Chained / Chain of responsibility
- Produces a single output which is a combination of multiple service outputs
- Steps
  - ServiceA calls ServiceB, ServiceB calls ServiceC. 
  - ServiceB collects data from ServiceC and it's own response, combines them and sends it to ServiceA
  - ServiceA collects data from ServiceA and combines with its own response and sends it to Client
- Client waits for output as it has to collect from all three services

### Asynchronus Messaging Pattern
- Services can communicate with each other but not synchornously

### Database
- Database per service
- Shared database

### Event Sourcing
- Events are stored a a sequence of events in Event Store
- Helps in falling back to older event states

### Branch Pattern
- Simultaneouly process the requests and responses from multiple microservices

### CQRS Pattern
- Segregate the functionality into two parts 
  - Command: Handle requests of Create/Update/DElete
  - Query: Handle requests of Get

### Decomposition of Monolith
- DDD
- Strangler / Vine Pattern

### Service Discovery
Is a technique wherein a client will locate the service dynamically
- DNS: serves basic purpouse
- Apache Zookeeper
- Consul

### Other Factors
- Idempotence: Is primary concept for microservices
- Computing Availability: multiplication of all microservice availabilities in a particular functionality


### Communication
- RPC: One way - Request-Reply - Synchronous
- Message Bus: One Way - multiple consumers (loose coupling) - Faster (as the success is decided on publishing message to message bus) - easy to add/remove consumers - more load-it's queued - client down? the message will be queued in bus, sent/pulled when the client is up
```
// anatomy of a message
- Sample payload (business relevant information)
- Headers (TimeStamp, Sender Info, Correlation ID, Error handling info, Custom headers)
```

### Event Driven Architecture
A system which is driven by production, detection, consumption and reaction to events

### Developing a microservice
- Find the System Boundaries and data ownership
- Find the dependant systems
- Come up with Testing strategy (Testing Pyramid)
- Continous Delivery Techniques 
  - Versioning - URL, version number in messages, system should support both versions, old version decommision strategy
  - Feature Flags - requires testing both paths
- Automation mindset is very much needed (invest in tooling)
- Ubiquitous Language: Same language for everyone. Domain names, class names, etc..
- Ensure right amount flexibility is achieved: Too much flexibility is also not right choice. A certain level of rigidity is also important.
- Capacity: Know the microservice's limits
- Observability: Monitoring & Logging. Analyse telemetry data ( use correlation IDs)
- Handling failures: fault tolerance patterns (retry, circuit breaker, etc..)

### Deployment
- Blue-Green Deployment
  - In which a new set of PROD like infra is brough up with new functionality
  - Once tested and certified, change the loadbalancer configuration to point to this new service
  - Monitor for sometime and if everything is fine remove the old service OR use it as sStaging/Prod-Bis
  - Requires Prod like infra setup
- Canary Deployment:
  - In whhich the new functionality is released to a subset of users. All infrastructure in a target environment is updated in small phases (e.g: 2%, 25%, 75%, 100%)
  - Session affinity is aprt of the process
- A/B Testing
  - Is more of running two different functionalities and redirecting the users to any of these functionalities
  - The redirection can be independent of user / sessiona affinity can be maintained   

### Software Quality
- External (For users) - correctness, user experience, reliability, absence of errors, performance
- Internal (for devlopers) - maintainability, testability, observability, simplicity, extensibility


