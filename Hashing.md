# Hashing
Hashing is a technique of generating fixed-size values, _**hash value**_, from a given data. There is a function 
associated with hashing called _**hash function**_ that generates the fixed size value based on 
mathematical algorithm. These algorithms are called _**hashing algorithm**_. 
Time complexity of reading a value from hash table is _O(1)_.

![Hashing](./img/Hashing.svg)

A good hash function uses a one-way hashing algorithm, or in other words, the hash cannot be converted back into the original key.

### Collisions
Hash collision is a phenomenon where hash value of two different key/data are same.
Collision is not expected and there are ways to handle hash collision.

**Chaining** is one of the method to handle hash collision.  In _Chaining_ the idea is to keep collided hash values in a _linked list_.
The drawback with this is approach is that all the overhead now comes to linked list data structure. To retrieve any specific value of a key
whose hash value is collided we have to traverse the linked list, time complexity _O(n)_. 

![Hash Chaining](./img/HashChaining.svg)

**Rehashing**
In Rehashing it detects if a new hash value is collided or not. If it collides then the hash will point to a spot that has something already.
If collided it hashes the given key/data again and hope to land in an open space.
This rehash can be the same function or something different. As long as the order of hashing is followed, you will get to your desired entry.

**Linear Probing**
In Linear Probing it just add 1 and go to the next position if the first hashed location is taken (collision). 
The issue with this is with high load factors it can lead to clustering which induces collisions into other collisions.

**Quadratic Probing**
This is similar to linear probing except instead of adding 1 or going to the neighboring location you add a successive values of an arbitrary 
quadratic polynomial until an open slot is found. This leads to less primary clustering.

### Features of Hash Functions
The typical features of hash functions are −
**Fixed Length Output (Hash Value)**
- Hash function coverts data of arbitrary length to a fixed length. This process is often referred to as hashing the data.
- In general, the hash is much smaller than the input data, hence hash functions are sometimes called **compression functions**.
- Since a hash is a smaller representation of a larger data, it is also referred to as a **digest**. 
- Hash function with _n_ bit output is referred to as an _n-bit_ hash function. Popular hash functions generate values between 160 and 512 bits.

**Efficiency of Operation**
- Generally for any hash function h with input _x_, computation of _h(x)_ is a fast operation. 
- Computationally hash functions are much faster than a symmetric encryption.
### Properties of Hash Functions
**Pre-Image Resistance**
- it should be computationally hard to reverse a hash function. if a hash function h produced a hash value z, then it should be a difficult process to find any input value _x_ that hashes to _z_.
- This property protects against an attacker who only has a hash value and is trying to find the input.
**Second Pre-Image Resistance**\
- Given an input and its hash, it should be hard to find a different input with the same hash.
- This property of hash function protects against an attacker who has an input value and its hash, and wants to substitute different value as legitimate value in place of original input value.
**Collision Resistance**\
- it should be hard to find two different inputs of any length that result in the same hash. In other words, for a hash function _h_, it is hard to find any two different inputs _x_ and _y_ such that _h(x) = h(y)_.

### Types of hashing algorithms
There are multiple types of hashing algorithms.
The most common hash functions uses the following algorithms
- Message Digest 5 (MD5)
  - MD5 was most popular and widely used hash function for quite some years.
  - The MD family comprises of hash functions MD2, MD4, MD5 and MD6. It was adopted as Internet Standard RFC 1321. It is a 128-bit hash function.
  - In 2004, collisions were found in MD5, An analytical attack was reported to be successful only in an hour by using computer cluster.
- Secure Hashing Algorithm (SHA) 1, 2 and 3
  - Family of SHA comprise of four SHA algorithms; SHA-0, SHA-1, SHA-2, and SHA-3. Though from same family, there are structurally different.
  - The original version is SHA-0, a 160-bit hash function, was published by the National Institute of Standards and Technology (NIST) in 1993.
  - SHA-1 is the most widely used of the existing SHA hash functions. It is employed in several widely used applications and protocols including Secure Socket Layer (SSL) security.
  - In 2005, a method was found for uncovering collisions for SHA-1 within practical time frame making long-term employability of SHA-1 doubtful.
  - SHA-2 family has four further SHA variants, SHA-224, SHA-256, SHA-384, and SHA-512 depending up on number of bits in their hash value. No successful attacks have yet been reported on SHA-2 hash function.
  - Though SHA-2 is a strong hash function. Though significantly different, its basic design is still follows design of SHA-1. 
  - In October 2012, the NIST chose the Keccak algorithm as the new SHA-3 standard.
- [RACE Integrity Primitives Evaluation Message Digest (RIPEMD)](https://en.wikipedia.org/wiki/RIPEMD)
- [Whirlpool](https://en.wikipedia.org/wiki/Whirlpool_(hash_function))


### Hashing by data types

#### Integer data
There are several common algorithms for hashing integers. One of the simplest and most common methods in 
practice is the modulo division method.

**Identity hash function**:\
If the data to be hashed is small enough, one can use the data itself (reinterpreted as an integer) as the hashed value. 
The cost of computing this identity hash function is effectively zero. This hash function is perfect, as it maps each input to a distinct hash value.

**Trivial hash function**:\
If the keys are uniformly or sufficiently uniformly distributed over the key space, so that the key values 
are essentially random, they may be considered to be already 'hashed'. In this case, any number of any bits in the key may be dialled
out and collated as an index into the hash table. 

**Mid-squares**:\
A mid-squares hash code is produced by squaring the input and extracting an appropriate number of middle digits or bits. 
For example, if the input is 123,456,789 and the hash table size 10,000, squaring the key produces 15,241,578,750,190,521, so the hash code is 
taken as the middle 4 digits of the 17-digit number (ignoring the high digit) 8750. The mid-squares method produces a reasonable 
hash code if there is not a lot of leading or trailing zeros in the key.

**Division hashing**:\
A standard technique is to use a modulo function on the key, by selecting a divisor _M_ which is a prime number close to the table size, so _h(K)=K mod M_. 
The table size is usually a power of _2_. This gives a distribution from _{0,M-1}_. This gives good results over a large number of key sets. 
A significant drawback of division hashing is that division is microprogrammed on most modern architectures including x86 and can be 10 times slower than multiply. 
A second drawback is that it won't break up clustered keys. 
For example, the keys 123000, 456000, 789000, etc. modulo 1000 all map to the same address. 
This technique works well in practice because many key sets are sufficiently random already, and the probability that a key set will be cyclical by a large prime number is small.

There are other hashing as well, [Multiplicative hashing](https://en.wikipedia.org/wiki/Hash_function#Multiplicative_hashing), [Fibonacci hashing](https://en.wikipedia.org/wiki/Hash_function#Fibonacci_hashing), [Zobrist hashing](https://en.wikipedia.org/wiki/Hash_function#Zobrist_hashing).

#### Hashing variable-length data

**Middle and ends**:\
Simplistic hash functions may add the first and last n characters of a string along with the length, or form a word-size hash from the middle 4 characters of a string. 
This saves iterating over the (potentially long) string, but hash functions that do not hash on all characters of a string can readily become linear due to redundancies, 
clustering or other pathologies in the key set.

**Character folding**:\
The paradigmatic example of folding by characters is to add up the integer values of all the characters in the string. A better idea is to multiply the hash total by a constant, 
typically a sizable prime number, before adding in the next character, ignoring overflow.