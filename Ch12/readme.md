# Message Authentication Code 
They are used to satisfy the authenticity of message sender, that the sender of the message is an authentic party, but not identify him specifically.

Only those who own the shared key are considered authentic users, and so, symmetric key cryptography is the metthod used to generate message authentication codes.

They are like digital signatures but made using the shared key.

## properties of MACs
1. Arbitrary input sizes.
2. Fixed output size 
3. it guarantees the authenticity of the message sender.
4. Message integrity: manipulations during transition would be detected.
5. *Non repudiation?, we don't do that here*, the sender is authentic but not specified, both sender and receiver can generate the MAC and so it doesn't provide Non-repudiation service.

## MAC
it's just hashing using the shared key with the message "some how".  
we have two simple methods.

### Secret Prefix
Concatenate K as a prefix for x, and hash that. 
*MAC = h(K || x)*  

But, this method can be easily attacked, the hash function has an iterative nature, meaning  
*h<sub>i</sub> = H(h<sub>i-1</sub>, X<sub>i</sub>)*  
In this way The attacker can append more blocks to the message, and generate a valid MAC for to accomodate them as well.  
However this attack fails if padding with length data was used.

### Secret Suffix
Concatenate K as a suffix for x, and hash that. 
*MAC = h(x || K)*  

This method is as secure as the hash function used, it can only be attacked by finding a collision in the hash function, so it may not be secure with SHA-1 which now has collisions, SHA-2 may work, and it's best to stay safe and use SHA-3.

## Hash MAC 
it's used in both SSL and TLS.  
it uses both prefix and suffix approaches.  
![formula](https://render.githubusercontent.com/render/math?math=\color{green}\Large%20M%20=%20HMAC_{k}(X)%20=%20H((K^{%2B}%20\oplus%20opad)%20||%20H(K^{%2B}%20\oplus%20ipad)%20||%20X))  
Where:  
k<sup>+</sup>: is the extended key, padded with prefix zeros until it reaches block length.  
opad: outter padding, it's formed by repeating the byte 0x36 until we have a block size.  
ipad: inner padding, it's formed by repeating the byte 0x5C until we have a block size.  
and the block size is 512 bits.  