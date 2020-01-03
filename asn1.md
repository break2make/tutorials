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
