Abstract Syntax Notation 1 (ASN.1)






# Important Links
- http://luca.ntop.org/Teaching/Appunti/asn1.html (ODI introduction)
- https://coolaj86.com/articles/asn1-for-dummies/ (Short but useful, sample parsing code is available too)
- https://www.oss.com/asn1/resources/books-whitepapers-pubs/larmouth-asn1-book.pdf
- https://www.cs.auckland.ac.nz/~pgut001/dumpasn1.c (asn parsing)
- http://oid-info.com/get/2 (OID list)
- https://www.scss.tcd.ie/~htewari/4D1/erlang/lib/asn1-1.3.3.1/doc/html/asn1_ug.html
- http://www.umich.edu/~x509/ssleay/asn1-oids.html
- https://gist.github.com/awood/9338235
- https://standards.ieee.org/content/dam/ieee-standards/standards/web/documents/tutorials/oid.pdf (OID description)
- https://en.wikipedia.org/wiki/Object_identifier
- Asn.1 Communication Between Heterogeneous Systems (Book)
- https://tools.ietf.org/html/rfc3447 (ANS systax for PKCS in details)
- https://tools.ietf.org/html/rfc5280 (ASN.1 structure for Certificate)
- https://www.itu.int/dms_pub/itu-s/opb/journal/S-JOURNAL-ICTF.VOL1-2018-2-P01-PDF-E.pdf



# Crytographic Message Syntax using ASN.1

```
ContentInfo ::= SEQUENCE {
      contentType        CONTENT-TYPE.
                      &id({ContentSet}),
      content            [0] EXPLICIT CONTENT-TYPE.
                      &Type({ContentSet}{@contentType})}

  ContentSet CONTENT-TYPE ::= {
      --  Define the set of content types to be recognized.
      ct-Data | ct-SignedData | ct-EncryptedData | ct-EnvelopedData |
      ct-AuthenticatedData | ct-DigestedData, ... }
```

## SignedData for digital signature
  
  ```
  SignedData ::= SEQUENCE {
      version CMSVersion,
      digestAlgorithms SET OF DigestAlgorithmIdentifier,
      encapContentInfo EncapsulatedContentInfo,
      certificates [0] IMPLICIT CertificateSet OPTIONAL,
      crls [1] IMPLICIT RevocationInfoChoices OPTIONAL,
      signerInfos SignerInfos }

  SignerInfos ::= SET OF SignerInfo

  EncapsulatedContentInfo ::= SEQUENCE {
      eContentType       CONTENT-TYPE.&id({ContentSet}),
      eContent           [0] EXPLICIT OCTET STRING
              ( CONTAINING CONTENT-TYPE.
                  &Type({ContentSet}{@eContentType})) OPTIONAL }
```
If `eContent` is empty, the file does not contain the signed data. Instead it is having the signature and certificate. This type of signature is called _Detached Signature._

```
  SignerInfo ::= SEQUENCE {
      version CMSVersion,
      sid SignerIdentifier,
      digestAlgorithm DigestAlgorithmIdentifier,
      signedAttrs [0] IMPLICIT SignedAttributes OPTIONAL,
      signatureAlgorithm SignatureAlgorithmIdentifier,
      signature SignatureValue,
      unsignedAttrs [1] IMPLICIT Attributes
          {{UnsignedAttributes}} OPTIONAL }
```

The signature value resides in `SignerInfo` as `signature SignatureValue`. This value is ASN.1 `OCTECT_STRING`. For RSA, it is a octect string, while for ECDSA, it is octect string over a sequecnce having two integer (as signature in ECDSA is a point).


```
  SignedAttributes ::= Attributes {{ SignedAttributesSet }}

  SignerIdentifier ::= CHOICE {
      issuerAndSerialNumber IssuerAndSerialNumber,
      ...,
      [[3: subjectKeyIdentifier [0] SubjectKeyIdentifier ]] }

  SignedAttributesSet ATTRIBUTE ::=
      { aa-signingTime | aa-messageDigest | aa-contentType, ... }

  UnsignedAttributes ATTRIBUTE ::= { aa-countersignature, ... }
  SignatureValue ::= OCTET STRING
```

The following are used for version numbers using the ASN.1
  - idiom "[[n:"
  - Version 1 = PKCS #7
  - Version 2 = S/MIME V2
  - Version 3 = RFC 2630
  - Version 4 = RFC 3369
  - Version 5 = RFC 3852

For more information, look into Page 25 in https://tools.ietf.org/html/rfc5911




# Digital Signature

## Attached and Detached Digital Signatures
Source: https://docs.oracle.com/cd/E19398-01/820-1228/gfnmj/index.html

Digital signatures are normally attached to the message. However, digital signatures can also be detached. A detached signature may be stored and transmitted separately from the message it signs. 

**Attached Signatures**
The characteristics of attached digital signatures in PKCS#7 and S/MIME formats are:

- PKCS#7
  - Includes the document in plain text with digital signature.

  - Ensures that certificates are encoded in Abstract Syntax Notation One (ASN.1) format, where ASN.1 is an ISO/IEC standard for encoding rules used in ANSI X.509 certificates and PKCS documents.

- S/MIME2:

  - Includes MIME headers and PKCS#7 with the signature attached.

**Detached Signatures**
The characteristics of detached digital signatures in PKCS#7 and S/MIME formats are as follows:

- PKCS#7: Includes the signature and certificate without the signed data.

- RNIF1.1: Uses PKCS#7 and a detached format.

- S/MIME2: May include a MIME multipart message consisting of the original data in one segment and a binary format signature or a base64-encoded signature in a second segment.
