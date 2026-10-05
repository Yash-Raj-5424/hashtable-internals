- store key-val pairs
- constant time insertion, deletion, lookups
- hashtables are also used as building blocks for constructing classes and its members, variable lookups
**two ideas to construct hashtables**
1. map application key to hash key
- we can't put anything as a key in hashtables like a list can't be a key in some languages.
- any custom type that implements the 'hash' function that returns an integer (hash key)
- **naive implementation:** use they hash value as an index of an array to store the value. 
- this could work only when hash key's range is small
- finding a chunk of memory for this array can be difficult
- many indices in the array would be empty (space wastage)
2. Mapping has key to smaller range
- say we wanna store 'k' keys and the array should be 'm' sized. so 'm' should be O(k)
- so hash key should be mapped to the range [0, m)
- if we add more keys to our hash table the holding array would have to be resized (twiced)
- the first step is simplifying our problem statmt for second step making it easier to optimize int => int distribution
- the 1st step also allows us to give great abstraction (object -> int) enabling us to support complex data types as keys