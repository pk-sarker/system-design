# HyperLogLog
HyperLogLog is an algorithm for the _count-distinct problem_, approximating the number of distinct elements in a multiset. 
Calculating the exact cardinality of a multiset requires an amount of memory proportional to the cardinality, which is 
impractical for very large data sets. For instance, for a set of _8_ numbers, _{4,3,6,2,2,6,1,7}_, the cardinality 
of the membership set would be 6.

HyperLogLog is most useful for large datasets, for instance, reporting the number 
of searches on Google performed by end users within a day. Trying to pull all of the searches into memory to work with 
them would be impossible because the memory required would be proportional to the number of Google searches in a day. 
HyperLogLog converts the data into a hash of random numbers representing the cardinality of the data supplied, solving 
this problem with as little as <i>1.5kB</i> of memory.

The _count-distinct_ problem is the problem of finding the number of distinct elements in a data stream with repeated elements.

The key concept behind this algorithm is that if we count the maximum number of leading zeros in the set items 
(hashed to uniform random numbers and represented in binary), we can estimate the number of unique items with a simple calculation.

If the maximum number of leading zeros is _n_, the estimated cardinality of the set is <i>2<sup>n</sup></i>.

![HyperLogLog](./img/HyperLogLog.png)


Let's take a example and solve it with HyperLogLog algorithm.

**Problem statement:**\
The problem is the find approximate number of unique users connected to a website at a moment. 
Each user is identified by a unique `UserId`. 

**Bruteforce solution:**\
Maintain a table for user connection in database with `UserId` and `Status`, may be some other optional information like device type(mobile app, browser, timezone).

*Connections* Table

| User ID | Device | Timezone | Status | 
|---|---|---|---|
|1234|Chrome|2022-03-28T02:11:28.826Z| Active|
|1235|Mobile App|2022-03-28T02:11:28.826Z| Active|
|1236|Chrome|2022-03-28T02:11:28.826Z| Active|
|1234|Chrome|2022-03-28T02:11:28.826Z| Active|

We can used a distinct query to count unique users, 
```sql
SELECT count(distinct(User ID)) From Connections where Status='Active'
```

Considering single database with large number of users, It has to check every entry which is the number of connection.\
So if there are _n_ connection the time complexity will be _O(n)_. And also the database engine has to keep the users ids in 
a set/hash map to find all the unique users. So the space complexity will be _O(n)_ where _n_ is the number of unique users.
So the time complexity and space complexity is _O(n)_.




**TODO**\
Let’s assume that we need to count the unique visitors for a web page, and that we have a large set containing IP addresses of all requests.


- Step 1: We will first convert the input IP addresses to a set of uniformly distributed random numbers using a Hash function. The cardinality doesn’t change here as only the IP addresses are converted to uniformly distributed random numbers. 
- Step 2: These random numbers are divided into different subsets using the initial few bits. The number of maximum leading zeros, within its values, are stored in memory. 
- Step 3: We calculate the harmonic mean of estimates for all the previously computed subsets. 
- Step 4: The harmonic mean computed above is an estimation of the unique visitor count on the web page.





For More on HyperLogLog read _Philippe Flajolet_ [paper](http://algo.inria.fr/flajolet/Publications/FlFuGaMe07.pdf).
