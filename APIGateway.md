### API Gateway
An API gateway is an API management tool that sits between a client and a collection of backend services.

An API gateway is a layer 7 (HTTP) router that acts as a reverse proxy to accept all API calls, aggregate the various services required 
to fulfill them, and return the appropriate result.

With an API gateway, one simply exposes and scales a single collection of services (the API gateway) and updates the API gateway’s 
configuration whenever a new upstream should be exposed externally.

Exactly what the API gateway does will vary from one implementation to another. 
Some common functions include _**authentication, routing, rate limiting, billing, monitoring, analytics, policies, alerts, and security**_.

**Important use cases**:\
- **Authentication**: An API Gateway can take the overhead of authenticating an API call from outside. which can remove the check of 
security and lowering the network latency.
- **Load Balancing**: The API Gateway can work as an L7 load balancer to handle requests in the most efficient manner. It can keep a track of the request load it has sent to different nodes of a particular service.
- **Service discovery and requests dispatching**: It can make the communication between client and Microservices simpler. It hits all the required services and waits for the results from all services. 
After obtaining the response from all the services, it combines the result and sends it back to the client. An API Gateway can record the basic response time from each node of a service instance. For higher priority API calls, it can be routed to the fastest responding node.
- **Response transformation**: Being a first and single point of entry for all API calls, the API Gateway knows which type of client is calling: mobile, web client, or other external consumers; 
it can make the internal call to the client and give the data to different clients as per their needs and configuration.
- **Circuit breaker**: To handle a partial failure, the API Gateway uses a technique called circuit breaker pattern, which means that after a specific threshold, the API gateway will stop sending data to the component failing. This gives time to analyze the logs, implement a fix, and push an update. Or if necessary close the circuit until the issue is solved.

