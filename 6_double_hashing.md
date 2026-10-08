- why do we need a linear/quadratic distribution at all ? it forms clustered collsions too which is bad
- so we use another hash function in order to reduce the clustered collisions
- the best thing is that it doesn't follow any particular pattern and gives near-uniform yet random offset from the primary slot of the key.

```
p(k, i) = (h1(k) + i*(h2(k)) )% m
```

**choosing the h2 (the second hash function)**
- it should never return 0
- it should cycle through the entire table (order doesn't matter)
- fast to compute and kinda similar to a random no. generator

**advantages**
- uniform spread upon collision
- no specific offset pattern - purely dependent on the key
- least prone to clustering problem