# Long-Polling
Long Polling is the mechanism where the client requests the server for a resource and waits for the server. 
The service may not have the resource that has been requested, as soon as the resource is available server send the response back.

In long polling connection between client and server persist for longer period of time. The server 
does not close the connection once it receives a request from the client. Instead, the server responds only 
if any new message is available or if a timeout threshold is reached. Once the client receives a response, 
it immediately sends a new request to the server to have a new pending connection to send data to the client, 
and the operation is repeated. With this approach, the server emulates a Realtime Server Push feature.

Ideal candidate of long polling will be a situation where client makes frequent request to the server for 
data/new data and data may not available at the moment but it may be available in near future time. So 
consider a case where client is asking for new data every 5 second and data is not available, so everytime 
server has to send empty response back. For a longer period of time there will lot of processing at server side
when no data is available. 

Making repeated requests to a server wastes resources, as each new incoming connection must be established, 
the HTTP headers must be parsed, a query for new data must be performed, and a response (usually with no new data to offer) 
must be generated and delivered. The connection must then be closed, and any resources cleaned up. 
Rather than having to repeat this process multiple times for every client until new data for a given client becomes available, 
long polling is a technique where the server elects to hold a client’s connection open for as long as possible, 
delivering a response only after data becomes available or a timeout threshold has been reached.

[More on Long-Polling](https://ably.com/topic/long-polling)


