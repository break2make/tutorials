

## HMAC and security sarameters

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


## Eliptic curve algorithms and security parameters

### ECDH
_Source: Wikipedia_

Elliptic-curve Diffie–Hellman (ECDH) is a key agreement protocol that allows two parties, each having an elliptic-curve public–private key pair, to establish a shared secret over an _insecure channel_. This shared secret may be directly used as a key, or to derive another key. The key, or the derived key, can then be used to encrypt subsequent communications using a symmetric-key cipher. It is a variant of the Diffie–Hellman protocol using elliptic-curve cryptography.

_Important notes:_
- If Alice maliciously chooses invalid curve points for her key and Bob does not validate that Alice's points are part of the selected group, she can collect enough residues of Bob's key to derive his private key. Several TLS libraries were found to be vulnerable to this attack.
- While the shared secret may be used directly as a key, it can be desirable to hash the secret to remove weak bits due to the Diffie–Hellman exchange.

Ephemeral ECDH

### Ephemeral ECDH
The "E" in ECDHE stands for "Ephemeral" and it implies that the keys exchanged are temporary, rather than permanent.
ECDHE is used, for example, in TLS, where both the client and the server generate their public-private key pair on the fly, when the connection is established. The keys are then signed with the TLS certificate (for authentication) and exchanged between the parties.

