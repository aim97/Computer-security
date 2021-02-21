# Hashing 
A function that extracts the fingerprint of a given input sequence usually a file.  
or in other words for a given input sequence x, a hash function should generate an output h , called a digest, that is "unique" to x.

## Requirements of Hash Function
A hash function must satisfy some properties.
1. The input can have any length.
2. the output is fixed length.
3. **efficient**: *h(x)* is easy to compute.
4. **Preimage search**: it's practically infeasible to find a value x that has a given hash value h.
5. **Second preimage search**: it's practically infeasible to find a message x<sub>2</sub> that has the same hash as a message x<sub>1</sub>.
## Birth day paradox
## SHA-3