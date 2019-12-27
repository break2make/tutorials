

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

### Domain parameters
Our elliptic curve algorithms will work in a cyclic subgroup of an elliptic curve over a finite field. Therefore, our algorithms will need the following parameters:

+ The prime *p* that specifies the size of the finite field.
+ The coefficients *a* and *b* of the elliptic curve equation.
+ The base point *G* that generates our subgroup.
+ The order *n* of the subgroup.
+ The cofactor  of the subgroup.

To summarizes, the domain parameters EC algorithms can be represented as 6-tuple *(p, a, b, G, n, h)*, and all these can be public information without any information leakage.

>The public and private keys are generated as follows:
>- Private key is an integer ***d***, randomly selected in the interval *[1,n-1]*
>- Public key is curve point ***H = dG***, which is an elliptic curve point multiplication by a scalar.

### Algorithms
#### ECDH
_Source: Wikipedia/ https://andrea.corbellini.name/2015/05/30/elliptic-curve-cryptography-ecdh-and-ecdsa/_

Elliptic-curve Diffie–Hellman (ECDH) is a key agreement protocol that allows two parties, each having an elliptic-curve public–private key pair, to establish a shared secret over an _insecure channel_. This shared secret may be directly used as a key, or to derive another key. The key, or the derived key, can then be used to encrypt subsequent communications using a symmetric-key cipher. It is a variant of the Diffie–Hellman protocol using elliptic-curve cryptography.

***Here's how it works:***

ECDH is a variant of the Diffie-Hellman algorithm for elliptic curves. It is actually a key-agreement protocol, more than an encryption algorithm. This basically means that ECDH defines (to some extent) how keys should be generated and exchanged between parties. How to actually encrypt data using such keys is up to us.

The problem it solves is the following: two parties (the usual Alice and Bob) want to exchange information securely, so that a third party (the Man In the Middle) may intercept them, but may not decode them. This is one of the principles behind TLS.

1. **Alice and Bob generate their own private and public keys.** Let *d<sub>A</sub>* and *H<sub>A</sub> = d<sub>A</sub>G* be the private and public keys of Alice, and the *d<sub>B</sub>* and *H<sub>B</sub> = d<sub>B</sub>G* are private and public keys for Bob. Note that both Alice and Bob are using the same domain parameters: the same base point *G* on the same elliptic curve on the same finite field.

2. **Alice and Bob exchange their public keys *H<sub>A</sub>* and *H<sub>B</sub>* over an insecure channel.** The Man In the Middle would intercept these public keys, but won't be able to find out neither *d<sub>A</sub>* nor *d<sub>B</sub>* without solving the discrete logarithm problem.

3. **Alice calculates *S = d<sub>A</sub>H<sub>B</sub>* (using her own private key and Bob's public key), and Bob calculates *S = d<sub>B</sub>H<sub>A</sub>* (using his own private key and Alice's public key).** Note that  *S* is the same for both Alice and Bob, in fact:  *S(y,x) = d<sub>B</sub>H<sub>A</sub> = d<sub>B</sub>(d<sub>A</sub>G) = d<sub>A</sub>(d<sub>B</sub>G) = d<sub>A</sub>H<sub>B</sub>*. The shared secret is *x* (the x coordinate of the point). 


The Man In the Middle, however, only knows *H<sub>A</sub>* and *H<sub>B</sub>* (together with the other domain parameters) and would not be able to find out the shared secret *S*. This is known as the Diffie-Hellman problem, which can be stated as follows:

> Given three points *P*, *aP* and *bP*, what is the result of *abP*?

***Important notes:***
- If Alice maliciously chooses invalid curve points for her key and Bob does not validate that Alice's points are part of the selected group, she can collect enough residues of Bob's key to derive his private key. Several TLS libraries were found to be vulnerable to this attack.
- While the shared secret may be used directly as a key, it can be desirable to hash the secret to remove weak bits due to the Diffie–Hellman exchange. ***Most standardized protocols based on ECDH derive a symmetric key from shared secret using some hash-based key derivation function.***

##### Ephemeral ECDH

The public keys are either static (and trusted, say via a certificate) or ephemeral (also known as ECDHE, where final 'E' stands for "ephemeral"). Ephemeral keys are temporary and not necessarily authenticated, so if authentication is desired, authenticity assurances must be obtained by other means. Authentication is necessary to avoid man-in-the-middle attacks. If one of either Alice's or Bob's public keys is static, then man-in-the-middle attacks are thwarted. ***Static public keys provide neither forward secrecy nor key-compromise impersonation resilience, among other advanced security properties.*** Holders of static private keys should validate the other public key, and should apply a secure key derivation function to the raw Diffie–Hellman shared secret to avoid leaking information about the static private key.

The "E" in ECDHE stands for "Ephemeral" and it implies that the keys exchanged are temporary, rather than static.
ECDHE is used, for example, in TLS, where both the client and the server generate their public-private key pair on the fly, when the connection is established. The keys are then signed with the TLS certificate (for authentication) and exchanged between the parties.


##### Ephemeral Diffie-Hellman vs static Diffie-Hellman
source: https://tls.mbed.org/kb/cryptography/ephemeral-diffie-hellman

Ephemeral Diffie-Hellman (DHE in the context of TLS) differs from the static Diffie-Hellman (DH) in the way that static Diffie-Hellman key exchanges always use the same Diffie-Hellman private keys (i.e. same private keys of client and server). So, each time the same parties do a DH key exchange, they end up with the same shared secret.

When a key exchange uses Ephemeral Diffie-Hellman a temporary DH key is generated for every connection and thus the same key is never used twice. This enables Forward Secrecy (FS), which means that if the long-term private key of the server gets leaked, past communication is still secure.

This distinction also holds for the Elliptic Curve variants ECDHE (ephemeral, provides Forward Secrecy) and ECDH (static).

Due to increasing concern about pervasive surveillance, key exchanges that provide Forward Secrecy are recommended, see for example RFC 7525, section 6.3.

Authentication
Ephemeral Diffie-Hellman doesn't provide authentication on its own, because the key is different every time. So neither party can be sure that the key is from the intended party.

Within SSL you will often use DHE as part of a key-exchange that uses an additional authentication mechanism (e.g. RSA, PSK or ECDSA). So the fact that the SSL server signs the content of its server key exchange message that contain the ephemeral public key implies to the SSL client that this Diffie-Hellman public key is from the SSL server.

Ciphersuites supporting Ephemeral Diffie-Hellman
There are a lot of ciphersuites that support Ephemeral Diffie-Hellman. The key exchange methods that use (EC)DHE in TLS are:

- Ephemeral Diffie Hellman with RSA (DHE-RSA) key exchange
- Elliptic Curve Ephemeral Diffie Hellman with RSA (ECDHE-RSA) key exchange
- Elliptic Curve Ephemeral Diffie Hellman with ECDSA (ECDHE-ECDSA) key exchange
- Pre Shared Key with Diffie Hellman (DHE-PSK) key exchange
- Pre Shared Key with Elliptic Curve Diffie Hellman (ECDHE-PSK) key exchange 

#### ECDSA
Source: https://andrea.corbellini.name/2015/05/30/elliptic-curve-cryptography-ecdh-and-ecdsa/_
Read the above link

##### Key and signature-size

- As with elliptic-curve cryptography in general, the bit size of the public key believed to be needed for ECDSA is about ***twice the size of the security level***, in bits. For example, at a security level of 80 bits (meaning an attacker requires a maximum of about 2<sup>80</sup> operations to find the private key) the size of an ECDSA public key would be 160 bits, whereas the size of a DSA public key is at least 1024 bits. 
- The signature size is the same for both DSA and ECDSA: approximately ***4t bits, where t is the security level measured in bits***, that is, about 320 bits for a security level of 80 bits.
