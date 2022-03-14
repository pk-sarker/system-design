# Code Deployment System

## Design a global and fast code-deployment system.


#### Clarifying Questions To Ask

1) A typical code deployment system contains many functionalities, like building code into binaries, testing and shipping code\
   which part of the system we are focusing.\
   **Response**: Design a system that takes code, builds it into a binary (an opaque blob of data—the compiled code), and deploys 
   the result globally in an efficient and scalable way. We don't need to worry about testing code; let's assume that's already covered.
2) When the code deployment system will trigger, which part of the software-development lifecycle it will be in. Is the process starts 
   when code is submitted for review or merged to the codebase.\
   **Response**: The process will trigger when code is merged into the master/main branch of a central code repository, developers should be able to trigger a build 
   and deploy that build. At that point, the code has already been reviewed and is ready to deploy/ship.
3) How we are shipping the code, are we shipping the code by sending the code to the application servers around the world?\
   **Response**: Yes.
4) Any idea about the number of machines we should be deploying each code? Is there any grouping/cluster or region?\
   **Response**: Approximately 7 to 10 regions that should cover the whole world, and thousands of machines in each region.
