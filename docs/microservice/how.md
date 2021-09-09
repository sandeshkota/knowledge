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

### service interaction
- If a micro service communicates with another using it's IP address, then there will be a tight coupling and by changing the IP address of one will impact another one. Also if we spin up another container of same microservice it will be a challenge.
- DNS: Use a DNS instead. Let the DNS point to the load balancer which inturn shares the load among different microservice instances
- Kubernetes: Communicate using the name of the service. Kuberenetes will handle the communication. It can also load balance if needed. 
- Message Broker
  - Messages are not delivered in the same order. So ensure that the messages are treated as such
  - Same messages can be sent multiple times. So ensure that the message handlers are Idempotent  

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

### Distributed Tracing: Sending Correlation ID
- Create middleware which adds a correaltionID to the HTTP request context, if it doesn't exists (if exists in the request header, use the same)
```csharp
app.UseMiddleware<LogHeaderMiddleware>();  
```
- Override SendAsync() of RequestHandler and add the correlationID to the request header (ensure that you are using this for all HTTP requests)
```csharp
services.AddHttpContextAccessor();
```
- Read the CorrelationID from the request header and use it for logging

### Security
- Ensure that the access to the data is secure (allow only the services which are really needed)
- Ensure the network is secure. Use virtual networks, API Gateway, IP whitelisting and Firewall
- Ensure that the data in transit is encrypted (TLS, create SSL Certificates & manage may be a challenge - several vloud proviers help is easy manage)
- Ensure that the data in store is encrypted (adds an overhead of encrypting and decrypting the data - so plan for sesible data) (cloud providers provide this functionality)
- Ensure that the data backups are also encrypted (based on need and sensitive data)
- Use Key Valuts to store configuration data
- Secure communication b/w services
  - Use the right Authentication & Authorization (basic auth - loginID & Pwd, API Key, Client Certificate\, **OAuth 2.0**)
- Ensure that proper testing is in place to ensure security 
  - Penetration Testing
  - Automated Security Testing (to check allo and rejct of services)
  - Attack detection: Put proper process in place which helps you detect attacks as soon as possible (ex: DDOS attack)
  - Auditing (logging and monitoring): helps in tracing back who did what from where and how 

### API gateway
- Sits in b/w front-end and back-end. Communication b/w them happens via API Gateway.
- Benefits
  - separate out cross cutting concerns (Authentication, Authorization, SSL Termination, DDoS protection / Throttling) 
  - Routing ( redirect to right services based on request ex:URL)
    - Based on headers, paths, params, etcc.. Load Balancing , A/B Testing, Canary 
  - ~Aggregator (collects data from several services, collate and send)
  - Cache in API gateway
  - Handle requests based on the client (mobile - fast/low/summarized data from 1 service, desktop - slow/high quality/detailed data) 
  - Protocol updates. Let client communicate with API Gateway via HTTP2, let the rest communication be through HTTP1.1 or so
- Examples: AWS/Azure API gateway, Kong Gateway, Tyk API Gateway

### Service Mesh
- Remove the microservice challenges like hard coded reference b/w microservices (IP Addresses), 
- Implemet Sidecar (proxies) which acts as a microservice. Each service will have a sidecar and acts as a procy for a microservice. 
  - Sidecars are controlled by control tower, which manages service discovery, networking policies, traffic management, Load balancing, Certificates
  - Control Tower can help in canary release. whereing it redirects 1% of traffic to canary release and rest to old service
- Service Registry
- Service Discovery
- Examples: Hashicorp Consul, Istio, Kubernetes service mesh
![Kubernetes & Service mesh](https://cdn.thenewstack.io/media/2021/03/200a2844-image4.png)
