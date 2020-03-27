# Hardware Security Module

The hardware security module (HSM) is a special `trused` computing element performing a variety of cryptographic operations: key management, key exchange, encryption etc.

By trusted, it is expected that HSM shall be free from “no viruses, no malware, no exploit, no unauthorized access.” An HSM is trusted because it ([source][blog-hsm-attributes]):
- Is built on top of specialized hardware. The hardware is well-tested and certified in special laboratories.
- Has a security-focused OS.
- Has limited access via a network interface that is strictly controlled by internal rules.
- Actively hides and protects cryptographic material.

>An ordinary, run-of-the-mill program writer mixes the database access code, business-logic and cryptographic calls in one big application. This is a dangerous approach as an attacker can use crafted data and vulnerabilities to access cryptographic material, steal keys, install an arbitrary X.509 certificate and so on. 
>
> For example, an XML vulnerability opened a door to a hacker who installed a root certificate to the trusted CA and stole $20 million.
>
> To prevent scenarios like this, it is required to separate the operations into two different areas. One for the business logic and one for cryptography. You then need to entrust the cryptographic operation to a trusted element, for example an HSM. ([source][blog-hsm-attributes])

# EVITA HSM Specification for Automotive


# HSM Certification

Security requirements for cryptographic modules are specified in [FIPS 140-2][fips-140-2]. There are four different levels (Level-1 to Level-4) are defined to classify the crypto graphic modules based on their implemented features. For more details for each of the level, read [FIPS 140-2][fips-140-2].

<!--- # HSM Interfaces --->

<!--- 
# HSM Chip Vendors
--->


# Cloud HSM - HSM for Could-hosted Applications 

Cloud HSM is a cloud-hosted hardware security module (HSM) service on a Cloud Platform. With Cloud HSM, you can host encryption keys and perform cryptographic operations. With this fully managed service, you can protect your most sensitive workloads without the need to worry about the operational overhead of managing an HSM cluster. A few well-known cloud HSM services are [Google Cloud HSM][google-cloudhsm], [Azure Dedicated HSM][azure-cloudhsm] and [AWS Cloud HSM][aws-cloudhsm].

Fore more detils on cloud HSM, go through the following resource:
- [AWS Cloud HSM Reference Documents][aws-cloudhsm-doc]
- [Choosing the Right Cloud HSM][cloudhsm-blog-1]

[google-cloudhsm]: https://cloud.google.com/hsm
[aws-cloudhsm]: https://aws.amazon.com/cloudhsm/
[azure-cloudhsm]: https://azure.microsoft.com/en-us/services/azure-dedicated-hsm/
[aws-cloudhsm-doc]: https://docs.aws.amazon.com/cloudhsm/?id=docs_gateway
[cloudhsm-blog-1]: https://blog.gemalto.com/security/2018/11/20/choosing-the-right-cloud-hsm/

# References

[fips-140-2]: https://en.wikipedia.org/wiki/FIPS_140-2#Level_3
[blog-hsm-attributes]: https://www.cryptomathic.com/news-events/blog/understanding-hardware-security-modules-hsms
