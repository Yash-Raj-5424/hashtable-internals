- we need to quantify how full the table is. this is called the **Load factor**
- Load factor is `n/m` where, n is no of keys in the table and m is the size of the array
- with chaining, we never fill the table but with open addressing, we would eventually run out of space and writes would fail.
- with chained hashing, load factor is avg no of elements stored per linked list. time to resolve collision = O(1+alpha) => 1 for adding a node and alpha for traversing the list
- with open adressing, collisions interfere -> collisions on one slot will interfere with probe begining on other
- the no. of probes required to find an empty slot increases exponentially with an increase in misses
**the probing is costly:**
- with chaining the linear traversal of LL and random memory access of LL nodes (also not cache friendly)
- with double hashing it requires us to evaluate two hash functions -> CPU intensive and time consuming and random jump in array (not cache friendly)

- optimal strategy depends on the use-case. so tune and evaluate

**how to compare and benchmark**
- we should analyze and benchmark our implementation
- the best metric to keep in mind while benchmarking can be **lookup time as a function of load**
- create a table of size 1024 -> insert n elements varying 32 to 900 -> lookup random 1000 keys (high miss ratio)
- we should see: perf for open addressing degrades as alpha tends to 1 (no of elements tends to be equal to slots in the array), chained approach degrades gracefully (cz always adding to an aux data structure and we have good space to put the keys), linear probing would be slower than double hashing (clustered collisions in linear probing so more lookups), probes of doulbe hashing would be shorter per collison

> but we can't claim that chaining is better than open addressing cz chained hashing is not very cache friendly

- but when tables are short, we don't see impact of caching

**better cache perf in chained hashing**
- to leverage CPU cache in chained hashing -> we allocate chunk of LL nodes (common allocation) instead of one new node everytime. so those slots would be cached in the CPU cache. 
- i.e, we use LL of arrays for common allocation

> chained hashing outperforms open addressing when tables are shorter and open addressing outperforms chained hashing when tables are larger

- so always experiment with different strategies, parameters, and algos based on ur use-case.
