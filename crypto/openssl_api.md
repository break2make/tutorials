# Openssl


## Installation

First, download the latest version from https://www.openssl.org/source/. I suggest to use version 1.1.1k or above as there were few reported vulnerability in openssl 1.1.1g and those are corrected in version 1.1.1k.

```
$ wget https://www.openssl.org/source/openssl-1.1.1k.tar.gz
$ wget https://www.openssl.org/source/openssl-1.1.1k.tar.gz.sha256
$ sha256sum openssl-1.1.1k.tar.gz
$ cat openssl-1.1.1k.tar.gz.sha256
$tar -zxvf openssl-1.1.1k.tar.gz
$ cd openssl-1.1.1k/
```
Now, configure the installation (with debug option - To debug your code using openssl library, we need to build the openssl library in debug mode which generates debug sysmbol for openssl.):

```
./config --prefix=/usr/local/openssl_111k_d --openssldir=/usr/local/openssl_111k_d -d shared no-asm no-ssl2 -g3 -ggdb -gdwarf-4 -fno-inline -O0 -fno-omit-frame-pointer
```

Then,
```
$ make
```

```
$ echo $?
0
```

```
$ make test
```

```
$ echo $?
0
```

```
$ sudo make install
```

```
$ echo $?
0
```

### Configuration for shared library and binary (Post installation)

### Links
- [Debugging OpenSSL code using gdb](https://medium.com/@amit.kulkarni/debugging-openssl-code-using-gdb-55451efe9428). Also check the following links:
	-  [Installing OpenSSL on Ubuntu](https://www.spinup.com/installing-openssl-on-ubuntu/)
	-  [Installing OpenSSL on Ubuntu 16.04/18.04](https://cloudwafer.com/blog/installing-openssl-on-ubuntu-16-04-18-04/)





# Parsing ASN file

https://stackoverflow.com/questions/38420344/parsing-asn1-document-with-openssl-c-api

## Extract ECDSA raw bytes from signature

The ECDSA signature is encoded as an ASN.1 structure, which is a SEQUENCE of two INTEGER values. When encoded, the first byte will by 0x30 (which means SEQUENCE), followed by the length, encoded over one or two bytes: if length is n bytes, then it will be encoded as a single byte of value n if n ≤ 127, or two bytes of value 0x81 then n, if 128 ≤ n ≤ 255 (the latter case may happen in case you use a "large" curve like P-521). These n bytes are the concatenation of the two INTEGER values, each with its own tag (a byte of value 0x02), then its length (same encoding; in practice, over a single byte, since it would take a 1000-bit or so curve to need more than one), then the INTEGER value. The value of an INTEGER uses signed big-endian (so you may have a leading byte of value 0x00).

Properly encoding and decoding ASN.1 structures is a difficult art. I don't know if OpenSSL has a public function for that. This function, from another SSL library, converts from ASN.1 to "raw" ECDSA signatures ("raw" means: the two integer values are simply encoded in big-endian and concatenated, both being adjusted to have the same encoding length).

# BN
https://students.cs.byu.edu/~cs465ta/fall2014/Samples/dh_bignum.htm
https://github.com/drichardson/examples/blob/master/openssl/BigNum/main.c

# Dealing with .PEM files

The PEM functions read or write structures in PEM format. In this sense PEM format is simply base64 encoded data surrounded by header lines. For details about the OpenSSL pem function, read https://www.openssl.org/docs/man1.1.1/man3/PEM_write_PrivateKey.html

There are different types of APIs for read and write from/to a file in PEM format, and those can be grouped based on the following aspects:
- the keys are written/read from file or bio
- keys are available as generic EVP_PEKY structure or algorithm specific structure like RSA, EC_KEY, DSA, etc.


# HKDF

### Links
- [HKDF implementation](https://www.programmersought.com/article/90085279316/)
- 


# Key management using EVP API

Definition of all structure for evp can be found: https://github.com/openssl/openssl/blob/master/include/crypto/evp.h

A few impotant type parameter values are:
```
# define EVP_PKEY_NONE   NID_undef
# define EVP_PKEY_RSA    NID_rsaEncryption
# define EVP_PKEY_RSA2   NID_rsa
# define EVP_PKEY_RSA_PSS NID_rsassaPss
# define EVP_PKEY_DSA    NID_dsa
# define EVP_PKEY_DSA1   NID_dsa_2
# define EVP_PKEY_DSA2   NID_dsaWithSHA
# define EVP_PKEY_DSA3   NID_dsaWithSHA1
# define EVP_PKEY_DSA4   NID_dsaWithSHA1_2
# define EVP_PKEY_DH     NID_dhKeyAgreement
# define EVP_PKEY_DHX    NID_dhpublicnumber
# define EVP_PKEY_EC     NID_X9_62_id_ecPublicKey
# define EVP_PKEY_SM2    NID_sm2
# define EVP_PKEY_HMAC   NID_hmac
# define EVP_PKEY_CMAC   NID_cmac
# define EVP_PKEY_SCRYPT NID_id_scrypt
# define EVP_PKEY_TLS1_PRF NID_tls1_prf
# define EVP_PKEY_HKDF   NID_hkdf
# define EVP_PKEY_POLY1305 NID_poly1305
# define EVP_PKEY_SIPHASH NID_siphash
# define EVP_PKEY_X25519 NID_X25519
# define EVP_PKEY_ED25519 NID_ED25519
# define EVP_PKEY_X448 NID_X448
# define EVP_PKEY_ED448 NID_ED448
```
All NID definition can be found here: https://github.com/openssl/openssl/blob/master/include/openssl/obj_mac.h


API definition for ``EVP_PKEY`` can be found here: https://github.com/openssl/openssl/blob/master/crypto/evp/p_lib.c


EVP_PKEY *EVP_PKEY_new(void)

EVP_PKEY *EVP_PKEY_new_raw_private_key(int type, ENGINE *e, const unsigned char *priv, size_t len)

**Set of important function to get and set the parameters of EVP_PKEY_CTX are:**

The ``EVP_PKEY_CTX_get_params()`` and ``EVP_PKEY_CTX_set_params()`` functions get and send arbitrary parameters from and to the algorithm implementation respectively. Not all parameters may be supported by all providers. See OSSL_PROVIDER(3) for more information on providers. See OSSL_PARAM(3) for more information on parameters. These functions must only be called after the EVP_PKEY_CTX has been initialised for use in an operation (for example by EVP_PKEY_sign_init_ex(3), EVP_PKEY_derive_init_ex(3) or other similar functions).

Source: https://www.openssl.org/docs/manmaster/man3/EVP_PKEY_CTX_set_params.html  (MUST read link)

**EVP_PKEY_CTX_ctrl**

This api is internally used by many openssl function to manage the EVP_KEY_CTX parameter
Source: https://github.com/openssl/openssl/blob/master/crypto/evp/pmeth_lib.c

EVP_PKEY_CTX_ctrl() and its macros return a positive value for success and 0 or a negative value for failure. In particular a return value of -2 indicates the operation is not supported by the public key algorithm. https://www.openssl.org/docs/man1.0.2/man3/EVP_PKEY_CTX_ctrl.html


# RSA Key generation

The following API can be use to update the EVP_PKEY_CTX preated for RSA key:
```
int EVP_PKEY_CTX_set_rsa_keygen_bits(EVP_PKEY_CTX *ctx, int mbits);           -> for modulus length in bits
int EVP_PKEY_CTX_set_rsa_keygen_pubexp(EVP_PKEY_CTX *ctx, BIGNUM *pubexp);    -> to specify the public key
int EVP_PKEY_CTX_set_rsa_keygen_primes(EVP_PKEY_CTX *ctx, int primes);        
```
The EVP_PKEY_CTX_set_rsa_keygen_bits() macro sets the RSA key length for RSA key generation to bits. If not specified 1024 bits is used.

The EVP_PKEY_CTX_set_rsa_keygen_pubexp() macro sets the public exponent value for RSA key generation to pubexp. Currently it should be an odd integer. The pubexp pointer is used internally by this function so it should not be modified or freed after the call. If not specified 65537 is used. The exponent is an odd number, typically 3, 17 or 65537

The EVP_PKEY_CTX_set_rsa_keygen_primes() macro sets the number of primes for RSA key generation to primes. If not specified 2 is used.

pkey_rsa_ctrl_str: https://github.com/openssl/openssl/blob/master/crypto/rsa/rsa_pmeth.c


**You could use following methods to separate public key and private key for future use.**

```
int PEM_write_bio_PrivateKey(BIO *bp, EVP_PKEY *x, const EVP_CIPHER *enc,
                    unsigned char *kstr, int klen,
                    pem_password_cb *cb, void *u);

 int PEM_write_PrivateKey(FILE *fp, EVP_PKEY *x, const EVP_CIPHER *enc,
                    unsigned char *kstr, int klen,
                    pem_password_cb *cb, void *u);
EVP_PKEY *PEM_read_bio_PUBKEY(BIO *bp, EVP_PKEY **x,
                    pem_password_cb *cb, void *u);

 EVP_PKEY *PEM_read_PUBKEY(FILE *fp, EVP_PKEY **x,
                    pem_password_cb *cb, void *u);

 int PEM_write_bio_PUBKEY(BIO *bp, EVP_PKEY *x);
 int PEM_write_PUBKEY(FILE *fp, EVP_PKEY *x);
 ```

Another way to generate RSA key:
https://stackoverflow.com/questions/5927164/how-to-generate-rsa-private-key-using-openssl
https://www.openssl.org/docs/man1.1.1/man3/PEM_read_RSA_PUBKEY.html
Get RSA structure from EVP_PKEY: https://www.openssl.org/docs/man1.0.2/man3/EVP_PKEY_get1_RSA.html

RSA structure: https://docs.huihoo.com/doxygen/openssl/1.0.1c/crypto_2rsa_2rsa_8h_source.html
```
struct rsa_st
  130     {
  131     /* The first parameter is used to pickup errors where
  132      * this is passed instead of aEVP_PKEY, it is set to 0 */
  133     int pad;
  134     long version;
  135     const RSA_METHOD *meth;
  136     /* functional reference if 'meth' is ENGINE-provided */
  137     ENGINE *engine;
  138     BIGNUM *n;
  139     BIGNUM *e;
  140     BIGNUM *d;
  141     BIGNUM *p;
  142     BIGNUM *q;
  143     BIGNUM *dmp1;
  144     BIGNUM *dmq1;
  145     BIGNUM *iqmp;
  146     /* be careful using this if the RSA structure is shared */
  147     CRYPTO_EX_DATA ex_data;
  148     int references;
  149     int flags;
  150 
  151     /* Used to cache montgomery values */
  152     BN_MONT_CTX *_method_mod_n;
  153     BN_MONT_CTX *_method_mod_p;
  154     BN_MONT_CTX *_method_mod_q;
  155 
  156     /* all BIGNUM values are actually in the following data, if it is not
  157      * NULL */
  158     char *bignum_data;
  159     BN_BLINDING *blinding;
  160     BN_BLINDING *mt_blinding;
  161     };
```
To extract the component from RSA structure, follow this link: https://www.openssl.org/docs/man1.1.1/man3/RSA_get0_e.html

> **2-prime vs Multi-prime.**
RSA_generate_key_ex() generates a 2-prime RSA key pair and stores it in the RSA structure provided in rsa. The pseudo-random number generator must be seeded prior to calling RSA_generate_key_ex().
>
>RSA_generate_multi_prime_key() generates a multi-prime RSA key pair and stores it in the RSA structure provided in rsa. The number of primes is given by the primes parameter. The random number generator must be seeded when calling RSA_generate_multi_prime_key().

# EC

Important links:
- https://andrea.corbellini.name/2015/05/17/elliptic-curve-cryptography-a-gentle-introduction/
- https://andrea.corbellini.name/2015/06/08/elliptic-curve-cryptography-breaking-security-and-a-comparison-with-rsa/
- https://www.ucalgary.ca/pst2017/files/pst2017/paper-39.pdf
- https://www.johndcook.com/blog/2018/08/21/a-tale-of-two-elliptic-curves/
- https://wiki.openssl.org/index.php/Command_Line_Elliptic_Curve_Operations  (read to know different format of private key)
- https://www.imsc.res.in/~ecc14/slides/costello.pdf


```
$ openssl ecparam -list_curves
  secp112r1 : SECG/WTLS curve over a 112 bit prime field
  secp112r2 : SECG curve over a 112 bit prime field
  secp128r1 : SECG curve over a 128 bit prime field
  secp128r2 : SECG curve over a 128 bit prime field
  secp160k1 : SECG curve over a 160 bit prime field
  secp160r1 : SECG curve over a 160 bit prime field
  secp160r2 : SECG/WTLS curve over a 160 bit prime field
  secp192k1 : SECG curve over a 192 bit prime field
  secp224k1 : SECG curve over a 224 bit prime field
  secp224r1 : NIST/SECG curve over a 224 bit prime field
  secp256k1 : SECG curve over a 256 bit prime field
  secp384r1 : NIST/SECG curve over a 384 bit prime field
  secp521r1 : NIST/SECG curve over a 521 bit prime field
  prime192v1: NIST/X9.62/SECG curve over a 192 bit prime field
  prime192v2: X9.62 curve over a 192 bit prime field
  prime192v3: X9.62 curve over a 192 bit prime field
  prime239v1: X9.62 curve over a 239 bit prime field
  prime239v2: X9.62 curve over a 239 bit prime field
  prime239v3: X9.62 curve over a 239 bit prime field
  prime256v1: X9.62/SECG curve over a 256 bit prime field
  sect113r1 : SECG curve over a 113 bit binary field
  sect113r2 : SECG curve over a 113 bit binary field
  sect131r1 : SECG/WTLS curve over a 131 bit binary field
  sect131r2 : SECG curve over a 131 bit binary field
  sect163k1 : NIST/SECG/WTLS curve over a 163 bit binary field
  sect163r1 : SECG curve over a 163 bit binary field
  sect163r2 : NIST/SECG curve over a 163 bit binary field
  sect193r1 : SECG curve over a 193 bit binary field
  sect193r2 : SECG curve over a 193 bit binary field
  sect233k1 : NIST/SECG/WTLS curve over a 233 bit binary field
  sect233r1 : NIST/SECG/WTLS curve over a 233 bit binary field
  sect239k1 : SECG curve over a 239 bit binary field
  sect283k1 : NIST/SECG curve over a 283 bit binary field
  sect283r1 : NIST/SECG curve over a 283 bit binary field
  sect409k1 : NIST/SECG curve over a 409 bit binary field
  sect409r1 : NIST/SECG curve over a 409 bit binary field
  sect571k1 : NIST/SECG curve over a 571 bit binary field
  sect571r1 : NIST/SECG curve over a 571 bit binary field
  c2pnb163v1: X9.62 curve over a 163 bit binary field
  c2pnb163v2: X9.62 curve over a 163 bit binary field
  c2pnb163v3: X9.62 curve over a 163 bit binary field
  c2pnb176v1: X9.62 curve over a 176 bit binary field
  c2tnb191v1: X9.62 curve over a 191 bit binary field
  c2tnb191v2: X9.62 curve over a 191 bit binary field
  c2tnb191v3: X9.62 curve over a 191 bit binary field
  c2pnb208w1: X9.62 curve over a 208 bit binary field
  c2tnb239v1: X9.62 curve over a 239 bit binary field
  c2tnb239v2: X9.62 curve over a 239 bit binary field
  c2tnb239v3: X9.62 curve over a 239 bit binary field
  c2pnb272w1: X9.62 curve over a 272 bit binary field
  c2pnb304w1: X9.62 curve over a 304 bit binary field
  c2tnb359v1: X9.62 curve over a 359 bit binary field
  c2pnb368w1: X9.62 curve over a 368 bit binary field
  c2tnb431r1: X9.62 curve over a 431 bit binary field
  wap-wsg-idm-ecid-wtls1: WTLS curve over a 113 bit binary field
  wap-wsg-idm-ecid-wtls3: NIST/SECG/WTLS curve over a 163 bit binary field
  wap-wsg-idm-ecid-wtls4: SECG curve over a 113 bit binary field
  wap-wsg-idm-ecid-wtls5: X9.62 curve over a 163 bit binary field
  wap-wsg-idm-ecid-wtls6: SECG/WTLS curve over a 112 bit prime field
  wap-wsg-idm-ecid-wtls7: SECG/WTLS curve over a 160 bit prime field
  wap-wsg-idm-ecid-wtls8: WTLS curve over a 112 bit prime field
  wap-wsg-idm-ecid-wtls9: WTLS curve over a 160 bit prime field
  wap-wsg-idm-ecid-wtls10: NIST/SECG/WTLS curve over a 233 bit binary field
  wap-wsg-idm-ecid-wtls11: NIST/SECG/WTLS curve over a 233 bit binary field
  wap-wsg-idm-ecid-wtls12: WTLS curve over a 224 bit prime field
  Oakley-EC2N-3: 
        IPSec/IKE/Oakley curve #3 over a 155 bit binary field.
        Not suitable for ECDSA.
        Questionable extension field!
  Oakley-EC2N-4: 
        IPSec/IKE/Oakley curve #4 over a 185 bit binary field.
        Not suitable for ECDSA.
        Questionable extension field!
  brainpoolP160r1: RFC 5639 curve over a 160 bit prime field
  brainpoolP160t1: RFC 5639 curve over a 160 bit prime field
  brainpoolP192r1: RFC 5639 curve over a 192 bit prime field
  brainpoolP192t1: RFC 5639 curve over a 192 bit prime field
  brainpoolP224r1: RFC 5639 curve over a 224 bit prime field
  brainpoolP224t1: RFC 5639 curve over a 224 bit prime field
  brainpoolP256r1: RFC 5639 curve over a 256 bit prime field
  brainpoolP256t1: RFC 5639 curve over a 256 bit prime field
  brainpoolP320r1: RFC 5639 curve over a 320 bit prime field
  brainpoolP320t1: RFC 5639 curve over a 320 bit prime field
  brainpoolP384r1: RFC 5639 curve over a 384 bit prime field
  brainpoolP384t1: RFC 5639 curve over a 384 bit prime field
  brainpoolP512r1: RFC 5639 curve over a 512 bit prime field
  brainpoolP512t1: RFC 5639 curve over a 512 bit prime field
  SM2       : SM2 curve over a 256 bit prime field
```
To get the NID for these curve, which is required by openssl APIs, check https://github.com/openssl/openssl/blob/master/include/openssl/obj_mac.h

```
typedef struct ec_key_st EC_KEY;
```
Source: https://github.com/enthought/openssl/blob/master/crypto/ec/ec.h

```
struct ec_key_st {
	int version;

	EC_GROUP *group;

	EC_POINT *pub_key;
	BIGNUM	 *priv_key;

	unsigned int enc_flag;
	point_conversion_form_t conv_form;

	int 	references;

	EC_EXTRA_DATA *method_data;
} /* EC_KEY */;
```
Source: https://github.com/enthought/openssl/blob/master/crypto/ec/ec_lcl.h

## Key Generation

### Command

### API

We can use the following function to generate the EC key pair:
```
EC_KEY * generate_eckey() {
    EC_KEY *eckey=EC_KEY_new();
    EC_GROUP *ecgroup= EC_GROUP_new_by_curve_name(NID_secp256k1);
    EC_KEY_set_group(eckey, ecgroup);
    EC_KEY_generate_key(eckey);

    return eckey;
}
```
We can also use a single API ``eckey = EC_KEY_new_by_curve_name(NID_secp256k1)`` in place of the following three lines in the above code:
```
EC_KEY *eckey=EC_KEY_new();
EC_GROUP *ecgroup= EC_GROUP_new_by_curve_name(NID_secp256k1);
EC_KEY_set_group(eckey, ecgroup);
 ```
 
 ### Save the key into file
 
 ### Load key from file
 
The key can be stred either in DER or PEM format. Note that private key also store the public key while using openssl API to save the `EC_KEY` into file. The loading of key file use two different set of APIs for this purpose:
- For ASN.1/DER, we have `d2i_ECPrivateKey` and `d2i_EC_PUBKEY` APIs for reading private key file and public key file, respectively.
- For PEM, we use `PEM_read_ECPrivateKey` and `PEM_read_EC_PUBKEY`. The write functions are similar and documented in the man pages.

Note that `d2i_*` is "DER to internal", and its used to read ASN.1/DER keys. The write functions use `i2d_*` and its "internal to DER". PEM does not use a cryptic prefix. Check this [post](https://stackoverflow.com/questions/38269867/reading-and-writing-openssl-ecdsa-keys-to-pem-file), for more details.
 
 
 # AES
 
 Input specification:
 - **Block size**. 128-bit (16 bytes)
 - **Key size**. 128-, 192-, 256-bit
 
 ## What should be the length of a ciphertext?

Assuming PKCS#7 padding, which is the default for OpenSSL ECB and CBC mode, the encrypted length will be:
```
plaintext_len + block_size - (plaintext_len % block_size)
```
where `block_size = 16` for AES. The end result is always a multiple of block_size. 

For modes like `CTR`, and `GCM`, no padding is used, and thus, plaintext and ciphertext lengths are same.


## AES GCM

### Inputs and Outputs to GCM

GCM has two operations, authenticated encryption and authenticated decryption. The authenticated encryption operation has four inputs, each of which is a bit string:
A secret key K, whose length is appropriate for the underlying block cipher.
- An initialization vector IV, that can have any number of bits between 1 and 2^64. For a fixed value of key, each IV value must be distinct, but need not have equal lengths. 96-bit IV values can be processed more efficiently, so that length is recommended for situations in which efficiency is critical.
- A plaintext P, which can have any number of bits between 0 and 2^39 - 256.
- Additional authenticated data (AAD), which is denoted as A. This data is authenticated, but not encrypted, and can have any number of bits between 0 and 2^64.

The There two Outputs:

- A ciphertext C whose length is exactly that of the plaintext P.
- An authentication tag T, whose length can be any value between 0 and 128. The length of the tag is denoted as t.

The authenticated decryption operation has five inputs: K, IV, C, A and T. It has only a single output, either the plaintext value P or a special symbol ‘FAIL’ that indicates that the inputs are not authentic. A ciphertext C, initialization vector IV, additional authenticated data A and tag T are authentic for key K when they are generated with the encrypt operation with inputs K, IV, A and P, for some plaintext P. 


### Configuring Parameters

- **Output size = input size**. That's correct, GCM uses CTR internally. It encrypts a counter value for each block, but it only uses as many bits as required from the last block. CTR turns the block cipher into a stream cipher. Note that this doesn't include any additional authenticated data (AAD) that needs to be send, the optional inclusion of the (otherwise required) IV nor size of the required authentication tag.

- **IV of any size**. For GCM a **12 byte (96-bit)** IV is strongly suggested as other IV lengths will require additional calculations. In principle any IV size can be used as long as the IV doesn't ever repeat. NIST however suggests that only an IV size of 12 bytes needs to be supported by implementations. How to transport IV Yes, generally the IV is prefixed to the ciphertext or calculated using some kind of nonce on both sides. The size of the IV should be defined by the protocol. If it is possible to synchronize a nonce of 12 bytes then the IV doesn't need to be included with the ciphertext.

- **Size of authentication tags**. The calculated tag will always be 16 bytes long, but the leftmost bytes can be used. GCM is defined for the tag sizes 128, 120, 112, 104, or 96, 64 and 32. Note that the security of GCM is strongly dependent on the tag size. You should try and use a tag size of 64 bits at the very minimum, but in general a tag size of the full **128 bits** should be preferred.

Few observations:
- In my AES-GCM implementation with IV more than 12 bytes, the decryption failed. [To be investigated].

Check the followng links for more details:
- Ciphertext and tag size and IV transmission with AES in GCM mode. [[stackexchange](https://crypto.stackexchange.com/questions/26783/ciphertext-and-tag-size-and-iv-transmission-with-aes-in-gcm-mode)]
- Recommendation for Block Cipher Modes of Operation: Galois/Counter Mode (GCM) and GMAC [[NIST](https://csrc.nist.gov/publications/detail/sp/800-38d/final)]
- EVP Authenticated Encryption and Decryption. [[Openssl wiki](https://wiki.openssl.org/index.php/EVP_Authenticated_Encryption_and_Decryption)]
- Galois / Counter Mode (GCM) Cipher. [[Blog](https://wirelessonthego.postach.io/post/galois-counter-mode-gcm-cipher)]
- Simple AES GCM test program [[Openssl source](https://github.com/openssl/openssl/blob/master/demos/evp/aesgcm.c)]
- Authenticated Encryption Gcm Ccm [[Slides](https://www.slideshare.net/ProjectSymphony/authenticated-encryption-gcm-ccm)]
- AES-GCM IV Vulnerabilities [[wycheproof](https://github.com/google/wycheproof/blob/master/doc/aesgcm.md)]




# Links
## Book
- Network Security with OpenSSL: Cryptography for Secure Communications
