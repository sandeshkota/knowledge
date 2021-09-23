### Migrating from monolith
- Needs a systematic approach
- Eliminate Risk: Tansition to microservices must not impact customers and business negatively
- Control speed: Ability to pause, stop and slow down at any stage
- Build Confidence: confident with microservices and new tools

### Steps
- Start with a small step
- Get used to tools and process
- Ensure that even if you stop the transition in b/w, it should be a complete application with the business running as expected
- Avoid Big Bang

### Strangler Application Pattern
- Anology: Tree (onolith) to Strangler Fig (microservices)

![Strangler Fig Tree Image](https://www.tpisoftware.com/tpu/File/onlineResource/articles/1339/titlePageImg.jpg)
- DDD process, decide your domains and sub domains
- Start small, start building a small and less complex sub domain as a microservice. Ensure that everything else remains the same (request and response objects, etc..)
- Bring in a router component b/w client and server. Let the routing component redirect the client requests to either monolith or microservice based on the funcitonality requested
- Incase of failure in microservice, switch back to the monolith for all functionality
- Once enough confidence is built with the new microservice, remove that functionality from monolith and use the new microservice for realted functionality
- ensure that the new microservice is integrated along with the monolith (consider, data migration, data sync, communication, etc..)

### Steps
- Transform
- Co Exist
- Release Strategy
- Eliminate
- Rinse and repeat

### The Process
- Identify the first service (candidate)
  - Based on Actual usage (use metrics)
  - Simple to Refactor 
  - Presents minimal risk
  - reduce future releases
  - good test coverage
  - smaller to reduce work
  - larger to simplify integration
- Resolve Missing Dependencies
  - Microservice to monolith
  - Temporal Coupling
  - monolith to Microservice
  - Feature Toggle Pattern
  - Remove Temporal Coupling
    - Using Cache? (cache hit, cache miss, cache healer, default / error) 

### Patterns
- Branch by abstraction
  - define an interface which serves the functionality. Implement the interface and call the respective microservice 
- Routing Mechanism, based on
  - path of the request
  - content of the request 
  - Back to Front End can also serves the same purpose
  - Ex in cloud: Azure API Management service

### Communication
- Microservice uses an internal monolith capability
  - Refactor monolith capability (to an abstraction with a clear interface)
  - Expose monolith capability (using suitableset of interaction points)
  - Avoid monolith behavior changes
  - microservice has a copy of the abstraction (own copy of the monolith capability interface/abstraction)
  - microservice implementation of the abstraction (microservice calls monolith's new capability endpoint)
- Monolith needs to use microservice capability
  - production ready  (microservice must be production ready)
  - Capability abstraction (monolith's new implementation calls microservice)
  - Shared abstraction (calling client code cant tell the difference)
  - Avoid monolith behavior changes
  - Rollback mechanism (switch back to internal capability if microservice fails using a release toggle)
- Routing
  - Transparent routing (invisible to client and server side)
  - Scale out options (options to support multiple instances of services)
  - Transformation options (transform request and response if required)
  - Quick to revert back (configuration allows rerouting traffic back to monolith quickly)
  - Many options (HTTP reverse procy, custom and third party)

### Database decomposition challenges
- Database, NOSQL, Reporting, Relational, Auditing, Joins, Cascade deletes, referential integrity, cross bounded context tables, abstract tables, business logic in DB, Data culture change, denormalized tables, table triggers, data secutiry, distributed transaction patterns, distributed data consistency, ACID, eventual consistency, transactions, distributed data, shared data, performance of data in one place, caching strategies, DBA, DB as a service

### Implementation
- Build microservice
- add an abstraction layer for the functionality in monolith (if doesn't exist)
- implement abstraction layer and call respective microservice (ensure to uses its own SPs/Views for DB) 
- ensure feature toggle (for rollback) is implemented in case microservice doesn't work as expected
- implement routing logic (in API gateway OR BFF) which redirects traffic to monolith or microservice based on request path or request content
- segregate DB (lift and shift the views/SPs/Tables)
- Segregate the UI if needed (micro frontend)
- If monolith needs the new functionality, implement abstract layer in monolith and call the microservice
- If microservice needs the monolith functionality, implement abstract layer in monolith and expose it as an API and call this in microservice through an abstract layer 
- ensure that for a certain period of time both the functionalities works in parallel and can be switched to any approach using Feature Toggle
- Once we get confidence on the microservice, remove the logic from the monolith along with the feature toggle






