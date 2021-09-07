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







