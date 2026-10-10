- perf of hashtable degrades as load factor incr and hence to maintain the perf we've to resize it
**when to resize?**
- when load factor is **too high**.
- we mustn't be too aggressive nor too lineant
- a common decision is to resize when alpha = 0.5 i.e, array is half filled

**how to resize?**
- create a new array, copy elems from old to new, delete old arr (also re-hash the keys)
- time to resize is prop to keys present in the arr
- a typical strategy is to always double the arr
**why do we always double while resizing ?**
- say we don't double, instead we incr by 1 and add the key, so for n keys to be added, we need to resize the array each time by increasing 1 => total ops would be n(n-1)/2 => O(n^2)
- but what happens when we double ? let's see: say we had an array of len n/2 and (n/2)-1 elems were filled already, when we're filling the last elem into this, we resize right then. so filling the last elem is 1 op, and when we doulbe it, we copy the n/2 elems to the new array that gives n/2 ops for copying plus the n ops for doubling the array and finally when we go from n to 2n, same things happen again. adding these ops give the ops as O(n)
- this always holds when the resizing factor is greater than 1 i.e, it is O(n)

**why hashtable array is always a power of 2 in length ?**
- hash table works on hash functions i.e, => key -> hash -> mod with the length to get the index
- MOD operation is imp as it bounds the outpupt from hash function to a range that fits in arr
- but MOD is really expensive => internally it does division and captures the remainder
- can we get same result without using MOD ?
- what if we do AND(m-1) instead of MOD(m) given that m is power of 2
- yes, doing AND(m-1) instead of MOD(m) gives the same result. also AND is more efficient than MOD
- 2^k - 1 has lower bits 1 and higher bits 0
- AND acts as a filter -> zeros keep the results bounded and ones percolate the set bits

**shrinking a hashtable**
- if keys are deleted from the hashtable, it doesn't make sense to keep the table as it is
- so we need to shrink it. but when ?
- we should shrink only when a few more inserts after shrinking won't trigger the resize of the array

> maan lo tumne shrink kr diya, fir kuch 2, 3 insertions hue aur tumhe fir resize krke incr krna pd gya => perf to degrade hoga na....

- **by calculations** - we should shrink the array when there are only n/8 elements/keys left in the array
