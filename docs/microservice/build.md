### Concepts
- Each microservice can be built with it's own technology stack. But it is good to standardise as the same team will be working on several microservices
- Backend for Frontend = API Gateway = Service Layer
  - Never put business logic
- Ensure one signle microservice should not manage too many responsibilities
- Avoid chatty services (message bus reduces this challenge)

### Domain Driven Design
- Domains and Sub Domains (Bounded Context)

### Service Responsibilities
- Incoming Requests
  - HTTP
  - Messages
- Domain Logic
  - Patterns
    - Transaction Script (Simple)
    - Domain Model (DDD - Object oriented approach)
    - Table Module 
- Data access
  - Patterns
    - ORMs (easier to deal with data)
    - Document Database (whole document updates) (limited support for joins)
    - CQRS (Command Query Responsibility Segregation)
    - Event Sourcing (All actions are stored as events - can be replayed) (eventual consistency)
  - Queries
  - Updates
- Integrate
  - HTTP
  - Messages
  - Third party services 





