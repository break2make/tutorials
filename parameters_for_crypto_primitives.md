

## HMAC Parameters

_"In cryptography, an HMAC (sometimes expanded as either keyed-hash message authentication code or hash-based message authentication code) is a specific type of message authentication code (MAC) involving a cryptographic hash function and a secret cryptographic key. It may be used to simultaneously verify both the data integrity and the authenticity of a message, as with any MAC. Any cryptographic hash function, such as SHA-256 or SHA-3, may be used in the calculation of an HMAC; the resulting MAC algorithm is termed HMAC-X, where X is the hash function used (e.g. HMAC-SHA256 or HMAC-SHA3)."_ https://en.wikipedia.org/wiki/HMAC

>**The cryptographic strength of the HMAC depends upon the cryptographic strength of the underlying hash function, the size of its hash output, and the size and quality of the key.** It is suggested to select minumun of these values (in bits)

>**How does it work?**
- HMAC uses two passes of hash computation. The secret key is first used to derive two keys – inner and outer. The first pass of the algorithm produces an internal hash derived from the message and the inner key. The second pass produces the final HMAC code derived from the inner hash result and the outer key.
- An iterative hash function breaks up a message into blocks of a fixed size and iterates over them with a compression function. For example, SHA-256 operates on 512-bit blocks. The size of the output of HMAC is the same as that of the underlying hash function (e.g., 256 and 1600 bits in the case of SHA-256 and SHA-3, respectively), although it can be truncated if desired.
- RFC2104 requires that "keys longer than B bytes are first hashed using H" which leads to a confusing pseudo-collision: if the key is longer than the hash block size (e.g. 64 characters for SHA-1), then HMAC(k, m) is computed as HMAC(H(k), m).This property is sometimes raised as a possible weakness of HMAC in password-hashing scenarios: it has been demonstrated that it's possible to find a long ASCII string and a random value whose hash will be also an ASCII string, and both values will produce the same HMAC output

### FAQ

1. _After reading a bunch of past stack exchange posts like this one and RFCs 5869, 2104, and 4868 I felt comfortable that a 32-byte key was sufficient for HMAC-SHA256. However, I am implementing my code in C# and someone pointed out to me that the Microsoft HMAC-SHA256 documentation recommends a 64-byte key: ``The key can be any length. However, the recommended size is 64 bytes.``
Is there any good reason to use a 64-byte key instead of a 32-byte key?_

Ans. Check this linkn for answer: https://crypto.stackexchange.com/questions/34864/key-size-for-hmac-sha256




