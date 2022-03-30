# Bloom Filter

Bloom filter is a space-efficient probabilistic data structure, that is used to test whether an element is a member of a set.
Another way we can say that Bloom filter is used to quickly find if an element might be present in a set.

False positive matches are possible, but false negatives are not – in other words, a query returns either "possibly in set" 
or "definitely not in set". Elements can be added to the set, but not removed (though this can be addressed with the 
counting Bloom filter variant); the more items added, the larger the probability of false positives.

An empty Bloom filter is a bit-array of _m_ bits, all set to _0_. 
There are also _k_ different hash functions, each of which maps a set element to one of the _m_ bit positions.

![Bloom Filter](./img/BloomFilter.png)
