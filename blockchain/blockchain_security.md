
# Blockchain

In most blockchains or distributed ledger technologies (DLT), the data is structured into blocks and each block contains a transaction or bundle of transactions. Each new block connects to all the blocks before it in a cryptographic chain in such a way that it's nearly impossible to tamper with. All transactions within the blocks are validated and agreed upon by a consensus mechanism, ensuring that each transaction is true and correct.

Blockchain technology enables decentralization through the participation of members across a distributed network. There is no single point of failure and a single user cannot change the record of transactions. However, blockchain technologies differ in some critical security aspects.

Blockchain networks can differ in who can participate and who has access to the data. Networks are typically labeled as either **public** or **private**, which describes who is allowed to participate, and **permissioned** or **permissionless**, which describes how participants gain access to the network.

When building a blockchain application, it’s critical to assess which type of network will best suit your business goals. Private and permissioned networks can be tightly controlled and preferable for compliance and regulatory reasons. However, public and permissionless networks can achieve greater decentralization and distribution.


# Anonymous Blockchain

- https://developer.ibm.com/tutorials/cl-blockchain-private-confidential-transactions-hyperledger-fabric-zero-knowledge-proof/


# Cryptographic methods for Privacy using Blockchains
- Zero-knowledge proofs
- Ring signature
- Mixing

source: 
- [Privacy and blockchain](https://en.wikipedia.org/wiki/Privacy_and_blockchain#:~:text=A%20key%20aspect%20of%20privacy,numbers%20and%20are%20cryptographically%20related.)

## Ring Signature

*Wikipedia* - In cryptography, a ring signature is a type of digital signature that can be performed by any member of a set of users that each have keys. Therefore, a message signed with a ring signature is endorsed by someone in a particular set of people. One of the security properties of a ring signature is that it should be computationally infeasible to determine which of the set's members' keys was used to produce the signature. Ring signatures are similar to group signatures but differ in two key ways: first, there is no way to revoke the anonymity of an individual signature; and second, any set of users can be used as a signing set without additional setup.

### Group signatures vs Ring signature
The general notion of a group signature scheme was introduced in 1991 by Chaum and van Heyst. In such a scheme, a trusted group manager predefines certain groups of users and distributes specially designed keys to their members. Individual members can then use these keys to anonymously sign messages on behalf of their group. The signatures produced by different group members look indistinguishable to their verifiers, but not to the group manager who can revoke the anonymity of misbehaving signers.

Ring signature schemes are simplified group signature schemes that have only users and no managers (we call such signatures “ring signatures” instead of “group signatures” since rings are geometric regions with uniform periphery and no center). Group signatures are useful when the members want to cooperate, while ring signatures are useful when the members do not want to cooperate. Both group signatures and ring signatures are signer-ambiguous, but in a ring signature scheme there are no prearranged groups of users, there are no procedures for setting, changing, or deleting groups, there is no way to distribute specialized keys, and there is no way to revoke the anonymity of the actual signer (unless he decides to expose himself). Our only assumption is that each member is already associated with the public key of some standard signature scheme such as RSA. To produce a ring signature, the actual signer declares an arbitrary set of possible signers that must include himself, and computes the signature entirely by himself using only his secret key and the others’ public keys. In particular, the other possible signers could have chosen their RSA keys only in order to conduct e-commerce over the internet, and may be completely unaware that their public keys are used by a stranger to produce such a ring signature on a message they have never seen and would not wish to sign. 

### Links
- [Ring Signatures- Analysis and Implementation](https://courses.csail.mit.edu/6.857/2020/projects/17-Barabonkov-Esteban-Fabrega.pdf) - MUST READ for details
- [How to Leak a Secret: Theory and Applications of Ring Signatures](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/01/2006-Leak_Secret.pdf) - MUST READ
- [Ring signature](https://en.wikipedia.org/wiki/Ring_signature)
- [Privacy on the Blockchain: Unique Ring Signatures](https://arxiv.org/abs/1612.01188)
- [A Hybrid Design of Linkable Ring Signature Scheme with Stealth Addresses](https://www.hindawi.com/journals/scn/2022/1417607/)
- [Ring Signatures And Anonymisation](https://medium.com/asecuritysite-when-bob-met-alice/ring-signatures-and-anonymisation-c9640f08a193) a good resource


# Cryptocurrency


## Monero (private cryptocurrency)

Monero obfuscates the following part of a transaction:
- Sender address (ring signature)
- Amount (Ring Confidential Transaction - RingCT)
- Recipent address (Stealth Address)

- [What is Monero? A Beginner’s Guide](https://www.youtube.com/watch?v=qrUq0v5VgdU&ab_channel=99Bitcoins)
- [How to Transact Cryptocurrency Anonymously: Monero Tutorial](https://www.youtube.com/watch?v=VYdfYUIQ_9c&ab_channel=CryptoTraders)


# Dark Web

# Web3
