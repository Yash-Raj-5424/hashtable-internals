- **linear probing** - say the hash of ur application key landed at an index that is already occupied, so in open addressing we tend to find empty slots, when we use linear probing we just keep moving right to this index in order to find the empty slot, once u reach the extreme right, we circle back and search on the left of this index from start
- for **lookups** say we land at an index, if the key isn't the one, we start moving right to search, if we find it we return. else: if we encounter an empty slot while lookup, it means the key itself isn't present in the table otherwise it must've been placed on some slot while inserting. so stop the traversal once u find an empty slot while lookup.
- do **soft-delete** for deletion of keys

**why so fast**
- we're using **locality of reference** i.e, say u access a[i] then the page is cached on CPU and that page contains neighboring elements. so subsequent accesses are served from CPU cache => about constant time

> Linear probing gives a constant time performance. In average case the collisions are rare

**challanges**
- a bad hash function wouldn't uniformly distribute the keys in the array. **MurmurHash** is preferred
- **clustered collisions** a prior key having more collision affects the nearby keys. so we see clustered keys sitting nearby. same stuff our **hash function should be good and uniform.**