- linear probing suffers from cascading collisons (clustered collisions) => a key with more collisions tends to push the new key forward in the array
- we use an **arbitrary quadratic function**. this would reduce forming of clusters nearby.
- how is it better than linear probing - the next slot to put the collided keys are quadratically away.

```
p(k) = h(k) + i^2 for ith collision
```

**properties of quadratic probing**
- it reduces clustered collisions
- has a good locality of reference but not as great as that of linear probing
- unless there are large collisions on the same key, the CPU cache is utilized pretty well.
