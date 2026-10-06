- **open addressing** is the space efficient approach to conflict resolution. it doesn't require an auxiliary data structure to store the collided keys instead we use the empty slots in the array itself
- to find the slots, we use **probing**.
- probing uses attempts to find the empty slots => make 'x' attempts for an 'x' sized array, if u find an empty slot, place it there else reject the write or replace an other key
- now that we're trying to find the empty slot in the array, our probing funxn must be good and deterministic enough to cover all the indices => it should generate permu of the numbers [0, n-1] to cover the entire array **eventually**

- **insertion** - using probing we try to find empty slots to insert into the array
- **lookup** - similar to insertion, we use probing to find the the key. worst case, key doesn't exist
- the iteration stops when we find the key, or we hit an empty slot, or we've iterated over all the slots in the array
- **deletion** - we first hash the key then apply probing function and delete the key. but how - **soft delete or hard delete ?** 
- with soft delete, we just mark the slot as free
- with hard delete, we've removed the key totally, so if u want to lookup the key next, u'd never be able to do so.
- it's recommended to use **soft deletion** i.e, freeing instead of deleting

- **limitation of probing** - we can only have as many keys as the size of the array