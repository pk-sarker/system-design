### Proxies

A proxy server is an intermediate server between the client and the back-end server. 
Clients connect to proxy servers to make a request for a service like a web page, file, connection, etc. 
In short, a proxy server is a piece of software or hardware that acts as an intermediary for requests from clients seeking 
resources from other servers.

Typically, proxies are used to 
- filter requests, 
- log requests, 
- or sometimes transform requests (by adding/removing headers, encrypting/decrypting, or compressing a resource). 
- Cache: A caching proxy server can also improve web performance by caching frequently used pages so the user request doesn’t have to go all the way out to the Internet at large to get some of the data it needs to display a particular page.
- Batch requests
- Collapsed forwarding: enable multiple client requests for the same URI to be processed as one request to the backend server
- Collapse requests for data that is spatially close together in the storage to minimize the reads
- Security: A proxy server can also be used to beef up security for a business. A proxy server can provide network address translation, which makes the individual users and computers on the network anonymous when they are using the Internet. This makes it much harder for hackers to access individual computers on the network.

#### Proxy Server Types

**Open Proxy**\
An open proxy is a proxy server that is accessible by any Internet user. Generally, a proxy server only allows users within a 
networking group (i.e. a closed proxy) to store and forward Internet services such as DNS or web pages to reduce and control the 
bandwidth used by the group. With an open proxy, however, any user on the Internet is able to use this forwarding service.

**Reverse Proxy**\
A reverse proxy retrieves resources on behalf of a client from one or more servers. These resources are then returned to the client, 
appearing as if they originated from the proxy server itself. It typically sits behind the firewall in a private network and directs 
client requests to the appropriate backend server. A reverse proxy provides an additional level of abstraction and control to ensure 
the smooth flow of network traffic between clients and servers.

Common uses for a reverse proxy server include:

- **Load balancing**: A reverse proxy server can act as a “traffic cop,” sitting in front of your backend servers and distributing 
client requests across a group of servers in a manner that maximizes speed and capacity utilization while ensuring no one server 
is overloaded, which can degrade performance. If a server goes down, the load balancer redirects traffic to the remaining online servers.

- **Web acceleration**: Reverse proxies can compress inbound and outbound data, as well as cache commonly requested content, 
both of which speed up the flow of traffic between clients and servers. They can also perform additional tasks such as SSL encryption 
to take the load off of your web servers, thereby boosting their performance.

- **Security and anonymity**: By intercepting requests headed for your backend servers, a reverse proxy server protects their identities 
and acts as an additional defense against security attacks. It also ensures that multiple servers can be accessed from a single record 
locator or URL regardless of the structure of your local area network.
