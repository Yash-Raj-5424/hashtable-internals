- when two keys produce same hash value, it results in collision. to resolve this we use chaining. 
- **Chaining** : form a cahin of keys that hash to the same slot. we put the colliding keys in a data structure that hold them well.
- most commonly we use **LinkedLists** for chaining
- the operations to perform are: adding a new key to LL, check is the key is present in the LL, remove a key from the LL
**possible implementations for insertion**
- insert at the **head** always => O(1)
- insert at the **tail** always => (can be O(1) if we keep a track of the tail always)
- insert as per **any order** => O(n), say sorted order

**for deletion and lookup**
- hash the key => arrive at the index => traverse the LL to do the operation 

**what if collisions are high**
- we first try to **resize** our array
- if resizing is not feasible, then we convert the LL to a self-balancing binary tree (Red-Black Tree) which gives O(N) lookups, insertions, deletions
- the RBT comes with its own trade-offs so we first try to see whether we can resize the array else we go for RBT.
