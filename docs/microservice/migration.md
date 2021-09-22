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
- DDD process, decide your domains and sub domains
- Start small, start building a small and less complex sub domain as a microservice. Ensure that everything else remains the same (request and response objects, etc..)
- Bring in a router component b/w client and server. Let the routing component redirect the client requests to either monolith or microservice based on the funcitonality requested
- Incase of failure in microservice, switch back to the monolith for all functionality
- Once enough confidence is built with the new microservice, remove that functionality from monolith and use the new microservice for realted functionality
- ensure that the new microservice is integrated along with the monolith (consider, data migration, data sync, communication, etc..)
