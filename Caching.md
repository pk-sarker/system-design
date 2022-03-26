## Caching
Caching is a technique that stores a copy of frequently used data to fast storage that's located close to the application.
Caching is used to improve performance and scalability of a system.

Caching is most efficient for read heavy information, especially if all the following condition apply to the original data store
- data is relatively static, means update is not that frequent
- Reading data from original storage is slower than reading from caching store
- It's subject to a high level of contention
- It's far away when network latency can cause access to be slow
- 

Based on the nature of the application/service architecture there are different ways of caching. In <u>distributed
applications</u> there are two strategies:
1) Private caching: In private caching data is held locally in the machine where the application is running. Mostly used in
   in-memory to store the cache. Expecting the cache data size to be smaller, not highly increasing over time. 
2) Shared caching: In shared caching a common source that can be accessed by multiple processes and machines. 
   Multiple application can read/write to same cache, it's little slower than private caching. Considering the cache store
   is in-memory but there will be some time for network call as the shared cache store is not local to the app machine.


Caching is a temporary storage, it may store data for longer period of time but it is not a persistent service/storage.
So it will be safe to store important data that you can afford to lose in persistent storage.\
For dynamic data, data that changes frequently caching is not that useful. If actual/original data changes too frequently
then either the cache becomes stale/old quickly or the overhead of synchronizing the cache with original data store 
reduces the effectiveness of caching.

**Cache hit:**
A _cache hit_ means the data required to serve request is available in the cache and served from the cache.

**Cache miss:** 
A _cache miss_ means the data required to serve requests is not available in the cache and need to compute/get/retrieve
from original datastore/service/server.

![Caching Architecture](./img/Cache-architecture.png)


**Do we cache all data ?**
Mostly we don't cache all data of an entity at a time. Means, most frequently used data is cached. Data may loaded in caching
store iteratively, just before or as needed. For example, It doesn't make sence to keep all the message, pictures, posts of a 
social network user in cache, rather store the mostly used information, like, profile picture and other identity related information.

#### Caching strategies
### Cache Aside
In cache aside pattern data is loaded in to cache from data store on demand. This can improve performance and also helps 
to maintain consistency between data held in the cache and data in the underlying data store.

Process:
- On receiving request to serve any data, It first determine whether the data is currently available in the cache.
- If the item is not currently available in cache, read the data from the original data store.
- Store a copy of the item in the cache.

### Write through cache
In _Write through cache_, all the write/update happens in the cache first and then to the orginal data store. 
The cache has a writer component that can write to data store/database.
- The application receives request to write data to data store/database.
- The application writes the data to the cache.
- The cache invokes the writer to write to database as well as update the cache.


### Read through cache
In _Read through cache_ strategy, the cache contains a component that can load or read data from 
original data store/database.

- When the application receives the read request, it asks the cache for data associated with the key.
- If requested data found in the cache, cache hit, then the data is served from the cache.
- If requested data is not available/old/outdated in the cache, cache miss, then the cache invokes the loader 
   that fetches the data from the database, updates the cache, and serves the fetched data.
- The next time there is a read request for the same data, it’s served from the cache.

### Write back cache
This strategy is similar to [Write through cache](#write-through-cache) with the change that 
write to original datastore is not synchronous, cache service writes the data to datastore asynchronously.

- The application send write request to the caching server
- The cache server writes data to the cache, also keep the data in a buffer/queue to write to original database,
- The cache server send an acknowledgement back to the application after writing the data cache and buffer. At this 
point write to original database didn't happen.
- The cache internally maintains a buffer to save the writes.
- The cache asynchronously writes the data from the buffer to the database at a later point in time.
