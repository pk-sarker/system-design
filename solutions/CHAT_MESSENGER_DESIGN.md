# Design messaging service

### Design a chat messaging service like Facebook/Whatsapp

#### Things to know
* **What is a chat messaging service?**\
    A chat messaging service is a software that provides text, image or mix content messaging service to its user. Basically user A sends message to user B and user B sends message to user A.


### Requirement / Goal / Features
**Functional Requirement**\
The system should support:
* One-to-one messaging
* Group messaging, 
* Message state/status: Sent, Delivered, Read
* User status: online or offline
* Persistent storage of chat history

**Non-Functional requirements:**\ 
* Users should have real time chat experience with the lowest possible latency.
* The system should be highly consistent, user should see the latest messages in all connected devices
* The system should be highly available. 

### Capacity estimation
User size, Daily active user: `500 Million`\
Average message sent by each user: `40 message / day`\
So, total number of messages/day : `500 Million * 40` = `20,000 Million = 20 Billion`\

Write and Read per second = `20 Billion message / 24 * 3600 = 230000 / second` 

**Storage**:\
Average size of each message(without images): `120 byte`\
Storage required each day: `20 Billion message * 120 byte = 2.4 TB/day`\
If we are looking for storing the chat history for 10 years then we will need: `2.4 TB * 30 day * 12 * 10 = ~8600 TB = 8.6 Petabyte`. This estimation is without considering increasing users, average message/day, other metadata information.\

**Bandwidth**\
Network bandwidth will be more for group messaging, for simplicity lets estimate one-to-one messaging.

There are `2.4 TB` data generated each day, so incoming data rate: `2.4 TB / 24 hour * 3600 second = 27 MB/sec.` If each message is sent to one user and read only once then we need to add `27 MB/sec`.

### High Level Design

 






