# Dealing with .PEM files

The PEM functions read or write structures in PEM format. In this sense PEM format is simply base64 encoded data surrounded by header lines. For details about the OpenSSL pem function, read https://www.openssl.org/docs/man1.1.1/man3/PEM_write_PrivateKey.html

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


# Links
## Book
- Network Security with OpenSSL: Cryptography for Secure Communications
