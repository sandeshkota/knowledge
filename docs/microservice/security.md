### Defence in Depth
- A risk mitigation strategy wherein enough security practices are followed across the microservices archtecture to ensure even if one of the defence fails, the other will reduce the impact

## Security
- Every request from clietns should be routed through API gateway
  - since an application consists of several microservices, several ports are exposed, the risk are high and hence 
- API Gateway helps in single point of contact for the client and also helps in several other functionalities like,
  - Logging, authentication, authorization, etc..
- Types of API Gateway
  - Kong, Netfliw Zuul, Spring Cloud Gateway, NGINX

### Types of Authentication
- Basic Authentication
  - wherein username and password are Base64 encoded and added as part of header (username:password = gsiuda69sjhalkd8) ``` header[Authorization] = Basic gsiuda69sjhalkd8```
  - In this case the username and password are encoded and not encrypted
- Client Certificate Authentication (service to service)
  - A mechanism wherein the service to service communication happens as the certificates are shared in prior (* read more)
  - Through HTTPS (HTTP over TLS)
  - Mutual TLS, both have trusted certificates issued by trusted certificate authority
  - [Let's Encrypt](https://letsencrypt.org/), free certificate
- Token Authentication
  - Check with Identity server (ID server)
  - OAuth2.0
  - ByValue Token, a process wherein the service validaets the token without checking with the ID server (concept - uses public key to ensure that the token is from ID server)
  - Token should always have an expiry date
  - Evolution of Security Token (Kerberos, SAML, JWT)
- ID Providers
  - Keycloak, NGINX, Gluu, Cloud Foundry UAA
  - IDaaS -> okta, auth0


### Ways of authentication
- Token Relay, the same token is passed along the microservices and each microservice checks with ID server to validate
- Token Exchange, each service will exchange it's token with ID server for another token which is required by the next microservice in the request pipeline. Reduces the risk since the token is valid only within a limited boundary
- Attribute Based Access Control , based on certain conditions. like,  when (only business hours), where (blocked countries), how (desktop / mobile) & why (reason)
  - Ex: A doctor is allowed to view the patient's data for treatment only during working hours from a desktop located in the hospital
- Token revocation, a way of invalidating the token. If a token gets leaked, we can invalidate it in the auth server

### Service Mesh
- Why?
  - There are lot of things that should be taken care other than the core business logic in a microservice. like: authn, authz, logging, throttling, Ddos prevention, token revocation, etc..
  - These can be handled in a another container within a pod, called as side car, which is provided by Service Mesh
  - It can also help in service discovery, telemetry, load balancing, health check, circuit breaker, failover, etc..
