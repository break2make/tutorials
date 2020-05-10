# SHA
The *Secure Hash Algorithms* are a family of cryptographic hash functions published by the National Institute of Standards and Technology (NIST) as a U.S. Federal Information Processing Standard (FIPS). The following table lists various secure hash algorithms, their variants and important parameters.

| Algorithms | Variants | Output Size (bits) | Internal State Size (bits) | Block Size (bits) | Rounds|
|:---:|:---:|:----------:|:---:|:---:|:---:|
|SHA-0/1 | - | 160 | 160 (5 x 32) | 512 | 80 |
|SHA2| SHA-224 | 224| 256 (8x32)| 512| 64|
|SHA2| SHA-256 | 256| 256 (8x32)| 512| 64|
|SHA2| SHA-384 | 384| 512 (8x64)| 1024| 80|
|SHA2| SHA-512 | 512| 512 (8x64)| 1024| 80|
|SHA2| SHA-512/224 | 224| 512 (8x64)| 1024| 80|
|SHA2| SHA-512/256 | 256| 512 (8x64)| 1024| 80|
|SHA3| SHA3-224 | 224| 1600 (5x5x64)| 1152| 24|
|SHA3| SHA3-256 | 256| 1600 (5x5x64)| 1088| 24|
|SHA3| SHA3-384 | 384| 1600 (5x5x64)| 832| 24|
|SHA3| SHA3-512 | 512| 1600 (5x5x64)| 576| 24|

For more details, check [here][].

## SHA-256
A detailed explanation of SHA-256 can be found [here][sha256-detailed].

[sha256-bitcoinwiki]: https://en.bitcoinwiki.org/wiki/SHA-256
[sha256-bellet]: https://medium.com/biffures/part-5-hashing-with-sha-256-4c2afc191c40
[sha256-detailed]: http://www.iwar.org.uk/comsec/resources/cipher/sha256-384-512.pdf 
[sha256-wiki]: https://en.wikipedia.org/wiki/SHA-2
[sha-wiki]: https://en.wikipedia.org/wiki/Secure_Hash_Algorithms

Few similar type of resurces are:
- [SHA-256][sha256-bitcoinwiki]
- [Hashing with SHA-256][sha256-bellet]
- [Descriptions of SHA-256, SHA-384, and SHA-512][sha256-detailed]
- [SHA256 - Wikipedia][sha256-wiki]
- [Secure Hash Algorithms - Wikipedia][sha-wiki]
