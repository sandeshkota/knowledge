### What is a microservice ?
An architectural style to develop a singel application as a suite of small services, each running in its own process and communicates with light weight mechanisms (HTTP resources). 

Micorservices are small, autonomous services that work together.

- Set of practices to meant to increase the speed and effeciency of developing and managing software solutions ar scale (Technology agnostic). Principles and architectural. patterns.
- Does one thing (a business process)
- Micro: Scope of funcationalities
- Bounded Context (Sub Domain) - each as a microservice - independently deployable
- interoperability, message based communication (SOA - almost same concept)

### Different elements of Microservices
- Organization: Teams, structure, responsibility, interaction, etc..
- Data Store: each microservice can implement its own technology for storing data (Relational, Document, NoSQL, etc.) ( 1 DB / sub domain)
- Data Synchronization: The data that is shared across different microservices should be in sync and it can be achieved using Event Sourcing Pattern (kafka, RabbitMQ, etc..) (Immediate consistency , Eventual Consistency)
- UI: How to display data when it is being fetched by multiple microservices
- Communication: Direct (sync & async), Message / Event via Broker / Channel (Publish-Subscribe) (ex. Rabbit MQ), Expose Contract (Swagger)
- Service Registry: Each services should register themselves to Service Registry (since the IPs can be dynamic) (Ex: Eureka, ZooKepper, Consul)
- Service Discovery: The Clients goes through the Service Registry and explores the APIs available
- Circuit Breaker: Handling failures in one of the services. Handle through proxies. (Ex: Hysterix, JRugged)
- Gateway: Singel entry point for all clients. Handles request based on the type (redirects to right APIs) (Ex: Zuul Netty, Finagle)
- Secutiry: Use IAM. Gateway deals with IAM. (Ex: Kerberos, OAuth 2.0, OpenID)
- Scalability: Vertical & Horizontal Scaling, Clustering, Load Balancing
- Availability: Measured in 99.99% availability, Single Point of Failure, Scale horizontally and cluster (to remove SPOF), Rate Limiting (to reduce DOS attack impacts)
- Monitoring & Dashboard: Centralized monitoring is very important as there are many machines, services (ELK Stack)
- Health Check: On OR Off check
- Logging: Using correlation ID to make sense of all the logging that has been done in several services
- Deployment: Container Images (Ex: Docker, RKT). Container management (Ex:Kubernetes, Docke swarm, MESOS), Automated Deployment (Jenkins, teamcity, etc..)
- DDD: To come up with the boundary context, which in turn can be a microservice
- Mindset: No matter what you cannot avoid failure, but it is important to plan on how to deal with a failure
- 
### Benefits
- Focus on small functionality
- Defined ownership
- Easy for new people to understand and be productive
- Faster TTM
- Scaleable
- Embrace new technologies faster
- Reduced dependency on other service deployments
- Incase of performance tuning (small & flexible, experimentation, scalable)


### Challenges
- Maintainence challenge as there are many services interacting with each other
- Distributed Transaction is complex if there are more services
- Testing entire flow is difficult and so logging and monitoring plays a vital role
- Since each microservice has its own set of technologies, moving people across teams will be challenging & requires training
- Resolving issues if it cuts across multiple services
- UI design can be challenging as the client (or server) should aggregate data from several microservices and show it to the user
- Monitoring & Logging is very important aspect and are very much needed. Monitoring is also a challenge as there are many components to monitor. Logging should be aggregated.
- Communication b/w microservices happens over a network. So the network performance is also a major factor in designing a micro service. (So avoid chatty behavior)
- Cascading Failures - Because of microservice dependencies. There are several patterns to reduce the impact - Fault Tolerant Patterns.
- Automation mindset is very much needed as there are several microservices.




