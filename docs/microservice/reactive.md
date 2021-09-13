### Reactive Manifesto
- Responsive: addresses systems ability to respond in a timely manner
  - request and response timings
  - latency
  - server and client metrics
- Resilient: ability to stay responsive in the event of failures
  - replication: multiple instances, distributed, load balancer (auto scaling)
  - containment & isolation: decoupling arch, containerization, louse coupling using messages
  - delegation:
- Elastic: ability to stay responsive in case of load
  - not scalability (scalability - handling increase load)
  - elasticity (handling in case of both increased and decreased load)
- Message Driven: loose coupling
  - non blobking
  - eventual consistency
  - ex: one way is HTTP callback, github - hooks



