- resizing is imp. to maintain a consistent perf.
- pef degrades as load factor increases (longer lookups, multiple collisions)
 **resizing the chained hash tables**
 - we need to know the load factor of the hashtable to decide when to resize (we must konw keys in the table and size of the array)
 - for expanding, whenever alpha(load-factor) >= 0.5 we call the resize() method. [implementation we'll see later]
 - for shrinking, we call the resize whenever the alpha < 0.125

 > we keep counting the key_count and calculate the alpha at each step whenever a key is inserted or removed and resize accordingly

> 3 operations that we perform everytime we resize: create a new array of desired size, insert all the keys in the new array, delete old array once inserts are complete

- two ways to create the new array in resizing:
1. re-insert all the existing keys in the new one(with the LL nodes all-together. i.e, re-allocating the nodes again) => simple but expensive
2. instead of reallocating the LL nodes, just adjust their pointers => slightly efficient

**resizing in open addressing hash tables**
- we always soft delete the elements so that we can reach the keys further in the collision chain
- hence when a key is deleted from the hashtable here, we **CAN'T** reduce `key_count`
- the soft deleted keys also slow down the lookups as we have to go through them to access our desired key
- to handle this: 1. we'd have `active_keys_count` that we incr and decr accordingly on insert and delete 2. keep a counter for actual slots occupied so on insert, we incr the `used_slots_count` but on delete, we keep it as is (as the slot is still in use though the key's been soft deleted)
- so in this case, the alpha would be calculated as (used_slots_count/array_size) => this ensures we're accounting for the soft deleted keys too
- so when resize is trigerred, we only rehash the active-keys and skip the soft-deleted ones and once those are inserted in the new array, we set the `used_slot_count` equal to `active_keys`
- similarly on shrinking we do the same stuff => rehash only the active-keys and set the `used_slot_count` to `active_keys`