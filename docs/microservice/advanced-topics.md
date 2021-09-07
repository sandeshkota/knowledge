### Service Registry & Service Discovery
All services (instances) that are running registers its IP address to a centralized registry called as Service Registry. 
Ex: 
- Consider there are two services A & B. 
- A & B both registers it's IP addresses with a Service Registry _( A = [IP1, IP2]   , B = [IP3 , IP4, IP5, IP6] )_ **SERVICE REGISTRY**
- A wants to communicate with B and it doesn't know the IP address of B as there are several instances.
- A goes to service registry asks for B's IP address
- Service Registry returns B one of B's IP addresses (ex: IP5) **SERVICE DSICOVERY**
- A uses the IP5 and communicates with Service B

### Service Segmentation
- Limiting the access to services for certain allowed services

### Tools to handle these
- HashiCorp's Consul

